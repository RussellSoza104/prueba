# prueba

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('PageView según el dispositivo')),
        body: SafeArea(
          child: LayoutBuilder(
            builder: (context, constraints) {
              bool isTablet = constraints.maxWidth >= 600; // Umbral para tablet

              return Center(
                child: Container(
                  height: double.infinity,
                  width: double.infinity,
                  child: isTablet
                      ? PageView(
                          scrollDirection: Axis.vertical,
                          children: [
                            Container(
                              width: double.infinity,
                              height: double.infinity,
                              color: Colors.white70,
                              child: Center(child: Text('Página 1')),
                            ),
                            Container(
                              width: double.infinity,
                              height: double.infinity,
                              color: Colors.blueAccent,
                              child: Center(child: Text('Página 2')),
                            ),
                          ],
                        )
                      : Container(
                          width: MediaQuery.of(context).size.height, // Usar la altura como ancho
                          height: MediaQuery.of(context).size.width, // Usar el ancho como altura
                          child: Transform(
                            transform: Matrix4.rotationZ(-1.5708), // Rotar 90 grados en radianes
                            alignment: Alignment.center,
                            child: PageView(
                              scrollDirection: Axis.horizontal,
                              children: [
                                Container(
                                  width: MediaQuery.of(context).size.height + 1000, // Ajusta el ancho
                                  height: MediaQuery.of(context).size.width, // Ajusta la altura
                                  color: Colors.white70,
                                  child: Center(child: Text('Página 1')),
                                ),
                                Container(
                                  width: MediaQuery.of(context).size.height, // Ajusta el ancho
                                  height: MediaQuery.of(context).size.width, // Ajusta la altura
                                  color: Colors.blueAccent,
                                  child: Center(child: Text('Página 2')),
                                ),
                              ],
                            ),
                          ),
                        ),
                ),
              );
            },
          ),
        ),
        floatingActionButton: FloatingActionButton(
          onPressed: () {
            // Acción del FAB
          },
          child: Icon(Icons.add),
        ),
      ),
    );
  }
}
