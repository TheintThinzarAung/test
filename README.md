import { useState } from "react";

export default function AboutMeCards() {
  const cards = [
    { title: "📍 Location", content: "Bay Area, CA" },
    { title: "🖥 Role", content: "Data Analyst | Power BI Developer | SQL Developer" },
    { title: "📊 Expertise", content: "Power BI, SQL, Python, Data Visualization" },
    { title: "🚀 Passion", content: "Turning data into insights for impactful decisions" },
  ];

  return (
    <div className="flex flex-wrap justify-center gap-6 p-8 bg-gray-900 min-h-screen">
      {cards.map((card, index) => (
        <FlippingCard key={index} title={card.title} content={card.content} />
      ))}
    </div>
  );
}

function FlippingCard({ title, content }) {
  const [flipped, setFlipped] = useState(false);

  return (
    <div
      className="relative w-64 h-40 [perspective:1000px] cursor-pointer"
      onClick={() => setFlipped(!flipped)}
    >
      <div
        className={`absolute inset-0 transition-transform duration-500 [transform-style:preserve-3d] ${
          flipped ? "[transform:rotateY(180deg)]" : ""
        }`}
      >
        {/* Front Side */}
        <div className="absolute inset-0 bg-blue-600 text-white flex items-center justify-center rounded-xl shadow-xl p-4 [backface-visibility:hidden]">
          <h2 className="text-xl font-semibold">{title}</h2>
        </div>

        {/* Back Side */}
        <div className="absolute inset-0 bg-gray-800 text-white flex items-center justify-center rounded-xl shadow-xl p-4 [transform:rotateY(180deg)] [backface-visibility:hidden]">
          <p className="text-lg">{content}</p>
        </div>
      </div>
    </div>
  );
}
