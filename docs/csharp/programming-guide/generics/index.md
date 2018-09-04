---
title: Typy ogólne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 638612a0ece8e701b088c97e5dfc49362e6d6419
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506084"
---
# <a name="generics-c-programming-guide"></a>Typy ogólne (Przewodnik programowania w języku C#)
Typy ogólne zostały dodane do wersji języka C# i środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0. Ogólne wprowadzenie do programu .NET Framework pojęcia parametrami typu, które umożliwiają projektowanie klas i metod, które Odrocz specyfikację jeden lub więcej typów, dopóki klasy lub metody jest zadeklarowana i tworzone przez kod klienta. Na przykład za pomocą parametru typu generycznego T, można napisać jedną klasę, używaną przez inny kod klienta bez ponoszenia kosztów ani ryzyka rzutowania środowiska uruchomieniowego lub operacje na polach, jak pokazano poniżej:  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>Przegląd typów ogólnych  
  
-   Aby zmaksymalizować ponowne wykorzystanie kodu, bezpieczeństwa i wydajności, należy użyć typów ogólnych.  
  
-   Najczęściej używane typy ogólne są do tworzenia klas kolekcji.  
  
-   Biblioteka klas .NET Framework zawiera kilka nowych klas ogólnych kolekcji w <xref:System.Collections.Generic> przestrzeni nazw. Powinny one być stosowane zawsze, gdy to możliwe, zamiast klasy, takie jak <xref:System.Collections.ArrayList> w <xref:System.Collections> przestrzeni nazw.  
  
-   Możesz utworzyć własne interfejsy ogólne, klas, metod, zdarzeń i delegatów.  
  
-   Klasy ogólne może być ograniczona umożliwiające dostęp do metod w typach danych.  
  
-   W czasie wykonywania można uzyskać informacje na temat typów, które są używane w typie danych typu ogólnego przy użyciu odbicia.  
  
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

- <xref:System.Collections.Generic>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Typy](../../../csharp/programming-guide/types/index.md)  
- [\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)  
- [\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
- [Typy ogólne w .NET](../../../standard/generics/index.md)  