import { useState } from "react";
import "./styles.css";

const services = [
  {
    id: 1,
    name: "Car General Service",
    price: "₹1,499",
    description: "Complete basic inspection and servicing."
  },
  {
    id: 2,
    name: "AC Service",
    price: "₹999",
    description: "AC inspection, cleaning and performance check."
  },
  {
    id: 3,
    name: "Oil Change",
    price: "₹799",
    description: "Engine oil replacement and basic inspection."
  },
  {
    id: 4,
    name: "Brake Service",
    price: "₹1,299",
    description: "Brake inspection and servicing."
  },
  {
    id: 5,
    name: "Car Detailing",
    price: "₹1,999",
    description: "Interior and exterior cleaning."
  }
];

function App() {
  const [selectedService, setSelectedService] = useState(null);
  const [booking, setBooking] = useState({
    name: "",
    phone: "",
    vehicle: "",
    date: "",
    time: ""
  });

  const handleChange = (e) => {
    setBooking({
      ...booking,
      [e.target.name]: e.target.value
    });
  };

  const submitBooking = (e) => {
    e.preventDefault();

    if (
      !booking.name ||
      !booking.phone ||
      !booking.vehicle ||
      !booking.date ||
      !booking.time
    ) {
      alert("Please fill all booking details.");
      return;
    }

    alert(
      `Booking request received!\n\nCustomer: ${booking.name}\nVehicle: ${booking.vehicle}\nService: ${selectedService?.name}`
    );
  };

  return (
    <div className="app">

      {/* Navigation */}
      <nav className="navbar">
        <div className="logo">
          <span>4F</span> Auto Service
        </div>

        <div className="nav-links">
          <a href="#home">Home</a>
          <a href="#services">Services</a>
          <a href="#booking">Book Service</a>
          <a href="#contact">Contact</a>
        </div>
      </nav>

      {/* Hero */}
      <section id="home" className="hero">
        <div className="hero-content">
          <h1>
            Reliable Car Care.
            <br />
            <span>Trusted by You.</span>
          </h1>

          <p>
            Professional automobile servicing, repairs and maintenance
            from 4F Auto Service.
          </p>

          <a href="#services" className="primary-btn">
            Explore Services
          </a>
        </div>
      </section>

      {/* Services */}
      <section id="services" className="services-section">
        <h2>Our Services</h2>

        <div className="service-grid">
          {services.map((service) => (
            <div className="service-card" key={service.id}>
              <div className="service-icon">🚗</div>

              <h3>{service.name}</h3>

              <p>{service.description}</p>

              <strong>{service.price}</strong>

              <button
                onClick={() => {
                  setSelectedService(service);
                  document
                    .getElementById("booking")
                    .scrollIntoView({ behavior: "smooth" });
                }}
              >
                Book Now
              </button>
            </div>
          ))}
        </div>
      </section>

      {/* Booking */}
      <section id="booking" className="booking-section">
        <div className="booking-container">

          <h2>Book Your Service</h2>

          {selectedService && (
            <div className="selected-service">
              Selected Service:
              <strong> {selectedService.name}</strong>
            </div>
          )}

          <form onSubmit={submitBooking}>

            <input
              type="text"
              name="name"
              placeholder="Your Name"
              value={booking.name}
              onChange={handleChange}
            />

            <input
              type="tel"
              name="phone"
              placeholder="Mobile Number"
              value={booking.phone}
              onChange={handleChange}
            />

            <input
              type="text"
              name="vehicle"
              placeholder="Vehicle Model"
              value={booking.vehicle}
              onChange={handleChange}
            />

            <input
              type="date"
              name="date"
              value={booking.date}
              onChange={handleChange}
            />

            <select
              name="time"
              value={booking.time}
              onChange={handleChange}
            >
              <option value="">Select Time</option>
              <option value="10:00 AM">10:00 AM</option>
              <option value="12:00 PM">12:00 PM</option>
              <option value="2:00 PM">2:00 PM</option>
              <option value="4:00 PM">4:00 PM</option>
              <option value="6:00 PM">6:00 PM</option>
            </select>

            <button type="submit" className="primary-btn">
              Confirm Booking
            </button>

          </form>
        </div>
      </section>

      {/* Contact */}
      <section id="contact" className="contact-section">
        <h2>4F Auto Service</h2>

        <p>
          Professional automobile service and maintenance.
        </p>

        <a
          href="https://wa.me/919999999999"
          target="_blank"
          rel="noreferrer"
          className="whatsapp-btn"
        >
          WhatsApp Us
        </a>
      </section>

      <footer>
        © 2026 4F Auto Service. All Rights Reserved.
      </footer>

    </div>
  );
}

export default App;
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: Arial, sans-serif;
  background: #f5f5f5;
  color: #111;
}

.navbar {
  height: 70px;
  background: #111;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 7%;
  position: sticky;
  top: 0;
  z-index: 100;
}

.logo {
  font-size: 22px;
  font-weight: bold;
}

.logo span {
  color: #e63946;
  font-size: 30px;
}

.nav-links {
  display: flex;
  gap: 25px;
}

.nav-links a {
  color: white;
  text-decoration: none;
}

.hero {
  min-height: 600px;
  display: flex;
  align-items: center;
  padding: 60px 8%;
  background: #151515;
  color: white;
}

.hero-content {
  max-width: 650px;
}

.hero h1 {
  font-size: 60px;
  line-height: 1.1;
  margin-bottom: 25px;
}

.hero h1 span {
  color: #e63946;
}

.hero p {
  font-size: 20px;
  line-height: 1.6;
  margin-bottom: 35px;
}

.primary-btn {
  display: inline-block;
  background: #e63946;
  color: white;
  padding: 14px 25px;
  border: none;
  border-radius: 7px;
  text-decoration: none;
  cursor: pointer;
  font-weight: bold;
}

.services-section {
  padding: 80px 7%;
}

.services-section h2,
.booking-section h2 {
  text-align: center;
  font-size: 36px;
  margin-bottom: 40px;
}

.service-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

.service-card {
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 5px 20px rgba(0,0,0,0.08);
}

.service-icon {
  font-size: 40px;
  margin-bottom: 15px;
}

.service-card h3 {
  margin-bottom: 12px;
}

.service-card p {
  color: #666;
  line-height: 1.5;
  margin-bottom: 20px;
}

.service-card strong {
  display: block;
  font-size: 22px;
  margin-bottom: 20px;
}

.service-card button {
  background: #111;
  color: white;
  border: none;
  padding: 12px 20px;
  border-radius: 6px;
  cursor: pointer;
}

.booking-section {
  background: #eee;
  padding: 80px 7%;
}

.booking-container {
  max-width: 650px;
  margin: auto;
}

.selected-service {
  background: white;
  padding: 15px;
  margin-bottom: 20px;
  border-radius: 7px;
}

form {
  display: grid;
  gap: 15px;
}

input,
select {
  width: 100%;
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 7px;
  font-size: 16px;
}

.contact-section {
  text-align: center;
  padding: 80px 20px;
}

.contact-section p {
  margin: 15px 0 25px;
}

.whatsapp-btn {
  display: inline-block;
  background: #25d366;
  color: white;
  padding: 14px 25px;
  border-radius: 7px;
  text-decoration: none;
}

footer {
  background: #111;
  color: white;
  text-align: center;
  padding: 25px;
}

@media (max-width: 768px) {

  .navbar {
    padding: 0 20px;
  }

  .nav-links {
    display: none;
  }

  .hero h1 {
    font-size: 42px;
  }

  .service-grid {
    grid-template-columns: 1fr;
  }

}
