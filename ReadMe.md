# Currency Apps
Currency Apps adalah program sederhana yang digunakan untuk memudahkan pengguna dalam mengetahui nilai tukar dari USD ke Rupiah (Rp)

### Cara Menggunakan
- Masukkan angka pada box USD 
- Tekan Tombol Hitung dan
- hasil akan tampil pada bagian paling bawah

### Kelebihan & Kekurangan
#### - Kelebihan
- Simpel
- Mudah dimengerti
- Hasil langsung diperlihatkan

#### - Kekurangan
- Hanya bisa USD
- Tampilannya membosankan

### Penjelasan Koding
Pada program ini saya menggunakan Class yang digunakan untuk menghitung dan melakukan logika. 

    class CurrencyController
    {
        public string usdToIdr(string nominal)
        {
            var nominalDouble = Convert.ToDouble(nominal);
            var result = nominalDouble * 15000;
            return Convert.ToString(result);
        }

        public Boolean isAllowed(string nominal)
        {
            Regex regex = new Regex ("[^0-9.-]+");
            return !regex.IsMatch(nominal);
        }
    }

Pada usdToIdr untuk menghitung dari USD ke Rupiah (Rp) dan isAllowed digunakan untuk melakukan logika, dan untuk menampilkan hasil saya menggunakan Class pertama-nya.

    public partial class MainWindow : Window
    {
        CurrencyController currencyController;

        public MainWindow()
        {
            InitializeComponent();
            currencyController = new CurrencyController();
        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            var nominalInput = InputTextBox.Text;
            var result = "invalid";
            if (currencyController.isAllowed(nominalInput))
            {
                result = currencyController.usdToIdr(nominalInput);
            }
            resultLabel.Content = result;

        }
    }

Karena saya memnggunakan Class lagi maka di Class pertama ini harus di deklarasi, jika sudah maka kita harus memanggil Class tersebut supaya hasil dari hitungannya bisa ditampilkan.