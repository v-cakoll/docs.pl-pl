---
title: "Klasy ogólne (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c92efd63f7b24917dc50ca0864f1a132c5c2bf00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generic-classes-c-programming-guide"></a>Klasy ogólne (Przewodnik programowania w języku C#)
Klasy ogólne hermetyzować operacje, które nie są specyficzne dla określonego typu danych. Jest najbardziej popularnym zastosowaniem klas ogólnych z kolekcjami, takie jak listy połączonej, tabelach skrótów, stosy, kolejek, drzewa i tak dalej. Operacje, takie jak dodawanie i usuwanie elementów z kolekcji są wykonywane w zasadniczo taki sam sposób, bez względu na typ przechowywanych danych.  
  
 Dla większości scenariuszy, które wymagają klasy kolekcji zalecanym rozwiązaniem jest użycie jednego z dostarczanych w bibliotece klas programu .NET Framework. Aby uzyskać więcej informacji o korzystaniu z tych klas, zobacz [typy ogólne w bibliotece klas programu .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).  
  
 Zazwyczaj do tworzenia klas rodzajowych począwszy od konkretnego istniejącej klasy, a zmiany typów w parametrach typu jeden w chwili, aż dojdziesz optymalną proporcję uogólnianie i użyteczność. Podczas tworzenia własnych klas rodzajowych, ważne następujące czynniki:  
  
-   Jakie typy do uogólnienia do parametrów typu.  
  
     Jako regułę, więcej typów, które można parametryzacja, bardziej elastyczne i do ponownego użycia kodu staje się. Jednak zbyt dużo generalizacji można tworzyć kod, który jest trudne dla innych projektantów do odczytu lub zrozumieć.  
  
-   Jakie ograniczenia, jeśli istnieją, aby zastosować do parametrów typu (zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).  
  
     Rozsądną regułą jest zastosowanie maksymalną ograniczenia możliwości umożliwiających będą nadal obsługiwać typy, które muszą obsługiwać. Na przykład jeśli wiadomo, że ogólny klasy jest przeznaczona do użycia tylko w przypadku typów referencyjnych, mają zastosowanie ograniczenia klasy. Uniemożliwi użycie niezamierzone klasy z typów wartości i umożliwi użytkownikowi korzystanie z `as` operator na `T`i sprawdź, czy wartości null.  
  
-   Określa, czy uwzględnić ogólne zachowanie podstawowych klas i podklas.  
  
     Ponieważ klasy rodzajowe mogą służyć jako klasy podstawowe, te same projektowania kwestie tutaj za pomocą klasy nieogólnego. Zobacz zasady dotyczące dziedziczenia z klasy podstawowej ogólne w dalszej części tego tematu.  
  
-   Określa, czy wdrożyć jeden lub więcej interfejsów ogólnych.  
  
     Na przykład w przypadku projektowania klasy, która będzie służyć do tworzenia elementów w kolekcji na podstawie ogólne, może być konieczne implementować interfejsu, takich jak <xref:System.IComparable%601> gdzie `T` jest typem klasy.  
  
 Na przykład prosty klasy ogólnej zobacz [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md).  
  
 Reguły dotyczące parametrów typu i ograniczenia dotyczą kilka zachowanie klasy ogólnej, szczególnie w odniesieniu do dziedziczenia i element członkowski ułatwień dostępu. Przed kontynuowaniem należy poznać niektóre warunki. Dla klasy ogólnej `Node<T>,` klienta kod można odwoływać się do klasy przez określenie typu argumentu, można utworzyć zamkniętego skonstruowanego typu (`Node<int>`). Alternatywnie można pozostawić parametr typu określony, na przykład po określeniu ogólny klasy podstawowej, można utworzyć otwarty skonstruować typu (`Node<T>`). Klasy ogólne może dziedziczyć z konkretnych, zamkniętego utworzone lub otwarte skonstruowane klas podstawowych:  
  
 [!code-csharp[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 Innymi słowy, specyficzne inne niż ogólne, klasy mogą dziedziczyć zamkniętego skonstruowane klas podstawowych, ale nie z klasy skonstruowane Otwórz lub parametrów typu, ponieważ w czasie wykonywania dla kodu klienta podać argument typu wymagane do utworzenia wystąpienia nie istnieje sposób Klasa podstawowa.  
  
 [!code-csharp[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 Klasy ogólne, które dziedziczą z Otwórz typy utworzone, musisz podać argumentów typu dla parametrów typu klasy podstawowej, które nie są udostępnione przez klasę dziedziczących, jak pokazano w poniższym kodzie:  
  
 [!code-csharp[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 Klasy ogólne, które dziedziczą z Otwórz typy utworzone musi określić ograniczeń, które są podzbiorem lub oznaczać ograniczenia dotyczące typu podstawowego:  
  
 [!code-csharp[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 Typy ogólne i można używać wielu parametrów typu ograniczenia, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 Otwórz typy utworzone skonstruowane i zamknięte może być używane jako parametry metody:  
  
 [!code-csharp[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 Jeśli klasy ogólnej implementuje interfejs, wszystkie wystąpienia tej klasy można rzutować na ten interfejs.  
  
 Klasy ogólne są niezmienne. Innymi słowy Jeśli określono parametr wejściowy `List<BaseClass>`, wystąpi błąd kompilacji Jeśli spróbujesz podaj `List<DerivedClass>`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
 [Zapisywanie stanu moduły wyliczające](http://go.microsoft.com/fwlink/?LinkId=112390)  
 [Układanki dziedziczenia jedną część](http://go.microsoft.com/fwlink/?LinkId=112380)
