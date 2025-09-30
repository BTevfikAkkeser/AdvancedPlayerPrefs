# AdvancedPlayerPrefs

An enhanced PlayerPrefs utility library for Unity, providing secure, flexible, and feature-rich storage for player data and settings.

---

## Why “Advanced”?

Unity’s built-in **PlayerPrefs** works well for basic key-value storage (int, float, string). But for real projects, you often need more:

- Encrypt / obfuscate stored data to protect against tampering  
- Save and load custom objects, lists, dictionaries  
- Migrate old data schemas to new ones  
- Backup and restore prefererences  
- Trigger events when certain data changes  

AdvancedPlayerPrefs addresses these needs, offering a drop-in replacement with extended capabilities.

---

## Features

- Int / Float / String storage (like standard PlayerPrefs)  
- `SetObject<T>` / `GetObject<T>` support for data classes (via JSON serialization)  
- Optional **encryption** layer  
- Automatic **migrations** for schema changes  
- Event / callback notifications on data updates  
- `Save()`, `DeleteKey()`, `HasKey()` utility methods  
- Backup / restore support (optional)  

---

## How to Use

```csharp
// Simple values
AdvancedPlayerPrefs.SetInt("HighScore", 1000);
int score = AdvancedPlayerPrefs.GetInt("HighScore", 0);

// Objects
MyGameData data = new MyGameData() { Level = 5, Coins = 300 };
AdvancedPlayerPrefs.SetObject("GameData", data);

MyGameData loaded = AdvancedPlayerPrefs.GetObject<MyGameData>("GameData");
if (loaded != null)
{
    Debug.Log($"Level: {loaded.Level}, Coins: {loaded.Coins}");
}

// Save changes to persistent storage
AdvancedPlayerPrefs.Save();
Example Use Cases
Game settings (audio, graphics, control mappings)

Player progress / profile data

Inventory systems

Preferences / configuration data

Feature flags (enable/disable modules)

Notes & Tips
Always call Save() when değişiklik yaptıktan sonra (örneğin uygulama kapanırken)

Beware of serialization issues (avoid non-serializable types)

If using encryption, keep keys / salts secure

For schema changes, create migration pathways (old → new data structures)
