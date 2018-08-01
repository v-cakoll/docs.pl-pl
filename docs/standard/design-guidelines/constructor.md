---
title: Projekt — Konstruktor
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d7ca279dc1626cd526910af93326280bcd8301d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575560"
---
# <a name="constructor-design"></a>Projekt — Konstruktor
Istnieją dwa rodzaje konstruktory: wpisz konstruktorów i konstruktorów wystąpienia.  
  
 Konstruktory typu są statyczne i są uruchamiane przez środowisko CLR, zanim będzie można użyć tego typu. Konstruktory wystąpień uruchamiany po utworzeniu wystąpienia typu.  
  
 Konstruktorów typów nie przyjmuje żadnych parametrów. Konstruktory wystąpień może. Konstruktory wystąpień, które nie przyjmuje żadnych parametrów są często nazywane domyślnych konstruktorów.  
  
 Konstruktory są najbardziej naturalny sposób można utworzyć wystąpienia typu. Większość deweloperów będzie wyszukiwanie i spróbuj użyć konstruktora przed uznają alternatywnych sposobów tworzenia wystąpień (na przykład metodami factory).  
  
 **✓ CONSIDER** udostępnia prostą, najlepiej domyślne, konstruktorów.  
  
 Prosty konstruktor ma bardzo małą liczbę parametrów, a wszystkie parametry są pierwotnych lub wyliczeń. Takie proste konstruktorów zwiększyć użyteczność platformy.  
  
 **✓ CONSIDER** przy użyciu metody statycznej fabryki zamiast konstruktora semantykę Żądana operacja nie mapują bezpośrednio do tworzenia nowego wystąpienia, lub zgodnie z wytycznymi projektowania konstruktora tak nienaturalnej.  
  
 **✓ DO** parametry konstruktora jako skróty do ustawiania właściwości głównego.  
  
 Nie powinna istnieć różnicy w semantyki między przy użyciu pustego konstruktora następuje niektóre zestawy właściwości i konstruktora z wieloma argumentami.  
  
 **✓ DO** Użyj takiej samej nazwy dla parametrami konstruktora a właściwością, jeśli używane są parametry konstruktora wystarczy ustawić właściwości.  
  
 Jedyną różnicą między tych parametrów i właściwości powinny być wielkość liter.  
  
 **✓ DO** minimalnego pracy w konstruktorze.  
  
 Konstruktory należy wykonać dużo pracy innych niż przechwytywania parametrami konstruktora. Powinno zostać opóźnione koszt żadnych innych operacji, dopóki wymagane.  
  
 **✓ DO** zgłaszanie wyjątków z konstruktorów wystąpienia, w razie potrzeby.  
  
 **✓ DO** jawnie deklarować publicznego konstruktora domyślnego w klasach, jeśli takie Konstruktor jest wymagana.  
  
 Wszystkie konstruktory nie jawnie zadeklarowana w typie, wiele języków (na przykład C#) automatycznie doda publiczny konstruktor domyślny. (Klas abstrakcyjnych get Konstruktor chroniony).  
  
 Dodawanie sparametryzowanym konstruktorze do klasy uniemożliwia kompilator Dodawanie domyślnego konstruktora. Powoduje to często przypadkowemu najważniejszych zmian.  
  
 **X AVOID** jawnie Definiowanie domyślnych konstruktorów w strukturach.  
  
 Dzięki temu utworzenia tablicy szybciej, ponieważ jeśli nie zdefiniowano domyślnego konstruktora, ma być uruchamiane na każdym miejsca w tablicy. Należy pamiętać, że struktury mieć konstruktorów bez parametrów z tego powodu nie zezwalaj na wiele kompilatorów, w tym C#.  
  
 **X AVOID** wywoływania wirtualne elementy członkowskie dla obiekt wewnątrz jego konstruktora.  
  
 Wywołanie elementu członkowskiego wirtualnego spowoduje najdalszych pochodnych zastąpienie do wywołania, nawet wtedy, gdy Konstruktor typu najbardziej pochodnej nie pełni uruchomiono jeszcze.  
  
### <a name="type-constructor-guidelines"></a>Wskazówki dotyczące konstruktora typu  
 **✓ DO** Oznacz jako prywatne konstruktory statyczne.  
  
 Konstruktor statyczny, nazywany również konstruktora klasy służy do inicjowania typu. Środowisko CLR wywołuje konstruktor statyczny przed utworzeniu pierwszego wystąpienia typu lub są nazywane żadnych statycznych elementów członkowskich tego typu. Użytkownik nie ma kontroli nad podczas wywołania konstruktora statycznego. Jeśli Konstruktor statyczny nie jest prywatne, może być wywoływany przez kod innych niż środowiska CLR. W zależności od operacji wykonywanych w Konstruktorze może to spowodować nieoczekiwane zachowanie. Kompilator języka C# wymusza konstruktory statyczne ma charakter prywatny.  
  
 **X DO NOT** zgłaszanie wyjątków z konstruktorów statycznych.  
  
 Jeśli z konstruktora typu jest zgłaszany wyjątek, typ nie jest użyteczne w bieżącej domenie aplikacji.  
  
 **✓ CONSIDER** inicjowanie pól statycznych zamiast jawnie konstruktory statyczne, ponieważ środowisko uruchomieniowe jest w stanie zoptymalizować wydajność typy, które nie mają jawnie zdefiniowanych Konstruktor statyczny.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
