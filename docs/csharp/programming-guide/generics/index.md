---
title: Typy ogólne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 8f412366072c81b8aaca94829e0aa214f356200d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333817"
---
# <a name="generics-c-programming-guide"></a>Typy ogólne (Przewodnik programowania w języku C#)
Typy ogólne zostały dodane do wersji 2.0 języka C# i środowisko uruchomieniowe języka wspólnego (CLR). Ogólne wprowadzenie do programu .NET Framework pojęcia parametrów typu, które umożliwiają do projektu klasy i metody, które mają być odroczone specyfikację jeden lub więcej typów, aż klasa lub metoda jest zadeklarowany i utworzone przez kod klienta. Na przykład za pomocą parametru typu ogólnego T można napisać jedną klasę, używaną przez inny kod klienta bez ponoszenia kosztów lub ryzyka środowiska uruchomieniowego rzutowania lub konwersji boxing operacji, jak pokazano poniżej:  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>Ogólne omówienie  
  
-   Typy ogólne można używać w celu zwiększenia ponowne użycie kodu, zabezpieczeń i wydajności.  
  
-   Najbardziej typowe typów ogólnych polega na utworzeniu klasy kolekcji.  
  
-   Biblioteka klas programu .NET Framework zawiera kilka nowych klas kolekcji ogólnych w <xref:System.Collections.Generic> przestrzeni nazw. Powinny być one używane zawsze, gdy to możliwe, zamiast klas takich jak <xref:System.Collections.ArrayList> w <xref:System.Collections> przestrzeni nazw.  
  
-   Możesz utworzyć własne ogólnych interfejsów, klas, metod, zdarzeń i delegatów.  
  
-   Klasy ogólne może ograniczonego umożliwiające dostęp do metody na typach danych.  
  
-   W czasie wykonywania można uzyskać informacji o typach, które są używane w typie ogólnym danych przy użyciu odbicia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
-   [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [Zalety typów ogólnych](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [Parametry typu ogólnego](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [Ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [Klasy ogólne](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [Interfejsy ogólne](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [Metody ogólne](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [Delegaci ogólni](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [Różnice między szablonami C++ i typami ogólnymi C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [Typy ogólne i odbicie](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [Typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
 [Typy ogólne w .NET](../../../standard/generics/index.md)  