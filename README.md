# workwave

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Learn Flutter](https://docs.flutter.dev/get-started/learn-flutter)
- [Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Flutter learning resources](https://docs.flutter.dev/reference/learning-resources)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
# 📡 Supabase API Calls in Flutter

This document explains the basic CRUD (Create, Read, Update, Delete) operations using the `supabase_flutter` package.

## Prerequisites

- Flutter
- Supabase Project
- `supabase_flutter` package

```bash
flutter pub add supabase_flutter
```

---

## Initialize Supabase

```dart
await Supabase.initialize(
  url: 'YOUR_SUPABASE_URL',
  anonKey: 'YOUR_PUBLISHABLE_KEY',
);
```

---

# CRUD Operations

## 1. Create (Insert)

```dart
await Supabase.instance.client
    .from('employees')
    .insert({
      'name': 'Vishnu',
      'email': 'vishnu@gmail.com',
    });
```

**Purpose:** Adds a new record to the database.

---

## 2. Read (Select)

```dart
final response = await Supabase.instance.client
    .from('employees')
    .select();

print(response);
```

**Purpose:** Fetches all records from the table.

---

## 3. Update

```dart
await Supabase.instance.client
    .from('employees')
    .update({
      'name': 'Vishnu Kumar',
    })
    .eq('id', 1);
```

**Purpose:** Updates an existing record.

---

## 4. Delete

```dart
await Supabase.instance.client
    .from('employees')
    .delete()
    .eq('id', 1);
```

**Purpose:** Deletes a record from the database.

---

# Filtering Data

```dart
final response = await Supabase.instance.client
    .from('employees')
    .select()
    .eq('id', 1);
```

**Purpose:** Returns records where `id = 1`.

---

# Order Data

```dart
final response = await Supabase.instance.client
    .from('employees')
    .select()
    .order('name');
```

---

# Limit Records

```dart
final response = await Supabase.instance.client
    .from('employees')
    .select()
    .limit(5);
```

---

# Count Records

```dart
final response = await Supabase.instance.client
    .from('employees')
    .select();
```

```dart
print(response.length);
```

---

# Summary

| Operation | Method |
|-----------|--------|
| Create | `.insert()` |
| Read | `.select()` |
| Update | `.update()` |
| Delete | `.delete()` |
| Filter | `.eq()` |
| Sort | `.order()` |
| Limit | `.limit()` |

---

Developed using **Flutter  Supabase**