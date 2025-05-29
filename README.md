- 👋 Hi, I’m @IeeSoul
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
IeeSoul/IeeSoul is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';
import 'package:url_launcher/url_launcher.dart';
import 'dart:async';

void main() {
  runApp(const WingChunApp());
}

class WingChunApp extends StatelessWidget {
  const WingChunApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Wing Chun Master',
      theme: ThemeData(
        primarySwatch: Colors.blueGrey,
        fontFamily: 'Roboto',
        cardTheme: CardTheme(
          elevation: 4,
          margin: const EdgeInsets.symmetric(vertical: 8, horizontal: 16),
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12)),
        ),
      ),
      home: const HomeScreen(),
    );
  }
}

// Home Screen
class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Wing Chun Master 🥋'),
        centerTitle: true,
      ),
      body: ListView(
        padding: const EdgeInsets.all(16.0),
        children: [
          Card(
            child: ListTile(
              leading: const Icon(Icons.info),
              title: const Text('Wing Chun Basics', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const BasicsScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.book),
              title: const Text('Forms Guide', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const FormsScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.link),
              title: const Text('Resources', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const ResourcesScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.fitness_center),
              title: const Text('Practice Tracker', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const PracticeTrackerScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.timer),
              title: const Text('Chi Sau Timer', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const ChiSauTimerScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.schedule),
              title: const Text('Training Schedule', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const TrainingScheduleScreen()),
              ),
            ),
          ),
        ],
      ),
    );
  }
}

// Basics Screen
class BasicsScreen extends StatelessWidget {
  const BasicsScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Wing Chun Basics')),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'Key Concepts 🧠',
              style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 16),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: const [
                    Text('• Centerline Theory: Control the central axis between you and your opponent.'),
                    SizedBox(height: 8),
                    Text('• Simultaneous Attack & Defense: Strike while defending.'),
                    SizedBox(height: 8),
                    Text('• Structure over Strength: Use efficiency and positioning, not brute force.'),
                  ],
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

// Forms Screen
class FormsScreen extends StatelessWidget {
  const FormsScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Wing Chun Forms')),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'Empty-Hand Forms 📚',
              style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 16),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: const [
                    Text('1. Siu Nim Tao: Builds fundamental stance and hand techniques.'),
                    SizedBox(height: 8),
                    Text('2. Chum Kiu: Focuses on footwork and bridging techniques.'),
                    SizedBox(height: 8),
                    Text('3. Biu Jee: Teaches emergency techniques and power generation.'),
                  ],
                ),
              ),
            ),
            const SizedBox(height: 16),
            const Text(
              'Advanced Tools 🛠️',
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
            ),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: const [
                    Text('• Wooden Dummy (Muk Yan Jong): Enhances precision and structure.'),
                    SizedBox(height: 8),
                    Text('• Weapons: Butterfly Swords and Long Pole for advanced training.'),
                  ],
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

// Resources Screen
class ResourcesScreen extends StatelessWidget {
  const ResourcesScreen({super.key});

  Future<void> _launchURL(String url) async {
    final Uri uri = Uri.parse(url);
    if (await canLaunchUrl(uri)) {
      await launchUrl(uri, mode: LaunchMode.externalApplication);
    } else {
      throw 'Could not launch $url';
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Resources')),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'Recommended Resources 📘',
              style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 16),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    const Text('Books:', style: TextStyle(fontWeight: FontWeight.bold)),
                    const SizedBox(height: 8),
                    const Text('• Wing Chun Kung Fu by Joseph Wayne Smith'),
                    const Text('• The Tao of Wing Chun by John Little'),
                    constimport 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';
import 'package:url_launcher/url_launcher.dart';
import 'dart:async';

void main() {
  runApp(const WingChunApp());
}

class WingChunApp extends StatelessWidget {
  const WingChunApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Wing Chun Master',
      theme: ThemeData(
        primarySwatch: Colors.blueGrey,
        fontFamily: 'Roboto',
        cardTheme: CardTheme(
          elevation: 4,
          margin: const EdgeInsets.symmetric(vertical: 8, horizontal: 16),
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12)),
        ),
      ),
      home: const HomeScreen(),
    );
  }
}

// Home Screen
class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Wing Chun Master 🥋'),
        centerTitle: true,
      ),
      body: ListView(
        padding: const EdgeInsets.all(16.0),
        children: [
          Card(
            child: ListTile(
              leading: const Icon(Icons.info),
              title: const Text('Wing Chun Basics', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const BasicsScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.book),
              title: const Text('Forms Guide', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const FormsScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.link),
              title: const Text('Resources', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const ResourcesScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.fitness_center),
              title: const Text('Practice Tracker', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const PracticeTrackerScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.timer),
              title: const Text('Chi Sau Timer', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const ChiSauTimerScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.schedule),
              title: const Text('Training Schedule', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const TrainingScheduleScreen()),
              ),
            ),
          ),
        ],
      ),
    );
  }
}

// Basics Screen
class BasicsScreen extends StatelessWidget {
  const BasicsScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Wing Chun Basics')),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'Key Concepts 🧠',
              style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 16),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: const [
                    Text('• Centerline Theory: Control the central axis between you and your opponent.'),
                    SizedBox(height: 8),
                    Text('• Simultaneous Attack & Defense: Strike while defending.'),
                    SizedBox(height: 8),
                    Text('• Structure over Strength: Use efficiency and positioning, not brute force.'),
                  ],
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

