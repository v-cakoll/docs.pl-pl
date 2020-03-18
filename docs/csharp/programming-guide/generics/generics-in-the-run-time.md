---
title: Rodzajowe w czasie wykonywania — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: a53a21d3028e588f5c4d5ce7bf35fad8d3720a08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75702990"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Typy ogólne w czasie wykonywania (Przewodnik programowania w języku C#)
Gdy typ rodzajowy lub metoda jest kompilowany do języka pośredniego firmy Microsoft (MSIL), zawiera metadane, które identyfikują go jako posiadające parametry typu. Sposób użycia msil dla typu ogólnego różni się w zależności od tego, czy parametr typu dostarczonego jest typem wartości, czy typem odwołania.  
  
 Gdy typ ogólny jest najpierw konstruowany z typem wartości jako parametrem, czas wykonywania tworzy wyspecjalizowany typ ogólny z podanych parametrów lub parametrów podstawionych w odpowiednich lokalizacjach w MSIL. Wyspecjalizowane typy ogólne są tworzone jeden raz dla każdego unikatowego typu wartości, który jest używany jako parametr.  
  
 Załóżmy na przykład, że kod programu zadeklarowany stos, który jest zbudowany z liczb całkowitych:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 W tym momencie czas wykonywania generuje wyspecjalizowaną wersję <xref:System.Collections.Generic.Stack%601> klasy, która ma liczbę całkowitą odpowiednio zastąpione dla jego parametru. Teraz, gdy kod programu używa stosu liczb całkowitych, w czasie <xref:System.Collections.Generic.Stack%601> wykonywania ponownie generuje wyspecjalizowanej klasy. W poniższym przykładzie tworzone są dwa wystąpienia stosu liczb całkowitych i współużytkują one pojedyncze wystąpienie `Stack<int>` kodu:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Załóżmy jednak, że inna <xref:System.Collections.Generic.Stack%601> klasa `long` o innym typie wartości, takich jak struktura zdefiniowana przez użytkownika jako jej parametr jest tworzony w innym punkcie kodu. W rezultacie program runtime generuje inną wersję typu ogólnego i zastępuje a `long` w odpowiednich lokalizacjach w MSIL. Konwersje nie są już konieczne, ponieważ każda wyspecjalizowana klasa ogólna natywnie zawiera typ wartości.  
  
 Rodzajowe działają nieco inaczej dla typów odwołań. Po raz pierwszy typ ogólny jest konstruowany z dowolnego typu odwołania, czas wykonywania tworzy wyspecjalizowany typ ogólny z odwołaniami do obiektów podstawione parametrów w MSIL. Następnie za każdym razem, gdy skonstruowany typ jest tworzony z typem odwołania jako jego parametr, niezależnie od typu, w czasie wykonywania ponownie używa wcześniej utworzonej wersji specjalistycznej typu ogólnego. Jest to możliwe, ponieważ wszystkie odwołania mają ten sam rozmiar.  
  
 Załóżmy na przykład, że `Customer` masz dwa `Order` typy odwołań, klasę i klasę, a także załóżmy, że utworzono stos `Customer` typów:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 W tym momencie program runtime generuje wyspecjalizowaną wersję <xref:System.Collections.Generic.Stack%601> klasy, która przechowuje odwołania do obiektów, które zostaną wypełnione później zamiast przechowywania danych. Załóżmy, że następny wiersz kodu tworzy stos innego typu odwołania, który nosi nazwę: `Order`  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 W przeciwieństwie do typów wartości <xref:System.Collections.Generic.Stack%601> inna wyspecjalizowana wersja `Order` klasy nie jest tworzona dla tego typu. Zamiast tego tworzone jest wystąpienie <xref:System.Collections.Generic.Stack%601> wyspecjalizowanej wersji klasy, a zmienna `orders` jest ustawiona na odwołanie się do niej. Załóżmy, że następnie napotkano wiersz kodu, `Customer` aby utworzyć stos typu:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Podobnie jak w przypadku <xref:System.Collections.Generic.Stack%601> poprzedniego użycia klasy `Order` utworzonej przy użyciu <xref:System.Collections.Generic.Stack%601> typu, tworzone jest inne wystąpienie klasy specjalistycznej. Wskaźniki, które są w nich zawarte są ustawione na odwoływanie `Customer` się do obszaru pamięci rozmiar typu. Ponieważ liczba typów odwołań może się różnić w zależności od programu, implementacja języka generyków języka generykowego c#znacznie zmniejsza ilość kodu, zmniejszając do jednej liczby wyspecjalizowanych klas utworzonych przez kompilator dla ogólnych klas typów odwołań.  
  
 Ponadto gdy ogólna klasa C# jest tworzone przy użyciu typu wartości lub parametrtypu odwołania, odbicie można zbadać go w czasie wykonywania i zarówno jego rzeczywistego typu i jego parametr typu można ustalić.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [Przewodnik programowania języka C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Typy ogólne](../../../standard/generics/index.md)
