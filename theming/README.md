public class WarehouseProcess {
    public static void main(String[] args) {
        // Membuat objek Amazon dan Customer
        Amazon amazon = new Amazon();
        Customer customer = new Customer();

        // Simulasi proses pengelolaan gudang
        String orderID = customer.sendOrder();
        if (amazon.receiveOrder(orderID)) {
            if (amazon.verifyOrder(orderID)) {
                if (amazon.isStockAvailable(orderID)) {
                    amazon.pickItem(orderID);
                    amazon.packItem(orderID);
                    amazon.labelAndDocument(orderID);
                    amazon.shipItem(orderID);
                    amazon.updateSystem(orderID);
                    customer.receiveOrder(orderID);
                } else {
                    amazon.notifyCustomer(orderID);
                }
            }
        }
    }
}

// Kelas Amazon
class Amazon {
    public boolean receiveOrder(String orderID) {
        System.out.println("Menerima Pesanan: " + orderID);
        return true; // Pesanan diterima
    }

    public boolean verifyOrder(String orderID) {
        System.out.println("Verifikasi Pesanan: " + orderID);
        return true; // Verifikasi berhasil
    }

    public boolean isStockAvailable(String orderID) {
        System.out.println("Periksa Ketersediaan Stok untuk Pesanan: " + orderID);
        // Simulasi stok tersedia
        return true;
    }

    public void pickItem(String orderID) {
        System.out.println("Mengambil Barang untuk Pesanan: " + orderID);
    }

    public void packItem(String orderID) {
        System.out.println("Pengepakan Barang untuk Pesanan: " + orderID);
    }

    public void labelAndDocument(String orderID) {
        System.out.println("Pelabelan dan Dokumentasi untuk Pesanan: " + orderID);
    }

    public void shipItem(String orderID) {
        System.out.println("Pengiriman Barang untuk Pesanan: " + orderID);
    }

    public void updateSystem(String orderID) {
        System.out.println("Pembaruan Sistem untuk Pesanan: " + orderID);
    }

    public void notifyCustomer(String orderID) {
        System.out.println("Stok tidak tersedia untuk Pesanan: " + orderID + ". Notifikasi dikirim ke pelanggan.");
    }
}

// Kelas Customer
class Customer {
    public String sendOrder() {
        String orderID = "ORD123";
        System.out.println("Mengirim Pesanan: " + orderID);
        return orderID;
    }

    public void receiveOrder(String orderID) {
        System.out.println("Menerima Pesanan: " + orderID);
    }
}
