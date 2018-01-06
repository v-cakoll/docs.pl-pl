---
title: "Nowości w języku C# 7.2."
description: "Przegląd nowych funkcji w języku C# 7.2."
keywords: "C# język projektu, 7.2, Visual Studio 2017 r."
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 9e7fefde6763dbd5c73c01e45e5652d9f207c213
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="whats-new-in-c-72"></a>Nowości w języku C# 7.2.

7.2 C# jest innej wersji punkt dodające wiele przydatnych funkcji.
Jeden motyw dla tej wersji jest wydajniejszą pracę z typami wartości, unikając niepotrzebnego kopie lub alokacji. 

Pozostałe funkcje są nieuprzywilejowany ma funkcje.

C# 7.2 używa [wybór wersji języka](csharp-7-1.md#language-version-selection) element konfiguracji, aby wybrać wersję językową kompilatora.

Dostępne są następujące nowe funkcje językowe w tej wersji:

* [Semantyka odwołań z typami wartości](#reference-semantics-with-value-types)
  - Kombinacja składni ulepszeń, które umożliwiają pracę z typów wartości, używając semantyki odwołania.
* [Non końcowe nazwane argumenty](#non-trailing-named-arguments)
  - Argumenty pozycyjne może następować nazwanych argumentów.
* [Wiodące znaki podkreślenia w literałach numerycznych](#leading-underscores-in-numeric-literals)
  - Literały numeryczne teraz mogą mieć wiodące znaki podkreślenia przed żadnych drukowanymi cyfr.
* [`private protected`Modyfikator dostępu](#private-protected)
  - `private protected` Modyfikator dostępu umożliwia dostęp do klas pochodnych w tym samym zestawie.

## <a name="reference-semantics-with-value-types"></a>Semantykę odwołania z typami wartości

Funkcje języka wprowadzone w 7.2 pozwalają pracować z typów wartości podczas używania semantykę odwołania. Są one przeznaczone do zwiększenia wydajności, minimalizując kopiowanie typów wartości bez ponoszenia alokacji pamięci skojarzone z typów odwołań. Funkcje obejmują:

 - `in` — Modyfikator parametrów, aby określić, że argument jest przekazywany przez odwołanie, ale nie zostały zmodyfikowane przez metodę o nazwie.
 - `ref readonly` Modyfikator na zwraca metodę, aby wskazać, że metoda zwraca wartość przez odwołanie, ale nie zezwala na zapisy do tego obiektu.
 - `readonly struct` Deklaracji, aby wskazać, że struktury jest niezmienne i powinien zostać przekazany jako `in` parametru do metody jego elementu członkowskiego.
 - `ref struct` Deklaracji, aby wskazać, że typem struktury uzyskuje dostęp do pamięci zarządzanej bezpośrednio i muszą zawsze być stosu przydzielone.

Możesz przeczytać więcej informacji na temat tych zmian w programie [przy użyciu typów wartości z semantykę odwołania](../reference-semantics-with-value-types.md).

## <a name="non-trailing-named-arguments"></a>Non końcowe nazwane argumenty

Wywołań metody mogą teraz używać nazwane argumenty, które poprzedzać argumenty pozycyjne, gdy to nazwane argumenty są poprawne pozycji. Aby uzyskać więcej informacji, zobacz [nazwane i opcjonalne argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Wiodące znaki podkreślenia w literałach numerycznych

Implementacja obsługę separatory cyfr w języku C# w wersji 7.0 nie zezwalają na `_` jako pierwszy znak w wartości literału. Hex i binarne literałach numerycznych może teraz rozpoczynać się od `_`. 

Na przykład:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>_prywatne chronione_ modyfikator dostępu

Ponadto nowe modyfikator dostępu złożone: `private protected` wskazuje, że element członkowski mogą być używane przez zawierające klasy lub klas pochodnych, które są zadeklarowane w tym samym zestawie. Gdy `protected internal` zezwala na dostęp klas pochodnych lub klasy, które znajdują się w tym samym zestawie, `private protected` ogranicza dostęp do typów pochodnych zadeklarowany w tym samym zestawie.

Aby uzyskać więcej informacji, zobacz [modyfikatorów dostępu](../language-reference/keywords/access-modifiers.md) w language reference.
