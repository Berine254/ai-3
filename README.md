# CryptoBuddy: A Simple AI Crypto Chatbot

crypto_db = {
    "Bitcoin": {
        "price_trend": "rising",
        "market_cap": "high",
        "energy_use": "high",
        "sustainability_score": 3/10
    },
    "Ethereum": {
        "price_trend": "stable",
        "market_cap": "high",
        "energy_use": "medium",
        "sustainability_score": 6/10
    },
    "Cardano": {
        "price_trend": "rising",
        "market_cap": "medium",
        "energy_use": "low",
        "sustainability_score": 8/10
    }
}

def get_recommendation(user_query):
    query = user_query.lower()
    if "sustainable" in query or "eco" in query:
        recommend = max(crypto_db, key=lambda x: crypto_db[x]["sustainability_score"])
        return f"Invest in {recommend}! 🌱 It’s eco-friendly and has long-term potential!"
    elif "trending" in query or "rising" in query:
        trending = [coin for coin in crypto_db if crypto_db[coin]["price_trend"] == "rising"]
        return f"These are trending up: {', '.join(trending)} 🚀"
    elif "most sustainable" in query:
        recommend = max(crypto_db, key=lambda x: crypto_db[x]["sustainability_score"])
        return f"The most sustainable coin is {recommend}."
    elif "growth" in query or "long-term" in query:
        recommend = "Cardano"
        return f"{recommend} (ADA) is trending up and has a top-tier sustainability score! 🚀"
    elif "profit" in query or "profitable" in query:
        # Prioritize price_trend == rising and market_cap == high
        profitable = [coin for coin in crypto_db if (crypto_db[coin]["price_trend"] == "rising" and crypto_db[coin]["market_cap"] == "high")]
        if profitable:
            return f"For profitability, consider: {', '.join(profitable)} 🚀"
        else:
            return "No highly profitable coins found at the moment."
    else:
        return "Sorry, I can only answer questions about crypto trends and sustainability for now!"

def main():
    print("CryptoBuddy: Hey there! Ask me about crypto trends or sustainability. (Type 'exit' to quit)")
    while True:
        user_query = input("You: ")
        if user_query.lower() in ["exit", "quit"]:
            print("CryptoBuddy: Crypto is risky—always do your own research! Bye! 👋")
            break
        print("CryptoBuddy:", get_recommendation(user_query))

if __name__ == "__main__":
    main()# ai-3
