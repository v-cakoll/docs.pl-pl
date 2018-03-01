---
title: "Typy ogólne w czasie wykonywania (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5ef0b63b293ec277ebf9331e8f282ce2c1692d31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Typy ogólne w czasie wykonywania (Przewodnik programowania w języku C#)
Gdy ogólnym typie lub metoda jest kompilowany na język pośredni firmy Microsoft (MSIL), zawiera metadanych, który identyfikuje ją jako mający parametrów typu. Jak MSIL dla typu ogólnego jest używany różni się zależnie od Określa, czy parametr dostarczony typ ma wartość lub typ odwołania.  
  
 Gdy typem ogólnym najpierw jest tworzony z typem wartości jako parametru, środowiska uruchomieniowego tworzy specjalne typu ogólnego z dostarczony parametr lub parametry zastąpione w odpowiednich miejscach w MSIL. Specjalne typy ogólne są tworzone jeden raz dla każdego typu unikatową wartość, który jest używany jako parametr.  
  
 Na przykład załóżmy, że zadeklarowany stosu, który jest tworzony liczb całkowitych kodu źródłowego:  
  
 [!code-csharp[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]  
  
 W tym momencie środowiska uruchomieniowego generuje specjalna wersja <xref:System.Collections.Generic.Stack%601> klasy, która ma całkowitą zastępowane odpowiednio dla jej parametr. Teraz, gdy kod programu stosem liczb całkowitych, wygenerowany powtórnych środowiska uruchomieniowego specjalizowany <xref:System.Collections.Generic.Stack%601> klasy. W poniższym przykładzie są tworzone dwa wystąpienia stosu liczb całkowitych i mają pojedyncze wystąpienie `Stack<int>` kodu:  
  
 [!code-csharp[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]  
  
 Że to inny <xref:System.Collections.Generic.Stack%601> klasy z typem innej wartości, takich jak `long` lub struktury zdefiniowane przez użytkownika jako jego parametr jest tworzony w momencie innego w kodzie. W związku z tym środowiska uruchomieniowego generuje inna wersja tego typu ogólnego i namiastki `long` w odpowiednich miejscach w MSIL. Konwersje nie są już wymagane ponieważ każdy specjalne klasy ogólnej natywnie zawiera typ wartości.  
  
 Ogólne działają trochę inaczej dla typów referencyjnych. Podczas pierwszego typu ogólnego jest tworzony w przypadku każdego typu odwołanie środowiska uruchomieniowego tworzy specjalne typu ogólnego z odwołań do obiektów zastępowane dla parametrów w MSIL. Następnie zawsze skonstruowanego typu zostanie uruchomiony z typem referencyjnym, jako jego parametr, niezależnie od tego, jakiego typu jest środowisko uruchomieniowe ponownie utworzonej wcześniej specjalna wersja typu ogólnego. Jest to możliwe, ponieważ wszystkie odwołania mają taki sam rozmiar.  
  
 Załóżmy na przykład, ma dwa typy referencyjne `Customer` klasy i `Order` klasy, a także Załóżmy, że utworzony stos `Customer` typów:  
  
 [!code-csharp[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]  
  
 [!code-csharp[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]  
  
 W tym momencie środowiska uruchomieniowego generuje specjalna wersja <xref:System.Collections.Generic.Stack%601> klasy, która przechowuje odwołania do obiektów, które zostanie wypełnione później zamiast przechowywania danych. Załóżmy, że w następnym wierszu kodu tworzy stosu innego typu odwołania o nazwie `Order`:  
  
 [!code-csharp[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]  
  
 W odróżnieniu od z typami wartości innego specjalizowany wersji <xref:System.Collections.Generic.Stack%601> klasa nie został utworzony dla `Order` typu. Zamiast tego wystąpienia specjalna wersja <xref:System.Collections.Generic.Stack%601> klasa jest tworzona i `orders` ustawiono zmienną do utworzenia odwołania. Załóżmy, że następnie napotkano wiersza kodu w celu utworzenia stos `Customer` typu:  
  
 [!code-csharp[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]  
  
 Jak przy użyciu poprzedniej <xref:System.Collections.Generic.Stack%601> utworzone za pomocą klasy `Order` wpisz inne wystąpienie specjalne <xref:System.Collections.Generic.Stack%601> utworzyć klasy. Wskaźniki, które są w niej zawarte są ustawione, aby odwołać to obszar pamięci rozmiar `Customer` typu. Liczba typów referencyjnych może się różnić bardzo z do programu, implementacja C# ogólne znacznie zmniejsza ilość kodu dzięki zmniejszeniu do jednej liczby klas specjalne utworzone przez kompilator dla klas ogólnych typów odniesienia.  
  
 Ponadto po C# klasy ogólnej zostanie uruchomiony przy użyciu parametru wartości typu lub odwołanie do typu, odbicia można zbadać go w czasie wykonywania i być ustalona zarówno jego rzeczywisty typ, jak i jej parametr typu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Typy ogólne](~/docs/standard/generics/index.md)
