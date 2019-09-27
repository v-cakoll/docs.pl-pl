---
title: Co nowego w C# 7,2
description: Omówienie nowych funkcji w C# 7,2.
ms.date: 08/16/2017
ms.openlocfilehash: d559f07c501b2a79472d01e2815b50cd8f0f57a5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332318"
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
- [`private protected`Modyfikator dostępu](#private-protected-access-modifier)
  - Modyfikator `private protected` dostępu umożliwia dostęp do klas pochodnych w tym samym zestawie.
- [Wyrażenia `ref` warunkowe](#conditional-ref-expressions)
  - Wynik wyrażenia warunkowego (`?:`) może teraz być odwołaniem.

Pozostała część tego artykułu zawiera omówienie każdej funkcji. Dla każdej funkcji znajdziesz jej uzasadnienie. Poznasz składnię. Te funkcje można eksplorować w środowisku za pomocą `dotnet try` narzędzia globalnego:

1. Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *try-Samples* .
1. Uruchom `dotnet try`.

## <a name="safe-efficient-code-enhancements"></a>Bezpieczne usprawnienia kodu

Funkcje języka wprowadzone w 7,2 umożliwiają współpracę z typami wartości przy użyciu semantyki odwołań. Są one przeznaczone do zwiększania wydajności poprzez minimalizowanie kopiowania typów wartości bez ponoszenia alokacji pamięci skojarzonej z użyciem typów referencyjnych. Funkcje obejmują:

- `in` Modyfikator parametrów, aby określić, że argument jest przesyłany przez odwołanie, ale nie modyfikowane przez wywołaną metodę. Dodanie modyfikatora do argumentu jest [zgodną zmianą źródłową.](version-update-considerations.md#source-compatible-changes) `in`
- `ref readonly` Modyfikator metody zwraca, aby wskazać, że metoda zwraca swoją wartość przez odwołanie, ale nie zezwala na zapis w tym obiekcie. Dodanie modyfikatora jest [zgodną ze źródłem zmian](version-update-considerations.md#source-compatible-changes), jeśli powrót jest przypisany do wartości. `ref readonly` Dodanie modyfikatora do istniejącej `ref` instrukcji return jest [niezgodną zmianą.](version-update-considerations.md#incompatible-changes) `readonly` Wymaga, `ref` `readonly` aby wywołujący zaktualizował deklarację zmiennych lokalnych w celu uwzględnienia modyfikatora.
- Deklaracja wskazująca, że struktura jest niezmienna i powinna zostać przeniesiona `in` jako parametr do metod składowych. `readonly struct` Dodanie modyfikatora do istniejącej deklaracji struktury jest [zgodną binarną zmianą.](version-update-considerations.md#binary-compatible-changes) `readonly`
- `ref struct` Deklaracja wskazująca, że typ struktury bezpośrednio uzyskuje dostęp do pamięci zarządzanej i zawsze musi mieć przydzieloną stos. Dodanie modyfikatora do istniejącej `struct` deklaracji jest [niezgodną zmianą.](version-update-considerations.md#incompatible-changes) `ref` Element `ref struct` a nie może być składową klasy ani używać w innych lokalizacjach, w których może być przydzielony na stercie.

Więcej informacji na temat tych zmian można znaleźć w artykule [pisanie bezpiecznego wydajnego kodu](../write-safe-efficient-code.md).

## <a name="non-trailing-named-arguments"></a>Argumenty nazwane inne niż końcowe

Wywołania metod mogą teraz używać nazwanych argumentów, które poprzedzają argumenty pozycyjne, gdy te nazwane argumenty znajdują się w poprawnych pozycjach. Aby uzyskać więcej informacji [, zobacz Argumenty nazwane i opcjonalne](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Wiodące znaki podkreślenia w literałach numerycznych

Implementacja obsługi separatorów cyfr w C# 7,0 nie zezwala `_` na pierwszy znak wartości literału. Szesnastkowe i binarne literały numeryczne mogą teraz zaczynać `_`się od.

Na przykład:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>modyfikator *prywatnego dostępu chronionego*

Nowy modyfikator dostępu złożonego: `private protected` wskazuje, że element członkowski może być dostępny przez zawiera klasy lub klasy pochodne, które są zadeklarowane w tym samym zestawie. Zezwala na dostęp przez klasy pochodne lub klasy, które znajdują się w tym `private protected` samym zestawie, ogranicza dostęp do typów pochodnych zadeklarowanych w tym samym zestawie. `protected internal`

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../language-reference/keywords/access-modifiers.md) w dokumentacji języka.

## <a name="conditional-ref-expressions"></a>Wyrażenia `ref` warunkowe

Na koniec wyrażenie warunkowe może generować wynik ref zamiast wyniku wartości. Na przykład Napisz następujące polecenie, aby pobrać odwołanie do pierwszego elementu w jednej z dwóch tablic:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

Zmienna `r` jest odwołaniem do pierwszej wartości `arr` z lub `otherArr`.

Aby uzyskać więcej informacji, zobacz [operator warunkowy (?:)](../language-reference/operators/conditional-operator.md) w dokumentacji języka.
