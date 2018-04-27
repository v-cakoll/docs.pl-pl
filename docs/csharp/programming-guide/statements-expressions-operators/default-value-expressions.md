---
title: Domyślna wartość wyrażenia (C# przewodnik programowania w języku)
description: Wyrażenia wartości domyślnej tworzy wartości domyślne dla dowolnego typu odwołanie lub typ wartości
ms.date: 04/25/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 174ac79c9e2c4a4e628816b1178d420ec7cfc809
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="default-value-expressions-c-programming-guide"></a>Domyślna wartość wyrażenia (C# programowania przewodnik)

Wyrażenie wartości domyślnej `default(T)` daje wartość domyślna typu `T`. W poniższej tabeli przedstawiono wartości, które są tworzone dla różnych typów:

|Typ|Wartość domyślna|
|---------|---------|
|dowolny typ odwołania|`null`|
|Typ wartości liczbowe|Zero|
|[bool](../../language-reference/keywords/bool.md)|`false`|
|[char](../../language-reference/keywords/char.md)|`'\0'`|
|[enum](../../language-reference/keywords/enum.md)|Wartość utworzonego przez wyrażenie `(E)0`, gdzie `E` to identyfikator wyliczenia.|
|[struct](../../language-reference/keywords/struct.md)|Wartość utworzonego przez ustawienie wartości wszystkich pól typu na ich wartości domyślne, a wszystkie odwołania pola typu do `null`.|
|Typ dopuszczający wartość null|Wystąpienie, dla którego <xref:System.Nullable%601.HasValue%2A> właściwość jest `false` i <xref:System.Nullable%601.Value%2A> właściwość jest niezdefiniowana.|

Wyrażenia wartości domyślne są szczególnie przydatne w ogólne klasy i metody. Jak przypisać wartość domyślną typu sparametryzowane jest jeden problem, który pojawia się przy użyciu typów ogólnych `T` Jeśli nie znasz następujące wcześniej:

- Czy `T` jest typem referencyjnym lub typem wartości.
- Jeśli `T` jest typem wartości, czy jest wartość liczbowa lub struktury.

 Podane zmiennej `t` sparametryzowane typu `T`, instrukcja `t = null` jest prawidłowy tylko jeśli `T` jest typem referencyjnym. Przypisanie `t = 0` działa tylko dla typów wartości liczbowe, ale nie dla struktury. Aby rozwiązać, który, należy użyć wyrażenie wartości domyślnej:

```csharp
T t = default(T);
```

`default(T)` Wyrażenie nie jest ograniczona do ogólne klasy i metody. Domyślna wartość wyrażenia może służyć z dowolnego typu zarządzanego. Dowolne z tych wyrażeń są prawidłowe:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 Poniższy przykład z `GenericList<T>` klasa przedstawia sposób użycia `default(T)` operatora w klasie rodzajowej. Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](../generics/introduction-to-generics.md).

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

 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../index.md)  
 [Typy ogólne (C# przewodnik programowania w języku)](../generics/index.md)  
 [Metody ogólne](../generics/generic-methods.md)  
 [Typy ogólne w .NET](~/docs/standard/generics/index.md)  
 [Tabela wartości domyślnych](../../language-reference/keywords/default-values-table.md)
