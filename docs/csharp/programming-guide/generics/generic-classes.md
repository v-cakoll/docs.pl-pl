---
title: Klasy ogólne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 6eb4df4489f4b377c68c5d49d1bf0bb01b835e85
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589767"
---
# <a name="generic-classes-c-programming-guide"></a>Klasy ogólne (Przewodnik programowania w języku C#)
Klasy ogólne hermetyzują operacje, które nie są specyficzne dla określonego typu danych. Najbardziej typowym zastosowaniem klas ogólnych jest kolekcje, takie jak listy połączone, tabele skrótów, stosy, kolejki, drzewa i tak dalej. Operacje, takie jak dodawanie i usuwanie elementów z kolekcji, są wykonywane w taki sam sposób, niezależnie od typu przechowywanych danych.  
  
 W przypadku większości scenariuszy, które wymagają klas kolekcji, Zalecanym podejściem jest użycie tych, które znajdują się w bibliotece klas .NET. Aby uzyskać więcej informacji o korzystaniu z tych klas, zobacz [kolekcje ogólne w programie .NET](../../../standard/generics/collections.md).  
  
 Zazwyczaj tworzysz klasy generyczne, rozpoczynając od istniejącej konkretnej klasy i zmieniając typy na parametry typu jeden na raz, aż osiągniesz optymalny bilans generalizacji i użyteczności. Podczas tworzenia własnych klas ogólnych ważne są następujące zagadnienia:  
  
- Które typy są uogólniać do parametrów typu.  
  
     Im więcej typów, które można Sparametryzuj, tym bardziej elastyczne i wielokrotne użycie kodu stanie się. Jednak zbyt wiele generalizacji może utworzyć kod, który jest trudny do odczytania lub zrozumienia dla innych deweloperów.  
  
- Jakie ograniczenia (jeśli istnieją) mają być stosowane do parametrów typu (zobacz [ograniczenia dotyczące parametrów typu](./constraints-on-type-parameters.md)).  
  
     Dobrą regułą jest zastosowanie maksymalnych ograniczeń, które nadal będą obsługiwać typy, które należy obsłużyć. Na przykład jeśli wiesz, że Klasa generyczna jest przeznaczona do użycia tylko z typami referencyjnymi, Zastosuj ograniczenie klasy. Uniemożliwi to niezamierzone użycie klasy z typami wartości i umożliwi użycie `as` operatora na `T`i sprawdzenie wartości null.  
  
- Czy należy wziąć pod uwagę ogólne zachowanie w klasach bazowych i podklasach.  
  
     Ponieważ klasy generyczne mogą działać jako klasy bazowe, te same zagadnienia dotyczące projektowania są stosowane w tym miejscu, jak w przypadku klas innych niż ogólne. Zapoznaj się z regułami dotyczącymi dziedziczenia z generycznych klas podstawowych w dalszej części tego tematu.  
  
- Czy zaimplementować co najmniej jeden interfejs generyczny.  
  
     Na przykład w przypadku projektowania klasy, która będzie używana do tworzenia elementów w kolekcji generycznej, może być konieczne zaimplementowanie interfejsu, takiego jak <xref:System.IComparable%601> gdzie `T` jest typem klasy.  
  
 Aby zapoznać się z przykładem prostej klasy generycznej, zobacz [wprowadzenie do typów ogólnych](./index.md).  
  
 Reguły dotyczące parametrów typu i ograniczeń mają różne konsekwencje dla zachowania klasy ogólnej, szczególnie dotyczące dziedziczenia i dostępności elementów członkowskich. Przed kontynuowaniem należy zrozumieć pewne warunki. Dla kodu klienta klasy `Node<T>,` generycznej może odwoływać się do klasy przez określenie argumentu typu, aby utworzyć zamknięty typ skonstruowany (`Node<int>`). Alternatywnie można pozostawić parametr typu nieokreślony, na przykład podczas określania generycznej klasy podstawowej, aby utworzyć otwarty typ skonstruowany (`Node<T>`). Klasy generyczne mogą dziedziczyć z konkretnych, zamkniętych skonstruowanych lub otwartych klas bazowych:  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 Nieogólne, innymi słowy, klasy mogą dziedziczyć po zamkniętych skonstruowanych klasach bazowych, ale nie z otwartych klas skonstruowanych lub parametrów typu, ponieważ w czasie wykonywania dla kodu klienta nie ma żadnego sposobu na dostarczenie argumentu typu wymaganego do wystąpienia Klasa bazowa.  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 Klasy generyczne dziedziczące od typów typu "Opened" muszą dostarczać argumenty typu dla wszystkich parametrów klasy bazowej, które nie są współużytkowane przez klasę dziedziczenia, jak pokazano w poniższym kodzie:  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 Klasy generyczne dziedziczące z typów typu "Open skonstruowane" muszą określać ograniczenia, które są nadzbiorem lub implikują ograniczenia dotyczące typu podstawowego:  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 Typy ogólne mogą używać wielu parametrów typu i ograniczeń w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 Jako parametry metody można użyć otwartych i zamkniętych typów skonstruowanych:  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 Jeśli Klasa ogólna implementuje interfejs, wszystkie wystąpienia tej klasy mogą być rzutowane do tego interfejsu.  
  
 Klasy generyczne są niezmienne. Innymi słowy, jeśli parametr wejściowy określa `List<BaseClass>`, zostanie wyświetlony błąd czasu kompilacji, jeśli spróbujesz `List<DerivedClass>`podać.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Typy ogólne](./index.md)
- [Zapisywanie stanu modułów wyliczających](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)
- [Dziedziczenie, część jedna](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)
