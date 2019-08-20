---
title: Typy ogólne w przewodniku w czasie C# wykonywania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: e011375ed069a48f80364e529e80397f5f0495a3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589612"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Typy ogólne w czasie wykonywania (Przewodnik programowania w języku C#)
Gdy typ ogólny lub metoda jest kompilowany do języka pośredniego firmy Microsoft (MSIL), zawiera metadane, które identyfikują go jako parametry typu. Sposób użycia MSIL dla typu ogólnego różni się w zależności od tego, czy dostarczony parametr typu jest typem wartości czy typem referencyjnym.  
  
 Gdy typ ogólny jest najpierw konstruowany z typem wartości jako parametr, środowisko uruchomieniowe tworzy wyspecjalizowany typ ogólny z dostarczonym parametrem lub parametrami zastępowanymi w odpowiednich lokalizacjach w języku MSIL. Wyspecjalizowane typy ogólne są tworzone jednokrotnie dla każdego unikatowego typu wartości, który jest używany jako parametr.  
  
 Załóżmy na przykład, że kod programu deklaruje stos, który jest zbudowany z liczb całkowitych:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 W tym momencie środowisko uruchomieniowe generuje wyspecjalizowaną wersję <xref:System.Collections.Generic.Stack%601> klasy, która ma odpowiednią liczbę całkowitą podstawioną odpowiednio do parametru. Teraz za każdym razem, gdy kod programu używa stosu liczb całkowitych, środowisko uruchomieniowe ponownie używa wygenerowanej klasy wyspecjalizowanej <xref:System.Collections.Generic.Stack%601> . W poniższym przykładzie są tworzone dwa wystąpienia stosu liczb całkowitych i współużytkują pojedyncze wystąpienie `Stack<int>` kodu:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Jednakże Załóżmy, że inna <xref:System.Collections.Generic.Stack%601> Klasa o innym typie wartości, taka `long` jak lub struktura zdefiniowana przez użytkownika, jest tworzona w innym punkcie w kodzie. W efekcie środowisko uruchomieniowe generuje inną wersję typu ogólnego i zastępuje `long` je w odpowiednich lokalizacjach w języku MSIL. Konwersje nie są już potrzebne, ponieważ każda wyspecjalizowana Klasa ogólna natywnie zawiera typ wartości.  
  
 Typy ogólne działają nieco inaczej w przypadku typów referencyjnych. Pierwszy raz, gdy typ ogólny jest konstruowany przy użyciu dowolnego typu referencyjnego, środowisko uruchomieniowe tworzy wyspecjalizowany typ ogólny z odwołaniami do obiektów, które zastępują parametry w MSIL. Następnie, za każdym razem, gdy tworzony jest typ wystąpienia typu referencyjnego jako jego parametr, niezależnie od tego, jakiego typu jest, środowisko uruchomieniowe ponownie używa wcześniej utworzonej wyspecjalizowanej wersji typu ogólnego. Jest to możliwe, ponieważ wszystkie odwołania mają ten sam rozmiar.  
  
 Załóżmy na przykład, że istniały dwa typy referencyjne, `Customer` Klasa `Order` i Klasa, a także Załóżmy, że utworzono stos `Customer` typów:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 W tym momencie środowisko uruchomieniowe generuje wyspecjalizowaną wersję <xref:System.Collections.Generic.Stack%601> klasy, która przechowuje odwołania do obiektów, które zostaną uzupełnione później, zamiast przechowywać dane. Załóżmy, że następny wiersz kodu tworzy stos innego typu referencyjnego, który nosi nazwę `Order`:  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 W przeciwieństwie do typów wartości, inna wyspecjalizowana wersja <xref:System.Collections.Generic.Stack%601> klasy nie jest tworzona dla tego `Order` typu. Zamiast tego tworzone jest wystąpienie wyspecjalizowanej wersji <xref:System.Collections.Generic.Stack%601> klasy, `orders` a zmienna jest ustawiana jako odwołująca się do niej. Załóżmy, że napotkasz wiersz kodu w celu utworzenia stosu `Customer` typu:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Podobnie jak w przypadku poprzedniego użycia <xref:System.Collections.Generic.Stack%601> klasy utworzonej przy `Order` użyciu typu, tworzone jest inne wystąpienie klasy wyspecjalizowanej <xref:System.Collections.Generic.Stack%601> . Znajdujące się w nim wskaźniki są ustawiane jako odwołujące się do obszaru pamięci o `Customer` rozmiarze typu. Ze względu na to, że liczba typów referencyjnych może się różnić w zależności C# od programu do programu, implementacja generycznych znacznie zmniejsza ilość kodu przez zredukowanie do jednej z wielu wyspecjalizowanych klas utworzonych przez kompilator dla klas ogólnych odwołania Typ.  
  
 Ponadto podczas tworzenia wystąpienia klasy C# generycznej przy użyciu typu wartości lub parametru typu odwołania odbicie może wysyłać zapytania do niego w czasie wykonywania i można ustalić zarówno jego rzeczywisty typ, jak i jego parametr typu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Typy ogólne](~/docs/standard/generics/index.md)
