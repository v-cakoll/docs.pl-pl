---
title: "Domyślna wartość wyrażenia (C# przewodnik programowania w języku)"
description: "Wyrażenia wartości domyślnej tworzy wartości domyślne dla dowolnego typu odwołanie lub typ wartości"
ms.date: 08/23/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2bb1c269e5347d615c47ab828506aef538c4761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="default-value-expressions-c-programming-guide"></a>Domyślna wartość wyrażenia (C# programowania przewodnik)

Wyrażenie wartości domyślnej powoduje wartością domyślną dla typu. Wyrażenia wartości domyślne są szczególnie przydatne w ogólne klasy i metody. Jak przypisać wartości domyślnej z typem sparametryzowane jest jeden problem, który pojawia się przy użyciu typów ogólnych `T` Jeśli nie znasz następujące wcześniej:

- Czy `T` jest typem referencyjnym lub typem wartości.
- Jeśli `T` jest to typ wartości określa, czy jest wartość liczbowa lub struktury zdefiniowane przez użytkownika.

 Podane zmiennej `t` sparametryzowane typu `T`, instrukcja `t = null` jest prawidłowy tylko jeśli `T` jest typem referencyjnym. Przypisanie `t = 0` działa tylko dla typów wartości liczbowe, ale nie dla struktury. Rozwiązaniem jest użycie domyślne wyrażenie wartości, która zwraca `null` dla typów odwołań (typy klas i typów interfejsów) oraz zero dla typów wartości liczbowych. Struktury zdefiniowane przez użytkownika, zwraca struktury zainicjowany zero wzorca bitowego, która tworzy 0 lub `null` dla każdego elementu członkowskiego, w zależności od tego, czy ten element członkowski jest typem wartości lub odwołania. Dla typów wartości null `default` zwraca <xref:System.Nullable%601?displayProperty=nameWithType>, którego zainicjowano podobnie jak wszelkie struktury.

`default(T)` Wyrażenie nie jest ograniczona do ogólne klasy i metody. Domyślna wartość wyrażenia może służyć z dowolnego typu zarządzanego. Dowolne z tych wyrażeń są prawidłowe:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 Poniższy przykład z `GenericList<T>` klasa przedstawia sposób użycia `default(T)` operatora w klasie rodzajowej. Aby uzyskać więcej informacji, zobacz [ogólne omówienie](../generics/introduction-to-generics.md).

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>Domyślnie literału i wnioskowanie o typie

Począwszy od C# 7.1, `default` literał może służyć do wyrażenia wartości domyślnej, gdy kompilator może wnioskować o typie wyrażenia. `default` Literał tworzy taką samą wartość jak odpowiednik `default(T)` gdzie `T` jest wywnioskowany typ. Może być kodu bardziej zwięzły zmniejszając nadmiarowość z typem deklarującym więcej niż raz. `default` Literał mogą być używane w dowolnej z następujących lokalizacji:

- Inicjator zmiennej
- przypisanie zmiennej
- deklarowanie wartości domyślnej dla parametru opcjonalnego
- udostępnia wartość argumentu wywołania — metoda
- Zwraca instrukcji (lub wyrażenie w elemencie członkowskim zabudowanego wyrażenia)

W poniższym przykładzie pokazano wiele sposobów użycia `default` literał w wyrażeniu wartości domyślne:

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>Zobacz także

 <xref:System.Collections.Generic>[Przewodnik programowania w języku C#](../index.md)  
 [Typy ogólne](../generics/index.md)  
 [Metody ogólne](../generics/generic-methods.md)  
 [Typy ogólne](~/docs/standard/generics/index.md)  
