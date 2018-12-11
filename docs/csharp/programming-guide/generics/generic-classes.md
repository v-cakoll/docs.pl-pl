---
title: Klasy ogólne — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 141da196869d3867a9a85087a073dbec095d5118
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244404"
---
# <a name="generic-classes-c-programming-guide"></a>Klasy ogólne (Przewodnik programowania w języku C#)
Klasy ogólne hermetyzować operacje, które nie są specyficzne dla określonego typu danych. Jest najbardziej popularnym zastosowaniem klas ogólnych kolekcji, takich jak połączonej listy, tabele zbędnych danych, stosów, kolejek, drzewa i tak dalej. Operacje, takie jak dodawanie i usuwanie elementów z kolekcji są wykonywane w zasadzie taki sam sposób niezależnie od rodzaju przechowywanych danych.  
  
 W przypadku większości scenariuszy, które wymagają klasy kolekcji Zalecanym podejściem jest użycie jednego z dostarczanych w bibliotece klas programu .NET. Aby uzyskać więcej informacji o korzystaniu z tych klas, zobacz [kolekcje ogólne w .NET](../../../standard/generics/collections.md).  
  
 Zazwyczaj tworzony klasy ogólne, począwszy od konkretnego istniejącej klasy, a zmiany typów w parametrach typu jeden do czasu osiągnięcia optymalną proporcję generalizacji i użyteczności tworzonych rozwiązań. Podczas tworzenia własnych klas ogólnych, istotne zagadnienia są następujące:  
  
-   Typy, które można uogólnić do parametrów typu.  
  
     Jako regułę, większą liczbę typów, które można zdefiniować parametry, bardziej elastyczne i wielokrotnego użytku staje się kodu. Zbyt dużo Generalizacja można jednak utworzyć kod, który jest trudny innym deweloperom do odczytu lub zrozumieć.  
  
-   Jakie ograniczenia, jeśli istnieją, aby zastosować do parametrów typu (zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).  
  
     Rozsądną regułą polega na zastosowaniu maksymalna ograniczenia możliwości, które pozwoli obsługiwać typy, które muszą obsługiwać. Na przykład jeśli wiesz, że Twoje klasy generycznej jest przeznaczony do użytku tylko w przypadku typów referencyjnych, mają zastosowanie ograniczenia klasy. Uniemożliwi niezamierzone korzystanie z klasy z typami wartości i umożliwi przy użyciu `as` operatora na `T`i sprawdź, czy dla wartości null.  
  
-   Określa, czy uwzględnić ogólne zachowanie podstawowych klas i podklas.  
  
     Ponieważ klas ogólnych może służyć jako klay bazowe, tym samym zagadnienia dotyczące projektowania zgłosić się tutaj podobnie jak w przypadku nieogólnej klasy. Zobacz reguły o dziedziczy z klasy bazowej ogólne w dalszej części tego tematu.  
  
-   Określa, czy zaimplementować jeden lub więcej interfejsów ogólnych.  
  
     Na przykład w przypadku projektowania klasę, która będzie służyć do tworzenia elementów w kolekcji na podstawie typów ogólnych, może być konieczne takich jak implementować interfejsu <xref:System.IComparable%601> gdzie `T` jest typem klasy.  
  
 Na przykład prosty klasy ogólnej zobacz [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md).  
  
 Reguły dotyczące parametrów typu i ograniczenia dotyczą kilka zachowanie klasy generycznej, szczególnie w odniesieniu do dziedziczenia i elementów członkowskich ułatwień dostępu. Przed kontynuowaniem należy poznać niektóre terminy. Dla klasy ogólnej `Node<T>,` kod klienta może odwoływać się do klasy albo poprzez określenie argument typ, Utwórz zamknięte skonstruowanego typu (`Node<int>`). Alternatywnie można pozostawić, parametr typu nie zostanie podany, na przykład po określeniu rodzajowego klasy podstawowej, aby utworzyć otwartą skonstruowany typ (`Node<T>`). Klasy ogólne może dziedziczyć z konkretnej, zamknięte zbudowane lub Otwórz skonstruowanych klasach bazowych:  
  
 [!code-csharp[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 Innymi słowy, betonu inne niż ogólne, klasy mogą dziedziczyć z zamknięty skonstruowanych klasach bazowych, ale nie otwieranie skonstruowany klasy lub parametry typu, ponieważ nie ma żadnego sposobu, w czasie wykonywania w przypadku kodu klienta podać argument typu wymagane do utworzenia wystąpienia Klasa bazowa.  
  
 [!code-csharp[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 Klasy ogólne, które dziedziczą z Otwórz typy utworzone, musisz podać argumenty typu parametrów typu klasy bazowej, które nie są współdzielone przez klasy dziedziczącej, jak pokazano w poniższym kodzie:  
  
 [!code-csharp[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 Klasy ogólne, które dziedziczą z Otwórz typy utworzone musi określić ograniczeń, które są podzbiorem, lub w sposób sugerujący ograniczenia dotyczące typu podstawowego:  
  
 [!code-csharp[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 Typy ogólne można użyć wielu parametrów typu i ograniczenia, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 Otwórz typy utworzone skonstruowany i zamknięte może służyć jako parametry metody:  
  
 [!code-csharp[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 Jeśli ogólne klasy implementuje interfejs, wszystkie wystąpienia tej klasy może być rzutowany tego interfejsu.  
  
 Klasy ogólne są niezmienne. Innymi słowy Jeśli określono parametr wejściowy `List<BaseClass>`, otrzymasz błąd kompilacji, jeśli zostanie podjęta próba zapewniają `List<DerivedClass>`.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
- [Zapisywanie stanu modułów wyliczających](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)  
- [Układanki dziedziczenia część pierwsza](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)
