import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    home: ShoppingCartScreen(),
  ));
}

class ShoppingCartScreen extends StatefulWidget {
  @override
  _ShoppingCartScreenState createState() => _ShoppingCartScreenState();
}

class _ShoppingCartScreenState extends State<ShoppingCartScreen> {
  int quantity = 1;
  int maxQuantity = 5;

  List<Map<String, dynamic>> items = [
    {
      'name': 'Pullover',
      'color': 'Black',
      'size': 'L',
      'price': 10.00,
      'quantity': 1,
      'image':
      'https://assets.ajio.com/medias/sys_master/root/20230624/cog9/6496592feebac147fcf098ea/-473Wx593H-465330195-green-MODEL.jpg',
    },
    {
      'name': 'Shirt',
      'color': 'Blue',
      'size': 'M',
      'price': 20.00,
      'quantity': 1,
      'image':
      'https://images.bestsellerclothing.in/data/selected/21-oct-2023/122003001_g1.jpg?width=415&height=550&mode=fill&fill=blur&format=auto',
    },
    {
      'name': 'Jeans',
      'color': 'Indigo',
      'size': 'S',
      'price': 15.00,
      'quantity': 1,
      'image': 'https://m.media-amazon.com/images/I/71R7b4Fu8ML._AC_UY1100_.jpg',
    },
    
  ];

  void _showSnackbar() {
    final snackBar = SnackBar(
      content: Text('Congratulations! Your order has been placed.'),
    );
    ScaffoldMessenger.of(context).showSnackBar(snackBar);
  }

  Future<void> _showDialog() async {
    return showDialog(
      context: context,
      builder: (BuildContext context) {
        return AlertDialog(
          title: Text(
            'Congratulation!!',
            style: TextStyle(
              fontSize: 20,
              fontWeight: FontWeight.bold,
              color: Colors.green,
            ),
          ),
          content: Text(
            'You have added 5 items to your bag!',
            style: TextStyle(
              fontSize: 16,
              color: Colors.black,
            ),
          ),
          actions: [
            Center(
              child: Container(
                margin: EdgeInsets.symmetric(vertical: 10),
                decoration: BoxDecoration(
                  color: Colors.pink,
                  borderRadius: BorderRadius.circular(10),
                ),
                child: TextButton(
                  onPressed: () {
                    Navigator.of(context).pop();
                  },
                  child: Text(
                    'OKAY',
                    style: TextStyle(
                      fontSize: 18,
                      color: Colors.white,
                    ),
                  ),
                ),
              ),
            ),
          ],
        );
      },
    );
  }


  Widget _buildCartItem(Map<String, dynamic> item) {
    return Container(
      padding: EdgeInsets.symmetric(vertical: 16),
      child: Row(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Image.network(
            item['image'],
            fit: BoxFit.fill,
            width: 100,
            height: 100,
          ),
          SizedBox(width: 16),
          Expanded(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                Text(
                  item['name'],
                  style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
                ),
                SizedBox(height: 8),
                Text('Color: ${item['color']}'),
                SizedBox(height: 8),
                Text('Size: ${item['size']}'),
                Row(
                  children: [
                    IconButton(
                      icon: Icon(Icons.remove),
                      onPressed: () {
                        if (item['quantity'] > 1) {
                          setState(() {
                            item['quantity']--;
                          });
                        }
                      },
                    ),
                    SizedBox(width: 8),
                    Text('${item['quantity']}'),
                    SizedBox(width: 8),
                    IconButton(
                      icon: Icon(Icons.add),
                      onPressed: () {
                        if (item['quantity'] < maxQuantity) {
                          setState(() {
                            item['quantity']++;
                          });
                        } else {
                          _showDialog();
                        }
                      },
                    ),
                  ],
                ),
                Row(
                  mainAxisAlignment: MainAxisAlignment.end,
                  children: [
                    Text(
                      'Total: \$${item['price'] * item['quantity']}',
                      style: TextStyle(fontWeight: FontWeight.bold),
                    ),
                  ],
                ),
              ],
            ),
          ),
        ],
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.green,
        title: Text('My Bag'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            // Wrap all items with a flexible ListView.builder
            Expanded(
              child: ListView.builder(
                itemCount: items.length,
                itemBuilder: (context, index) {
                  return _buildCartItem(items[index]);
                },
              ),
            ),

            Row(
              mainAxisAlignment: MainAxisAlignment.end,
              children: [
                Text(
                  'Total Amount: \$${(items.fold<double>(0, (total, item) => total + item['price'] * item['quantity'])).toStringAsFixed(2)}',
                  style: TextStyle(fontWeight: FontWeight.bold),
                ),
              ],
            ),
            SizedBox(height: 16),
            ElevatedButton(
              onPressed: () {
                _showSnackbar();
              },
              style: ElevatedButton.styleFrom(
                backgroundColor: Colors.redAccent,
                padding: EdgeInsets.symmetric(horizontal: 16, vertical: 8),
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(10),
                ),
              ),
              child: Text(
                'CHECK OUT',
                style: TextStyle(
                  fontSize: 18,
                  fontWeight: FontWeight.bold,
                  color: Colors.white,
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }

}