// Forms Screen
class FormsScreen extends StatelessWidget {
  const FormsScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Wing Chun Forms')),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'Empty-Hand Forms 📚',
              style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 16),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: const [
                    Text('1. Siu Nim Tao: Builds fundamental stance and hand techniques.'),
                    SizedBox(height: 8),
                    Text('2. Chum Kiu: Focuses on footwork and bridging techniques.'),
                    SizedBox(height: 8),
                    Text('3. Biu Jee: Teaches emergency techniques and power generation.'),
                  ],
                ),
              ),
            ),
            const SizedBox(height: 16),
            const Text(
              'Advanced Tools 🛠️',
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
            ),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: const [
                    Text('• Wooden Dummy (Muk Yan Jong): Enhances precision and structure.'),
                    SizedBox(height: 8),
                    Text('• Weapons: Butterfly Swords and Long Pole for advanced training.'),
                  ],
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

// Resources Screen
class ResourcesScreen extends StatelessWidget {
  const ResourcesScreen({super.key});

  Future<void> _launchURL(String url) async {
    final Uri uri = Uri.parse(url);
    if (await canLaunchUrl(uri)) {
      await launchUrl(uri, mode: LaunchMode.externalApplication);
    } else {
      throw 'Could not launch $url';
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Resources')),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'Recommended Resources 📘',
              style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 16),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    const Text('Books:', style: TextStyle(fontWeight: FontWeight.bold)),
                    const SizedBox(height: 8),
                    const Text('• Wing Chun Kung Fu by Joseph Wayne Smith'),
                    const Text('• The Tao of Wing Chun by John Little'),
                    constimport 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';
import 'package:url_launcher/url_launcher.dart';
import 'dart:async';

void main() {
  runApp(const WingChunApp());
}

class WingChunApp extends StatelessWidget {
  const WingChunApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Wing Chun Master',
      theme: ThemeData(
        primarySwatch: Colors.blueGrey,
        fontFamily: 'Roboto',
        cardTheme: CardTheme(
          elevation: 4,
          margin: const EdgeInsets.symmetric(vertical: 8, horizontal: 16),
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12)),
        ),
      ),
      home: const HomeScreen(),
    );
  }
}

// Home Screen
class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Wing Chun Master 🥋'),
        centerTitle: true,
      ),
      body: ListView(
        padding: const EdgeInsets.all(16.0),
        children: [
          Card(
            child: ListTile(
              leading: const Icon(Icons.info),
              title: const Text('Wing Chun Basics', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const BasicsScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.book),
              title: const Text('Forms Guide', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const FormsScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.link),
              title: const Text('Resources', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const ResourcesScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.fitness_center),
              title: const Text('Practice Tracker', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const PracticeTrackerScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.timer),
              title: const Text('Chi Sau Timer', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const ChiSauTimerScreen()),
              ),
            ),
          ),
          Card(
            child: ListTile(
              leading: const Icon(Icons.schedule),
              title: const Text('Training Schedule', style: TextStyle(fontWeight: FontWeight.bold)),
              onTap: () => Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const TrainingScheduleScreen()),
              ),
            ),
          ),
        ],
      ),
    );
  }
}

// Basics Screen
class BasicsScreen extends StatelessWidget {
  const BasicsScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Wing Chun Basics')),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'Key Concepts 🧠',
              style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 16),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: const [
                    Text('• Centerline Theory: Control the central axis between you and your opponent.'),
                    SizedBox(height: 8),
                    Text('• Simultaneous Attack & Defense: Strike while defending.'),
                    SizedBox(height: 8),
                    Text('• Structure over Strength: Use efficiency and positioning, not brute force.'),
                  ],
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

// Forms Screen
class FormsScreen extends StatelessWidget {
  const FormsScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Wing Chun Forms')),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'Empty-Hand Forms 📚',
              style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 16),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: const [
                    Text('1. Siu Nim Tao: Builds fundamental stance and hand techniques.'),
                    SizedBox(height: 8),
                    Text('2. Chum Kiu: Focuses on footwork and bridging techniques.'),
                    SizedBox(height: 8),
                    Text('3. Biu Jee: Teaches emergency techniques and power generation.'),
                  ],
                ),
              ),
            ),
            const SizedBox(height: 16),
            const Text(
              'Advanced Tools 🛠️',
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
            ),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: const [
                    Text('• Wooden Dummy (Muk Yan Jong): Enhances precision and structure.'),
                    SizedBox(height: 8),
                    Text('• Weapons: Butterfly Swords and Long Pole for advanced training.'),
                  ],
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

// Resources Screen
class ResourcesScreen extends StatelessWidget {
  const ResourcesScreen({super.key});

  Future<void> _launchURL(String url) async {
    final Uri uri = Uri.parse(url);
    if (await canLaunchUrl(uri)) {
      await launchUrl(uri, mode: LaunchMode.externalApplication);
    } else {
      throw 'Could not launch $url';
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Resources')),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'Recommended Resources 📘',
              style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 16),
            Card(
              child: Padding(
                padding: const EdgeInsets.all(12.0),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    const Text('Books:', style: TextStyle(fontWeight: FontWeight.bold)),
                    const SizedBox(height: 8),
                    const Text('• Wing Chun Kung Fu by Joseph Wayne Smith'),
                    const Text('• The Tao of Wing Chun by John Little'),
                    const
