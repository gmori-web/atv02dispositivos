import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatefulWidget {
  const MyApp({super.key});

  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  bool _mostrarHabilidade = false;

  static const String _urlFoto =
      'https://upload.wikimedia.org/wikipedia/commons/9/92/LogoSantosFC.png';

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      theme: ThemeData(primarySwatch: Colors.blue),
      home: Scaffold(
        appBar: AppBar(
          title: const Text(
            'Meu currículo',
            style: TextStyle(color: Colors.white),
          ),
          backgroundColor: const Color(0xFF0B3975),
        ),
        body: Padding(
          padding: const EdgeInsets.all(16),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              // Foto redonda (imagem da internet)
              CircleAvatar(
                radius: 48,
                backgroundColor: Colors.white,
                child: ClipOval(
                  child: Image.network(
                    _urlFoto,
                    width: 96,
                    height: 96,
                    fit: BoxFit.contain,
                    loadingBuilder: (context, child, progress) {
                      if (progress == null) return child;
                      return const SizedBox(
                        width: 96,
                        height: 96,
                        child: Center(child: CircularProgressIndicator()),
                      );
                    },
                    errorBuilder: (context, error, stackTrace) {
                      return const Icon(
                        Icons.person,
                        size: 64,
                        color: Color(0xFF546E7A),
                      );
                    },
                  ),
                ),
              ),
              const SizedBox(height: 16),
              const Text(
                'Gustavo Savio Almeida de Araújo Mori',
                style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
              ),
              const SizedBox(height: 4),
              const Row(
                children: [
                  Icon(Icons.mail_outline, size: 20),
                  SizedBox(width: 8),
                  Text(
                    'g.mori@estudante.ifro.edu.br',
                    style: TextStyle(fontSize: 16),
                  ),
                ],
              ),
              const SizedBox(height: 4),
              const Row(
                children: [
                  Icon(Icons.phone, size: 20),
                  SizedBox(width: 8),
                  Text('(69) 99950-7690', style: TextStyle(fontSize: 16)),
                ],
              ),
              const SizedBox(height: 16),
              const Text(
                'Formação',
                style: TextStyle(
                  fontSize: 16,
                  fontWeight: FontWeight.bold,
                  color: Colors.blue,
                ),
              ),
              const SizedBox(height: 4),
              const Text(
                'Técnico em Informática - IFRO\nCursando Análise e Desenvolvimento de Sistemas - IFRO',
                style: TextStyle(fontSize: 16),
              ),
              const SizedBox(height: 16),
              const Text(
                'Habilidades',
                style: TextStyle(
                  fontSize: 16,
                  fontWeight: FontWeight.bold,
                  color: Colors.blue,
                ),
              ),
              const SizedBox(height: 4),

              if (_mostrarHabilidade)
                const Text(
                  'TypeScript \n C# \nJava',
                  style: TextStyle(fontSize: 16),
                ),
              const SizedBox(height: 8),
              ElevatedButton(
                onPressed: () {
                  setState(() {
                    _mostrarHabilidade = !_mostrarHabilidade;
                  });
                },
                child: const Text('Habilidade'),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
