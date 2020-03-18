---
title: Co nowego w języku C# 7.2
description: Przegląd nowych funkcji w języku C# 7.2.
ms.date: 08/16/2017
ms.openlocfilehash: 7febefb81bbea6f24690adb05488ad6a18bbf552
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75694598"
---
# <a name="whats-new-in-c-72"></a>Co nowego w języku C# 7.2

C# 7.2 to kolejna wersja punktowa, która dodaje wiele przydatnych funkcji.
Jednym z tematów dla tej wersji jest bardziej efektywne działanie z typami wartości, unikając niepotrzebnych kopii lub alokacji.

Pozostałe funkcje są małe, ładne do posiadania funkcje.

C# 7.2 używa elementu konfiguracji [wyboru wersji językowej,](../language-reference/configure-language-version.md) aby wybrać wersję językową kompilatora.

Nowe funkcje języka w tej wersji to:

- [Techniki pisania bezpiecznego, wydajnego kodu](#safe-efficient-code-enhancements)
  - Kombinacja ulepszeń składni, które umożliwiają pracę z typami wartości przy użyciu semantyki odwołań.
- [Argumenty nazwane inne niż końcowe](#non-trailing-named-arguments)
  - Po nazwanych argumentach mogą następują argumenty pozycyjne.
- [Wiodące podkreślenia w literałach liczbowych](#leading-underscores-in-numeric-literals)
  - Literały liczbowe mogą teraz mieć wiodące podkreślenia przed dowolnymi drukowanymi cyframi.
- [`private protected`modyfikator dostępu](#private-protected-access-modifier)
  - Modyfikator `private protected` dostępu umożliwia dostęp dla klas pochodnych w tym samym zestawie.
- [Wyrażenia `ref` warunkowe](#conditional-ref-expressions)
  - Wynik wyrażenia warunkowego`?:`( ) może być teraz odwołaniem.

W dalszej części tego artykułu przedstawiono omówienie każdej funkcji. Dla każdej funkcji dowiesz się, co za nią kryje. Dowiesz się składni. Te funkcje można eksplorować w swoim środowisku za pomocą narzędzia globalnego: `dotnet try`

1. Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *próbek.*
1. Uruchom polecenie `dotnet try`.

## <a name="safe-efficient-code-enhancements"></a>Bezpieczne, wydajne ulepszenia kodu

Funkcje języka wprowadzone w 7.2 umożliwiają pracę z typami wartości przy użyciu semantyki referencyjnej. Są one przeznaczone do zwiększenia wydajności, minimalizując kopiowanie typów wartości bez ponoszenia alokacji pamięci skojarzonych z użyciem typów odwołań. Dostępne funkcje to:

- Modyfikator `in` parametrów, aby określić, że argument jest przekazywany przez odwołanie, ale nie jest modyfikowany przez wywoływaną metodę. Dodanie `in` modyfikatora do argumentu jest [zmianą zgodną ze źródłem](version-update-considerations.md#source-compatible-changes).
- Modyfikator `ref readonly` metody zwraca, aby wskazać, że metoda zwraca jego wartość przez odwołanie, ale nie zezwala na zapisy do tego obiektu. Dodanie `ref readonly` modyfikatora jest [zmianą zgodną ze źródłem,](version-update-considerations.md#source-compatible-changes)jeśli zwrot jest przypisany do wartości. Dodanie `readonly` modyfikatora `ref` do istniejącej instrukcji return jest [niezgodną zmianą](version-update-considerations.md#incompatible-changes). Wymaga wywoływania, aby zaktualizować deklarację `ref` zmiennych `readonly` lokalnych w celu uwzględnienia modyfikatora.
- Deklaracja, `readonly struct` aby wskazać, że struktury jest niezmienne i `in` powinny być przekazywane jako parametr do jego metody członkowskie. Dodanie `readonly` modyfikatora do istniejącej deklaracji struktury jest [zmianą zgodną z binarną](version-update-considerations.md#binary-compatible-changes).
- Deklaracja, `ref struct` aby wskazać, że typ struktury uzyskuje dostęp do pamięci zarządzanej bezpośrednio i zawsze musi być przydzielony stos. Dodanie `ref` modyfikatora `struct` do istniejącej deklaracji jest [niezgodną zmianą](version-update-considerations.md#incompatible-changes). A `ref struct` nie może być członkiem klasy lub używane w innych miejscach, gdzie może być przydzielona na stercie.

Możesz przeczytać więcej o wszystkich tych zmianach w [Napisz bezpieczny kod.](../write-safe-efficient-code.md)

## <a name="non-trailing-named-arguments"></a>Argumenty nazwane inne niż końcowe

Wywołania metody mogą teraz używać nazwanych argumentów, które poprzedzają argumenty pozycyjne, gdy te nazwane argumenty znajdują się we właściwych pozycjach. Aby uzyskać więcej informacji, zobacz [Argumenty nazwane i opcjonalne](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Wiodące podkreślenia w literałach liczbowych

Implementacja obsługi separatorów cyfr w języku C# 7.0 nie pozwoliła `_` na pierwszy znak wartości dosłownej. Literały liczbowe szesnaste i binarne mogą teraz zaczynać się od `_`.

Przykład:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>*prywatny chroniony* dostęp modyfikator

Nowy modyfikator `private protected` dostępu złożonego: wskazuje, że element członkowski może być dostępny przez zawierające klasy lub klasy pochodne, które są zadeklarowane w tym samym zestawie. Umożliwia `protected internal` dostęp przez klasy pochodne lub klasy, `private protected` które znajdują się w tym samym zestawie, ogranicza dostęp do typów pochodnych zadeklarowanych w tym samym zestawie.

Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../language-reference/keywords/access-modifiers.md) w odwołaniu do języka.

## <a name="conditional-ref-expressions"></a>Wyrażenia `ref` warunkowe

Na koniec wyrażenie warunkowe może spowodować wynik ref zamiast wyniku wartości. Na przykład należy napisać następujące, aby pobrać odwołanie do pierwszego elementu w jednej z dwóch tablic:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

Zmienna `r` jest odwołaniem do pierwszej wartości w jednym `arr` lub `otherArr`.

Aby uzyskać więcej informacji, zobacz [operator warunkowy (?:)](../language-reference/operators/conditional-operator.md) w odwołaniu do języka.
