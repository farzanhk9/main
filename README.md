import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'UI/UX Demo',
      theme: ThemeData(
        primarySwatch: Colors.indigo,
        textTheme: TextTheme(
          headline4: TextStyle(fontWeight: FontWeight.bold, color: Colors.black87),
          bodyText2: TextStyle(fontSize: 16, color: Colors.black54),
        ),
      ),
      home: HomePage(),
    );
  }
}

class HomePage extends StatelessWidget {
  final List<Map<String, String>> features = [
    {"icon": "🛒", "title": "Shop", "subtitle": "Explore the best deals"},
    {"icon": "❤️", "title": "Favorites", "subtitle": "Your saved items"},
    {"icon": "⚡", "title": "Fast Delivery", "subtitle": "Quick and reliable"},
    {"icon": "💬", "title": "Support", "subtitle": "We’re here for you"},
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.grey[100],
      appBar: AppBar(
        elevation: 0,
        backgroundColor: Colors.transparent,
        title: Text("UI/UX Demo", style: TextStyle(color: Colors.black)),
        centerTitle: true,
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text("Welcome 👋", style: Theme.of(context).textTheme.headline4),
            SizedBox(height: 8),
            Text("Design a smooth and modern app experience.",
                style: Theme.of(context).textTheme.bodyText2),
            SizedBox(height: 20),
            Expanded(
              child: GridView.builder(
                itemCount: features.length,
                gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                  crossAxisCount: 2,
                  mainAxisSpacing: 16,
                  crossAxisSpacing: 16,
                  childAspectRatio: 1,
                ),
                itemBuilder: (context, index) {
                  final feature = features[index];
                  return Card(
                    shape: RoundedRectangleBorder(
                      borderRadius: BorderRadius.circular(20),
                    ),
                    elevation: 4,
                    child: InkWell(
                      onTap: () {},
                      borderRadius: BorderRadius.circular(20),
                      child: Center(
                        child: Column(
                          mainAxisSize: MainAxisSize.min,
                          children: [
                            Text(feature["icon"]!, style: TextStyle(fontSize: 40)),
                            SizedBox(height: 10),
                            Text(feature["title"]!,
                                style: TextStyle(fontWeight: FontWeight.bold)),
                            Text(feature["subtitle"]!,
                                style: TextStyle(color: Colors.grey, fontSize: 12)),
                          ],
                        ),
                      ),
                    ),
                  );
                },
              ),
            ),
          ],
        ),
      ),
    );
  }
}

