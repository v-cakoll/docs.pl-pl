---
title: Wyrażenia wartości domyślnych (C# Programming Guide)
description: Domyślna wartość wyrażenia dają wartość domyślna dla dowolnego typu odwołania lub typu wartości
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 94866f22fb3ad921a834cffb16fe17e44cef5965
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46698403"
---
# <a name="default-value-expressions-c-programming-guide"></a>wyrażenia wartości domyślnych (C# Podręcznik programowania)

Wyrażenie wartości domyślnej `default(T)` generuje wartość domyślna typu `T`. W poniższej tabeli przedstawiono wartości, które są tworzone dla różnych typów:

|Typ|Wartość domyślna|
|---------|---------|
|dowolny typ odwołania|`null`|
|Typ wartości liczbowych|Zero|
|[bool](../../language-reference/keywords/bool.md)|`false`|
|[char](../../language-reference/keywords/char.md)|`'\0'`|
|[enum](../../language-reference/keywords/enum.md)|Wartość produkowane przez wyrażenie `(E)0`, gdzie `E` jest identyfikatorem wyliczenia.|
|[struct](../../language-reference/keywords/struct.md)|Wartość produkowane przez ustawienie wartości wszystkich pól typu na ich wartości domyślne, a wszystkie odwoływać się do pola typu do `null`.|
|Typ dopuszczający wartość null|Wystąpienie, dla którego <xref:System.Nullable%601.HasValue%2A> właściwość `false` i <xref:System.Nullable%601.Value%2A> właściwość jest niezdefiniowana.|

Wyrażenia wartości domyślnych są szczególnie przydatne w ogólne klasy i metody. Jednym problemem, który pojawia się za pomocą typów ogólnych jest jak przypisać wartość domyślną typu sparametryzowane `T` podczas nie wiesz, że wcześniej:

- Czy `T` jest typem referencyjnym lub typem wartości.
- Jeśli `T` jest typem wartości, czy jest wartością liczbową lub struktury.

 Biorąc pod uwagę zmienną `t` sparametryzowane typu `T`, instrukcji `t = null` jest prawidłowa tylko jeśli `T` jest typem referencyjnym. Przypisanie `t = 0` działa tylko wtedy, typach wartości liczbowe, ale nie struktury. Aby rozwiązać, który, należy użyć wyrażenie wartości domyślnej:

```csharp
T t = default(T);
```

`default(T)` Wyrażenie nie jest ograniczona do ogólne klasy i metody. Wyrażenia wartości domyślnych może służyć za pomocą dowolnego typu zarządzanego. Dowolne z tych wyrażeń są prawidłowe:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 Poniższy przykład z `GenericList<T>` klasy ilustruje sposób używania `default(T)` operatora w klasie ogólnej. Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](../generics/introduction-to-generics.md).

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>domyślny literał i wnioskowanie o typie

Począwszy od C# 7.1 `default` literał może służyć do wyrażenia wartości domyślnych, gdy kompilator może wywnioskować typ wyrażenia. `default` Literał tworzy taką samą wartość jak odpowiednik `default(T)` gdzie `T` jest wnioskowany typ. To może uczynić kod bardziej zwięzły widok przez ograniczenie nadmiarowości więcej niż raz deklarowania typu. `default` Literał mogą być używane w dowolnej z następujących lokalizacji:

- Inicjator zmiennej
- przypisanie zmiennej
- deklarowanie wartość domyślna dla opcjonalnego parametru
- podając wartości argumentu wywołania metody
- Zwraca instrukcję (lub wyrażenia w elemencie członkowskim zabudowanego wyrażenia)

W poniższym przykładzie pokazano wiele użycia `default` literału w wyrażeniu wartości domyślne:

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>  
- [Przewodnik programowania w języku C#](../index.md)  
- [Typy ogólne (C# Programming Guide)](../generics/index.md)  
- [Metody ogólne](../generics/generic-methods.md)  
- [Typy ogólne w .NET](~/docs/standard/generics/index.md)  
- [Tabela wartości domyślnych](../../language-reference/keywords/default-values-table.md)
