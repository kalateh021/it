// it_store_demo: فروشگاه قطعات IT - صفحه اصلی + جزئیات محصول
import React, { useState } from "react";

const products = [
  {
    id: 1,
    name: "رم 8 گیگ DDR4",
    price: "1,200,000 تومان",
    description: "رم 8 گیگابایت DDR4 مناسب برای سیستم‌های میان‌رده و حرفه‌ای.",
    image: "https://via.placeholder.com/200x150?text=RAM+8GB"
  },
  {
    id: 2,
    name: "هارد SSD 256GB",
    price: "1,800,000 تومان",
    description: "هارد SSD با ظرفیت 256 گیگ، سرعت بالا، مناسب برای لپ‌تاپ و PC.",
    image: "https://via.placeholder.com/200x150?text=SSD+256GB"
  },
  {
    id: 3,
    name: "مادربرد ASUS B450",
    price: "3,500,000 تومان",
    description: "مادربرد حرفه‌ای از برند ASUS با چیپست B450 مناسب برای گیمینگ.",
    image: "https://via.placeholder.com/200x150?text=Motherboard"
  }
];

export default function Home() {
  const [selectedProduct, setSelectedProduct] = useState(null);

  return (
    <div className="min-h-screen bg-gray-100 p-6">
      <header className="text-center mb-10">
        <h1 className="text-3xl font-bold text-blue-700">فروشگاه قطعات IT</h1>
        <p className="text-gray-600 mt-2">انواع قطعات کامپیوتری با بهترین قیمت</p>
      </header>

      {!selectedProduct ? (
        <section className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
          {products.map((product) => (
            <div key={product.id} className="bg-white rounded-2xl shadow p-4 flex flex-col items-center">
              <img src={product.image} alt={product.name} className="mb-4 rounded" />
              <h2 className="text-lg font-semibold text-gray-800 mb-2">{product.name}</h2>
              <p className="text-green-600 font-bold mb-4">{product.price}</p>
              <button
                className="bg-blue-600 text-white px-4 py-2 rounded-xl hover:bg-blue-700"
                onClick={() => setSelectedProduct(product)}
              >
                جزئیات محصول
              </button>
            </div>
          ))}
        </section>
      ) : (
        <section className="bg-white rounded-2xl shadow p-6 max-w-xl mx-auto">
          <button
            onClick={() => setSelectedProduct(null)}
            className="text-blue-600 mb-4 hover:underline"
          >
            ← بازگشت به فروشگاه
          </button>
          <img src={selectedProduct.image} alt={selectedProduct.name} className="mb-4 rounded mx-auto" />
          <h2 className="text-2xl font-bold text-gray-800 mb-2 text-center">{selectedProduct.name}</h2>
          <p className="text-gray-700 mb-4 text-center">{selectedProduct.description}</p>
          <p className="text-green-600 font-bold text-center text-lg mb-6">{selectedProduct.price}</p>
          <div className="flex justify-center">
            <button className="bg-green-600 text-white px-6 py-2 rounded-xl hover:bg-green-700">افزودن به سبد خرید</button>
          </div>
        </section>
      )}
    </div>
  );
}
