---
title: Klasy ogólne — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 1fdfaa833ad32428d341b6f3a61cc7f638036183
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937503"
---
# <a name="generic-classes-c-programming-guide"></a>Klasy ogólne (Przewodnik programowania w języku C#)
Klasy ogólne hermetyzują operacje, które nie są specyficzne dla określonego typu danych. Najczęstszym zastosowaniem dla klas ogólnych jest z kolekcji, takich jak listy połączone, tabele mieszania, stosy, kolejki, drzewa i tak dalej. Operacje, takie jak dodawanie i usuwanie elementów z kolekcji są wykonywane w zasadzie w taki sam sposób, niezależnie od typu przechowywanych danych.  
  
 W przypadku większości scenariuszy, które wymagają klas kolekcji, zaleca się podejście jest użycie tych, które są podane w bibliotece klas .NET. Aby uzyskać więcej informacji na temat korzystania z tych klas, zobacz [Kolekcje ogólne w .NET](../../../standard/generics/collections.md).  
  
 Zazwyczaj można utworzyć klasy ogólne, zaczynając od istniejącej klasy betonu i zmieniając typy na parametry typu po jednym naraz, aż do osiągnięcia optymalnej równowagi uogólnienia i użyteczności. Podczas tworzenia własnych klas ogólnych ważne zagadnienia obejmują następujące kwestie:  
  
- Które typy do uogólniania do parametrów typu.  
  
     Z reguły im więcej typów można parametryzować, tym bardziej elastyczny i wielokrotnego użytku staje się kod. Jednak zbyt wiele generalizacji można utworzyć kod, który jest trudny do odczytania lub zrozumienia dla innych deweloperów.  
  
- Jakie ograniczenia, jeśli istnieją, aby zastosować do parametrów typu (zobacz [Ograniczenia parametrów typu](./constraints-on-type-parameters.md)).  
  
     Dobrą zasadą jest zastosowanie maksymalnych możliwych ograniczeń, które nadal umożliwiają obsługę typów, które należy obsługiwać. Na przykład jeśli wiesz, że klasa ogólna jest przeznaczona tylko do użytku z typami odwołań, należy zastosować ograniczenie klasy. Zapobiegnie to niezamierzonemu użyciu klasy z typami wartości `as` i `T`umożliwi użycie operatora na i sprawdzenie wartości null.  
  
- Czy uwzględniać ogólne zachowanie w klasach podstawowych i podklasach.  
  
     Ponieważ klasy ogólne mogą służyć jako klasy podstawowe, te same zagadnienia dotyczące projektowania mają zastosowanie w tym miejscu, jak w przypadku klas nieogólnych. Zobacz reguły dotyczące dziedziczenia z ogólnych klas podstawowych w dalszej części tego tematu.  
  
- Czy zaimplementować jeden lub więcej ogólnych interfejsów.  
  
     Na przykład jeśli projektujesz klasę, która będzie używana do tworzenia elementów w kolekcji opartej na rodzajowych, może być konieczne zaimplementowanie interfejsu, takiego jak <xref:System.IComparable%601> where `T` jest typem klasy.  
  
 Na przykład prostej klasy ogólnej zobacz [Wprowadzenie do typów ogólnych](./index.md).  
  
 Reguły parametrów typu i ograniczeń mają kilka implikacji dla zachowania klasy ogólnej, szczególnie w odniesieniu do dziedziczenia i dostępności elementu członkowskiego. Przed kontynuowaniem należy zapoznać się z pewnymi terminami. Dla klasy `Node<T>,` ogólnej kod klienta może odwoływać się do klasy albo określając`Node<int>`argument typu, aby utworzyć zamknięty typ konstruowany ( ). Alternatywnie może pozostawić parametr typu nieokreślony, na przykład po określeniu ogólnej klasy podstawowej, aby utworzyć otwarty typ konstruowany (`Node<T>`). Klasy ogólne mogą dziedziczyć z betonu, zamknięte skonstruowane lub otwarte skonstruowane klasy podstawowe:  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 Non-generic, innymi słowy konkretne, klasy mogą dziedziczyć z zamkniętych skonstruowanych klas podstawowych, ale nie z otwartych klas skonstruowanych lub z parametrów typu, ponieważ nie ma sposobu w czasie wykonywania dla kodu klienta, aby podać argument typu wymagany do wystąpienia wystąpienia klasy podstawowej.  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 Klasy ogólne, które dziedziczą z otwartych typów skonstruowanych musi podać argumenty typu dla wszystkich parametrów typu klasy podstawowej, które nie są współużytkowane przez klasę dziedziczenia, jak pokazano w następującym kodzie:  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 Klasy ogólne, które dziedziczą z otwartych typów skonstruowanych musi określić ograniczenia, które są nadzbiorem lub sugerować, ograniczenia typu podstawowego:  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 Typy ogólne mogą używać wielu parametrów i ograniczeń typu w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 Jako parametry metody można stosować typy konstrukcji skonstruowanych i zamkniętych:  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 Jeśli klasa ogólna implementuje interfejs, wszystkie wystąpienia tej klasy mogą być rzutowani do tego interfejsu.  
  
 Klasy ogólne są niezmienne. Innymi słowy, jeśli parametr wejściowy `List<BaseClass>`określa , otrzymasz błąd czasu kompilacji, jeśli `List<DerivedClass>`spróbujesz podać .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [Przewodnik programowania języka C#](../index.md)
- [Typy ogólne](./index.md)
- [Zapisywanie stanu wyliczaczy](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [Zagadka dziedziczenia, część pierwsze](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
