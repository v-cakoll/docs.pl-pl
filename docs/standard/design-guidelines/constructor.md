---
title: Projekt konstruktora
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: KrzysztofCwalina
ms.openlocfilehash: 074aa391b71257584a01171e95da7472354cdc2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746775"
---
# <a name="constructor-design"></a>Projekt konstruktora
Istnieją dwa rodzaje konstruktorów: wpisz konstruktorów i konstruktorów wystąpienia.  
  
 Konstruktorzy typów są statyczne i są uruchamiane przez środowisko CLR, zanim typ jest używany. Konstruktory wystąpień uruchamiane, gdy tworzone jest wystąpienie typu.  
  
 Konstruktorzy typów nie przyjmuje żadnych parametrów. Konstruktory wystąpień może. Konstruktory wystąpień, które nie przyjmuje żadnych parametrów są często nazywane konstruktorów bez parametrów.  
  
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
  
 **CZY ✓** jawnie deklarować publicznego konstruktora bez parametrów w klasach, jeśli taki Konstruktor jest wymagana.  
  
 Jeśli nie jawnie deklarować żadnych konstruktorów typu, wielu języków (takie jak C#) automatycznie doda publiczny konstruktor bez parametrów. (Klasy abstrakcyjne uzyskać Konstruktor chroniony).  
  
 Dodawanie sparametryzowania konstruktora do klasy zabezpiecza kompilator przed dodanie konstruktora bez parametrów. To często powoduje, że przypadkowe przełomowe zmiany.  
  
 **X należy UNIKAĆ** jawne określenie konstruktorów bez parametrów w strukturach.  
  
 Ułatwia to utworzenie tablicy szybciej, ponieważ jeśli nie zdefiniowano konstruktora bez parametrów, ma być uruchamiane na każdego miejsca, w tablicy. Należy pamiętać, że wiele kompilatorów, w tym C#, nie zezwalaj na zwracanie struktur mieć konstruktory bez parametrów, dlatego.  
  
 **X AVOID** wywoływania wirtualne elementy członkowskie dla obiekt wewnątrz jego konstruktora.  
  
 Wywołanie wirtualna elementu członkowskiego spowoduje zastąpienie najbardziej pochodnej, można wywołać, nawet wtedy, gdy Konstruktor typu najbardziej pochodnego nie został w pełni uruchomiony jeszcze.  
  
### <a name="type-constructor-guidelines"></a>Wytyczne dotyczące konstruktora typu  
 **✓ DO** Oznacz jako prywatne konstruktory statyczne.  
  
 Statyczny Konstruktor, nazywany również konstruktora klasy jest używany do inicjowania typu. Środowisko CLR wywołuje statyczny Konstruktor przed utworzeniu pierwszego wystąpienia tego typu lub wszelkich statyczne elementy członkowskie tego typu są wywoływane. Użytkownik nie ma kontroli nad kiedy wywoływany jest konstruktor statyczny. Jeśli Konstruktor statyczny nie jest prywatny, może ona zostać wywołana przez kod inny niż środowiska CLR. W zależności od operacje wykonywane w Konstruktorze może to spowodować nieoczekiwane zachowanie. Kompilator języka C# wymusza konstruktorów statycznych jako prywatne.  
  
 **X DO NOT** zgłaszanie wyjątków z konstruktorów statycznych.  
  
 Jeśli wyjątek jest zgłaszany z konstruktora typu, typ nie jest użyteczny w bieżącej domenie aplikacji.  
  
 **✓ CONSIDER** inicjowanie pól statycznych zamiast jawnie konstruktory statyczne, ponieważ środowisko uruchomieniowe jest w stanie zoptymalizować wydajność typy, które nie mają jawnie zdefiniowanych Konstruktor statyczny.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
