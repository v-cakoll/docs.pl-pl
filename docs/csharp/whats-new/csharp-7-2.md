---
title: Co nowego w języku C# 7.2
description: Omówienie nowych funkcji w języku C# 7.2.
ms.date: 08/16/2017
ms.openlocfilehash: 87fd67b37a31a02960334a2b2a325724e0cc2c73
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109579"
---
# <a name="whats-new-in-c-72"></a>Co nowego w języku C# 7.2

C# 7.2 jest innej wersji punkt, który dodaje wiele użytecznych funkcji.
Jeden motywu w tej wersji pracuje wydajniej typów wartości, unikając niepotrzebnego kopiowania lub alokacji. 

Pozostałe funkcje są przydatne do być funkcji.

Używa języka C# 7.2 [wybór wersji języka](../language-reference/configure-language-version.md) element konfiguracji, aby wybrać wersję językową kompilatora.

Dostępne są następujące nowe funkcje języka w tej wersji:

* [Semantyka odwołań z typami wartości](#reference-semantics-with-value-types)
  - Kombinacja ulepszenia składni, które umożliwiają pracę z typów wartości za pomocą semantyki odwołania.
* [Inne niż końcowe argumenty nazwane](#non-trailing-named-arguments)
  - Argumenty nazwane może następować argumentów pozycyjnych.
* [Wiodące znaki podkreślenia w literałach numerycznych](#leading-underscores-in-numeric-literals)
  - Literały numeryczne, mogą teraz zawierać podkreśleniami wiodącymi przed wszystkie cyfry drukowanych.
* [`private protected` Modyfikator dostępu](#private-protected-access-modifier)
  - `private protected` Modyfikator dostępu umożliwia dostęp do klas pochodnych tego samego zestawu.

## <a name="reference-semantics-with-value-types"></a>Semantyka odwołań z typami wartości

Funkcje językowe, które wprowadzono w 7.2 pozwalają pracować z typami wartości podczas korzystania z semantyką odwołań. Są one przeznaczone do zwiększenia wydajności, minimalizując kopiowania typów wartości bez powodowania alokacji pamięci, związanych z użyciem typów odwołań. Funkcje obejmują:

 - `in` Modyfikator parametrów, aby określić, że argument jest przekazywany przez odwołanie, ale nie jest modyfikowany przez metodę o nazwie. Dodawanie `in` modyfikator do argumentu jest [źródła zmiany zgodne](version-update-considerations.md#source-compatible-changes).
 - `ref readonly` Modyfikator na zwraca metodę, aby wskazać, że metoda zwraca wartość przez odwołanie, ale nie zezwala na operacje zapisu do tego obiektu. Dodawanie `ref readonly` modyfikator jest [źródła zmiany zgodne](version-update-considerations.md#source-compatible-changes), jeśli zwracana jest przypisany do wartości. Dodawanie `readonly` modifer do istniejącego `ref` zwracany jest instrukcja [niezgodna zmiana](version-update-considerations.md#incompatible-changes). Wymaga ona wywołań zaktualizować deklaracji `ref` zmienne lokalne, aby uwzględnić `readonly` modyfikator.
 - `readonly struct` Deklaracji, aby wskazać, że struktury jest niemodyfikowalna i mają być przekazywane jako `in` parametru do metody jego elementu członkowskiego. Dodawanie `readonly` modyfikator do istniejącej deklaracji struktury jest [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).
 - `ref struct` Deklaracji, aby wskazać, że typ struktury uzyskuje dostęp do pamięci zarządzanej bezpośrednio i muszą zawsze być stosu przydzielone. Dodawanie `ref` modyfikator do istniejącego `struct` deklaracja jest [niezgodna zmiana](version-update-considerations.md#incompatible-changes). Element `ref struct` nie może być składową klasy ani używane w innych lokalizacjach, w którym może zostać przydzielone na stercie.

Możesz przeczytać więcej na temat wszystkich tych zmian w [przy użyciu typów wartości z semantyką odwołań](../reference-semantics-with-value-types.md).

## <a name="non-trailing-named-arguments"></a>Inne niż końcowe argumenty nazwane

Wywołania metody mogą teraz używać argumentów nazwanych, które poprzedzają argumenty pozycyjne, gdy te argumenty nazwane są właściwe pozycje. Aby uzyskać więcej informacji, zobacz [nazwane i opcjonalne argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Wiodące znaki podkreślenia w literałach numerycznych

Nie zezwalaj na implementację obsługę separatory cyfr w języku C# 7.0 `_` jako pierwszy znak w wartości literału. Hex i literały liczbowe binarne mogą teraz zaczynają się od `_`. 

Na przykład:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>_prywatny chroniony_ modyfikator dostępu

Na koniec nowy modyfikator dostępu złożone: `private protected` wskazuje, czy członek mogą być używane przez zawierający klasy lub klas pochodnych, które są zadeklarowane w tym samym zestawie. Gdy `protected internal` zezwala na dostęp przez klasy pochodne lub klasy, które znajdują się w tym samym zestawie `private protected` ogranicza dostęp do typów pochodnych zadeklarowanych w tym samym zestawie.

Aby uzyskać więcej informacji, zobacz [modyfikatorach dostępu](../language-reference/keywords/access-modifiers.md) w dokumentacji języka.
