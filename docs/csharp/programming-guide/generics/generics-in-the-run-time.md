---
title: Typy ogólne w czasie wykonywania - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: c739ae9b9804ffcb27d6bdc969bf7b5c0fe90512
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423328"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Typy ogólne w czasie wykonywania (Przewodnik programowania w języku C#)
W przypadku typu ogólnego lub metody jest kompilowany na język Microsoft intermediate language (MSIL), zawiera metadane, które identyfikuje go jako parametrów typu. Jak kod w języku MSIL dla typu ogólnego jest używany różni się w oparciu czy parametr typu podana jest wartość typu lub typów referencyjnych.  
  
 W przypadku typu ogólnego, najpierw jest zbudowany z typem wartości jako parametr, środowisko uruchomieniowe tworzy wyspecjalizowane typu ogólnego z podany parametr lub parametry zastąpione w odpowiednich miejscach w kodzie MSIL. Specjalne typy ogólne są tworzone jeden raz dla każdego typu unikatową wartość, która jest używana jako parametr.  
  
 Na przykład załóżmy, że kodu programu zadeklarowana stosu, który jest konstruowany liczb całkowitych:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 W tym momencie środowisko wykonawcze zgłasza wersji specjalistycznej metody <xref:System.Collections.Generic.Stack%601> klasy, która ma całkowitą odpowiednio zastąpiony parametrem. Teraz zawsze, gdy kod program używa stosu liczb całkowitych, wyspecjalizowany powtórnych czasu wykonywania wygenerowany <xref:System.Collections.Generic.Stack%601> klasy. W poniższym przykładzie są tworzone dwa wystąpienia stosu liczb całkowitych i one współdzielić jedno wystąpienie `Stack<int>` kodu:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Jednak Załóżmy, że oznacza innego <xref:System.Collections.Generic.Stack%601> klasy przy użyciu innego typu wartości, takich jak `long` lub struktury zdefiniowany przez użytkownika jako jego parametr jest tworzony w innym punkcie w kodzie. W rezultacie środowisko wykonawcze zgłasza inna wersja tego typu ogólnego i zastępuje `long` w odpowiednich miejscach w kodzie MSIL. Konwersje są już potrzebne, ponieważ każdy wyspecjalizowane klasy ogólnej natywnie zawiera typ wartości.  
  
 Typy ogólne działa nieco inaczej dla typów odwołań. Po raz pierwszy typ ogólny jest skonstruowany przy użyciu dowolnego typu odwołania, środowisko uruchomieniowe tworzy specjalne typu ogólnego z odwołania do obiektu podstawiane dla parametrów w MSIL. Następnie ilekroć dany skonstruowanego typu zostanie uruchomiony z typem referencyjnym, jako parametr, niezależnie od tego, jakiego typu, jest środowisko uruchomieniowe ponownie używa uprzednio utworzonej wersji specjalistycznej metody typu ogólnego. Jest to możliwe, ponieważ wszystkie odwołania mają taki sam rozmiar.  
  
 Załóżmy, że masz dwa typy referencyjne `Customer` klasy i `Order` klasy, a także Załóżmy, że utworzony stos `Customer` typów:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 W tym momencie środowisko wykonawcze zgłasza wersji specjalistycznej metody <xref:System.Collections.Generic.Stack%601> klasy, która przechowuje odwołania do obiektów, które są wypełniane później zamiast przechowywania danych. Załóżmy, że następny wiersz kodu tworzy stosu innego typu odwołania, który nosi nazwę `Order`:  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 W odróżnieniu od z typami wartości innego wyspecjalizowany wersję <xref:System.Collections.Generic.Stack%601> klasa nie jest tworzona dla `Order` typu. Zamiast tego wystąpienia wersji specjalistycznej metody <xref:System.Collections.Generic.Stack%601> klasa jest tworzona i `orders` zmienna jest ustawiona na odwoływać się do niego. Załóżmy, że następnie napotkał wiersz kodu, aby utworzyć stos `Customer` typu:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Podobnie jak w przypadku użycia poprzedniej <xref:System.Collections.Generic.Stack%601> utworzone za pomocą klasy `Order` wpisz inną instancję wyspecjalizowane <xref:System.Collections.Generic.Stack%601> klasa jest tworzona. Wskaźniki, które są w niej zawarte są ustawione na odwołanie to obszar pamięci rozmiar `Customer` typu. Ponieważ liczba typów referencyjnych może się różnić w sposób bardzo popularny od kolejnych programu implementacji języka C#, typów ogólnych znacznie zmniejsza ilość kodu przez ograniczenie do jednej liczby klas wyspecjalizowanych utworzony przez kompilator dla klas ogólnych typów referencyjnych.  
  
 Ponadto podczas tworzenia wystąpienia rodzajowego klasy C# za pomocą parametru wartości typu lub odwołanie do typu, odbicie można badać je w czasie wykonywania i można ustalić typu rzeczywistego i jego parametr typu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/index.md)
- [Typy ogólne](~/docs/standard/generics/index.md)
