---
title: Co nowego w C# 7,2
description: Omówienie nowych funkcji w C# 7,2.
ms.date: 08/16/2017
ms.openlocfilehash: 7febefb81bbea6f24690adb05488ad6a18bbf552
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694598"
---
# <a name="whats-new-in-c-72"></a>Co nowego w C# 7,2

C#7,2 to inna wersja punktu, która dodaje wiele przydatnych funkcji.
Jeden motyw dla tej wersji działa wydajniej z typami wartości poprzez uniknięcie niepotrzebnych kopii lub przydziałów.

Pozostałe funkcje są małe, całkiem-do-mają funkcje.

C#7,2 używa elementu konfiguracja [wyboru wersji języka](../language-reference/configure-language-version.md) , aby wybrać wersję języka kompilatora.

Nowe funkcje języka w tej wersji są następujące:

- [Techniki pisania bezpiecznego wydajnego kodu](#safe-efficient-code-enhancements)
  - Kombinacja ulepszeń składni, które umożliwiają pracę z typami wartości przy użyciu semantyki referencyjnej.
- [Argumenty nazwane inne niż końcowe](#non-trailing-named-arguments)
  - Po nazwanych argumentach mogą występować argumenty pozycyjne.
- [Wiodące znaki podkreślenia w literałach numerycznych](#leading-underscores-in-numeric-literals)
  - Literały numeryczne mogą teraz zawierać podkreślenia wiodące przed wszelkimi drukowanymi cyframi.
- [Modyfikator dostępu `private protected`](#private-protected-access-modifier)
  - Modyfikator dostępu `private protected` umożliwia dostęp do klas pochodnych w tym samym zestawie.
- [Wyrażenia warunkowe `ref`](#conditional-ref-expressions)
  - Wynik wyrażenia warunkowego (`?:`) może teraz być odwołaniem.

Pozostała część tego artykułu zawiera omówienie każdej funkcji. Dla każdej funkcji znajdziesz jej uzasadnienie. Poznasz składnię. Te funkcje można eksplorować w środowisku za pomocą narzędzia globalnego `dotnet try`:

1. Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *try-Samples* .
1. Uruchom polecenie `dotnet try`.

## <a name="safe-efficient-code-enhancements"></a>Bezpieczne usprawnienia kodu

Funkcje języka wprowadzone w 7,2 umożliwiają współpracę z typami wartości przy użyciu semantyki odwołań. Są one przeznaczone do zwiększania wydajności poprzez minimalizowanie kopiowania typów wartości bez ponoszenia alokacji pamięci skojarzonej z użyciem typów referencyjnych. Funkcje obejmują:

- Modyfikator `in` dla parametrów, aby określić, że argument jest przesyłany przez odwołanie, ale nie modyfikowane przez wywołaną metodę. Dodanie modyfikatora `in` do argumentu jest [zgodną zmianą źródłową](version-update-considerations.md#source-compatible-changes).
- Modyfikator `ref readonly` dla metody zwraca, aby wskazać, że metoda zwraca swoją wartość przez odwołanie, ale nie zezwala na zapisywanie w tym obiekcie. Dodanie modyfikatora `ref readonly` jest [zmianą zgodną ze źródłem](version-update-considerations.md#source-compatible-changes), jeśli powrót jest przypisany do wartości. Dodanie modyfikatora `readonly` do istniejącej instrukcji `ref` Return jest [niezgodną zmianą](version-update-considerations.md#incompatible-changes). Wymaga to od wywołujących aktualizacji deklaracji `ref` zmiennych lokalnych w celu uwzględnienia modyfikatora `readonly`.
- Deklaracja `readonly struct`, aby wskazać, że struktura jest niezmienna i powinna zostać przeniesiona jako parametr `in` do metod składowych. Dodanie modyfikatora `readonly` do istniejącej deklaracji struktury jest [zgodną z binarną zmianą](version-update-considerations.md#binary-compatible-changes).
- Deklaracja `ref struct`, aby wskazać, że typ struktury bezpośrednio uzyskuje dostęp do pamięci zarządzanej i zawsze musi mieć przydzieloną stos. Dodanie modyfikatora `ref` do istniejącej deklaracji `struct` jest [niezgodną zmianą](version-update-considerations.md#incompatible-changes). `ref struct` nie może być składową klasy ani używać w innych lokalizacjach, w których może być przypisana na stercie.

Więcej informacji na temat tych zmian można znaleźć w artykule [pisanie bezpiecznego wydajnego kodu](../write-safe-efficient-code.md).

## <a name="non-trailing-named-arguments"></a>Argumenty nazwane inne niż końcowe

Wywołania metod mogą teraz używać nazwanych argumentów, które poprzedzają argumenty pozycyjne, gdy te nazwane argumenty znajdują się w poprawnych pozycjach. Aby uzyskać więcej informacji [, zobacz Argumenty nazwane i opcjonalne](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Wiodące znaki podkreślenia w literałach numerycznych

Implementacja obsługi separatorów cyfr w C# 7,0 nie zezwala `_` na pierwszy znak wartości literału. Literały numeryczne szesnastkowe i binarne mogą teraz zaczynać się od `_`.

Na przykład:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>modyfikator *prywatnego dostępu chronionego*

Nowy modyfikator dostępu złożonego: `private protected` wskazuje, że element członkowski może być dostępny przez zawiera klasy lub klasy pochodne, które są zadeklarowane w tym samym zestawie. Chociaż `protected internal` zezwala na dostęp za pomocą klas pochodnych lub klas, które znajdują się w tym samym zestawie, `private protected` ogranicza dostęp do typów pochodnych zadeklarowanych w tym samym zestawie.

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../language-reference/keywords/access-modifiers.md) w dokumentacji języka.

## <a name="conditional-ref-expressions"></a>Wyrażenia warunkowe `ref`

Na koniec wyrażenie warunkowe może generować wynik ref zamiast wyniku wartości. Na przykład Napisz następujące polecenie, aby pobrać odwołanie do pierwszego elementu w jednej z dwóch tablic:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

Zmienna `r` jest odwołaniem do pierwszej wartości w obu `arr` lub `otherArr`.

Aby uzyskać więcej informacji, zobacz [operator warunkowy (?:)](../language-reference/operators/conditional-operator.md) w dokumentacji języka.
