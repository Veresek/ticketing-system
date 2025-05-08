# 🛠️ System Zgłaszania Usterek w Szkole

## 📌 Opis

Aplikacja umożliwia użytkownikom (uczniom/nauczycielom) zgłaszanie usterek technicznych w salach szkolnych. Logowanie odbywa się przez konto Office 365 (Microsoft Azure AD). 
Administratorzy mają dostęp do specjalnego panelu, gdzie mogą przeglądać wszystkie zgłoszenia i oznaczać naprawione problemy.

---

## ⚙️ Tech Stack

- **Next.js** – framework do budowy aplikacji webowych (SSR/CSR)
- **TypeScript** – statyczne typowanie dla większego bezpieczeństwa kodu
- **Tailwind CSS** – nowoczesny system stylowania komponentów
- **next-auth** – obsługa logowania przez Microsoft Azure AD (Office 365)

---

## 🔐 Logowanie

- Autoryzacja przy użyciu Microsoft Azure AD (Office 365)
- Wymagana konfiguracja aplikacji w Azure Portal
- Obsługa ról (`user`, `admin`) na podstawie adresu email lub przypisanej roli

---

## 📝 Formularz zgłoszeniowy (dla użytkowników)

Dostępny po zalogowaniu.

### Pola:
- **Sala** – tekst (np. `203`, `101A`)
- **Rodzaj usterki** – lista rozwijana:
  - Sprzęt komputerowy
  - Projektor
  - Oświetlenie
  - Internet / Wi-Fi
  - Inne
- **Opis** – pole tekstowe, wymagane minimum 10 znaków

### Walidacja:
- Wszystkie pola są wymagane
- Sala: maksymalnie 10 znaków, litery i cyfry
- Opis: minimum 10 znaków

---

## 🛠️ Panel administratora

Dostępny tylko dla użytkowników z rolą `admin`.

### Funkcje:
- Lista wszystkich zgłoszeń
- Sortowanie i filtrowanie (np. według sali lub statusu)
- Przycisk **"Oznacz jako naprawione"**
- Podgląd szczegółów zgłoszenia

---

## 🔒 Uprawnienia

| Funkcja                            | User | Admin |
|------------------------------------|------|--------|
| Logowanie przez Office 365         | ✅   | ✅     |
| Dodawanie zgłoszeń                 | ✅   | ✅     |
| Podgląd własnych zgłoszeń          | ✅   | ✅     |
| Podgląd wszystkich zgłoszeń        | ❌   | ✅     |
| Oznaczanie usterek jako naprawione | ❌   | ✅     |

## ⚠️ Przebieg działania

1. Użytkownik loguje się przez Office 365
2. Wypełnia formularz i wysyła zgłoszenie
3. Admin widzi zgłoszenie w swoim panelu
4. Admin oznacza usterkę jako „Naprawioną”

---

## 🧩 Możliwe rozszerzenia

- Powiadomienia email przy zmianie statusu zgłoszenia
- Historia zgłoszeń danego użytkownika
- Możliwość dodania zdjęcia usterki
- Eksport zgłoszeń do pliku CSV lub PDF

---

## 🛠️ Wymagania środowiskowe

- Node.js 18+
- Microsoft Azure AD App z uprawnieniami do logowania
- Zmiennie środowiskowe `.env.local`:
