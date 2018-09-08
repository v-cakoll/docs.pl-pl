---
title: Projekt konstruktora
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
ms.openlocfilehash: 6ad920c8028b102a13fdfe928d21768538e25b0f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180452"
---
# <a name="constructor-design"></a>Projekt konstruktora
Istnieją dwa rodzaje konstruktorów: wpisz konstruktorów i konstruktorów wystąpienia.  
  
 Konstruktorzy typów są statyczne i są uruchamiane przez środowisko CLR, zanim typ jest używany. Konstruktory wystąpień uruchamiane, gdy tworzone jest wystąpienie typu.  
  
 Konstruktorzy typów nie przyjmuje żadnych parametrów. Konstruktory wystąpień może. Konstruktory wystąpień, które nie przyjmuje żadnych parametrów są często nazywane domyślnych konstruktorów.  
  
 Konstruktory są najbardziej naturalny sposób tworzenia wystąpień tego typu. Większość programistów poszuka i spróbuj użyć konstruktora, zanim rozważa alternatywne sposoby tworzenia wystąpień (takie jak metodach fabryki).  
  
 **✓ CONSIDER** udostępnia prostą, najlepiej domyślne, konstruktorów.  
  
 Proste Konstruktor ma bardzo niewielkiej liczby parametrów, a wszystkie parametry są w nim elementów podstawowych lub wyliczenia. Takie proste konstruktory zwiększyć użyteczność Framework.  
  
 **✓ CONSIDER** przy użyciu metody statycznej fabryki zamiast konstruktora semantykę Żądana operacja nie mapują bezpośrednio do tworzenia nowego wystąpienia, lub zgodnie z wytycznymi projektowania konstruktora tak nienaturalnej.  
  
 **✓ DO** parametry konstruktora jako skróty do ustawiania właściwości głównego.  
  
 Powinna istnieć nie różnice w semantyce między za pomocą pustego konstruktora, następuje niektórych zestawów właściwości i za pomocą konstruktora z wielu argumentów.  
  
 **✓ DO** Użyj takiej samej nazwy dla parametrami konstruktora a właściwością, jeśli używane są parametry konstruktora wystarczy ustawić właściwości.  
  
 Jedyną różnicą między takie parametry i właściwości powinny być wielkość liter.  
  
 **✓ DO** minimalnego pracy w konstruktorze.  
  
 Konstruktory nie powinien wykonać dużo pracy innych niż przechwytywania parametry konstruktora. Koszt dowolne inne procesy przetwarzania powinno zostać opóźnione, dopóki nie jest wymagane.  
  
 **✓ DO** zgłaszanie wyjątków z konstruktorów wystąpienia, w razie potrzeby.  
  
 **✓ DO** jawnie deklarować publicznego konstruktora domyślnego w klasach, jeśli takie Konstruktor jest wymagana.  
  
 Jeśli w danym typie, nie jawnie deklarować żadnych konstruktorów, wielu języków (takich jak C#) spowoduje automatyczne dodanie publicznego konstruktora domyślnego. (Klasy abstrakcyjne uzyskać Konstruktor chroniony).  
  
 Dodawanie sparametryzowania konstruktora do klasy zapobiega dodawaniu konstruktora domyślnego przez kompilator. To często powoduje, że przypadkowe przełomowe zmiany.  
  
 **X AVOID** jawnie Definiowanie domyślnych konstruktorów w strukturach.  
  
 Ułatwia to utworzenie tablicy szybciej, ponieważ jeśli nie zdefiniowano domyślnego konstruktora, nie ma być uruchamiane na każdego miejsca, w tablicy. Należy pamiętać, że wiele kompilatorów, w tym C#, nie zezwalaj na zwracanie struktur mieć konstruktory bez parametrów, dlatego.  
  
 **X AVOID** wywoływania wirtualne elementy członkowskie dla obiekt wewnątrz jego konstruktora.  
  
 Wywołanie wirtualna elementu członkowskiego spowoduje zastąpienie najbardziej pochodnej, można wywołać, nawet wtedy, gdy Konstruktor typu najbardziej pochodnego nie został w pełni uruchomiony jeszcze.  
  
### <a name="type-constructor-guidelines"></a>Wytyczne dotyczące konstruktora typu  
 **✓ DO** Oznacz jako prywatne konstruktory statyczne.  
  
 Statyczny Konstruktor, nazywany również konstruktora klasy jest używany do inicjowania typu. Środowisko CLR wywołuje statyczny Konstruktor przed utworzeniu pierwszego wystąpienia tego typu lub wszelkich statyczne elementy członkowskie tego typu są wywoływane. Użytkownik nie ma kontroli nad kiedy wywoływany jest konstruktor statyczny. Jeśli Konstruktor statyczny nie jest prywatny, może ona zostać wywołana przez kod inny niż środowiska CLR. W zależności od operacje wykonywane w Konstruktorze może to spowodować nieoczekiwane zachowanie. Kompilator języka C# wymusza konstruktorów statycznych jako prywatne.  
  
 **X DO NOT** zgłaszanie wyjątków z konstruktorów statycznych.  
  
 Jeśli wyjątek jest zgłaszany z konstruktora typu, typ nie jest użyteczny w bieżącej domenie aplikacji.  
  
 **✓ CONSIDER** inicjowanie pól statycznych zamiast jawnie konstruktory statyczne, ponieważ środowisko uruchomieniowe jest w stanie zoptymalizować wydajność typy, które nie mają jawnie zdefiniowanych Konstruktor statyczny.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
