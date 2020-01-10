---
title: Wirtualne składowe
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 2c1e6d9aeafa1c9d7ee4b0c2c626b6fd7be6cf99
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708974"
---
# <a name="virtual-members"></a>Wirtualne składowe
Wirtualne elementy członkowskie można przesłonić, zmieniając zachowanie podklasy. Są one bardzo podobne do wywołania zwrotnego pod względem rozszerzalności, które zapewnia, ale są lepsze pod względem wydajności i zużycia pamięci. Ponadto wirtualne elementy członkowskie działają bardziej naturalnie w scenariuszach, które wymagają utworzenia specjalnego rodzaju istniejącego typu (specjalizacji).  
  
 Wirtualne elementy członkowskie działają lepiej niż wywołania zwrotne i zdarzenia, ale nie wykonują lepszych możliwości niż w przypadku metod innych niż wirtualne.  
  
 Główna wada wirtualnych elementów członkowskich polega na tym, że zachowanie wirtualnej składowej może być modyfikowane tylko w czasie kompilacji. Zachowanie wywołania zwrotnego można modyfikować w czasie wykonywania.  
  
 Wirtualne elementy członkowskie, takie jak wywołania zwrotne (i mogą być większe niż wywołania zwrotne), są kosztowne do projektowania, testowania i konserwowania, ponieważ każde wywołanie elementu wirtualnego można przesłonić w sposób nieprzewidywalny i można wykonać dowolny kod. Ponadto zwykle wymagane jest wyraźne określenie kontraktu wirtualnych elementów członkowskich, dzięki czemu koszt projektowania i dokumentowania jest wyższy.  
  
 **X DO NOT** tworzenie elementów członkowskich wirtualnego, chyba że masz powód, dla zrobić i poznać wszystkich kosztów związanych z projektowania i testowania oraz Obsługa wirtualnych elementów członkowskich.  
  
 Wirtualne elementy członkowskie są mniej łagodniejszej pod względem zmian, które mogą być w nich przeznaczone bez przerywania zgodności. Ponadto są one wolniejsze niż wirtualne elementy członkowskie, głównie ponieważ wywołania wirtualnych elementów członkowskich nie są wbudowane.  
  
 **✓ CONSIDER** ograniczanie rozszerzalności tylko co to jest bezwzględnie konieczne.  
  
 **✓ DO** Preferuj dostępności chronione przed powszechnej dostępności dla wirtualnych elementów członkowskich. Publiczne składowe powinny zapewnić rozszerzalność (jeśli jest to wymagane), wywołując do chronionej wirtualnej składowej.  
  
 Publiczne składowe klasy powinny zapewnić odpowiedni zestaw funkcji dla bezpośrednich odbiorców tej klasy. Wirtualne elementy członkowskie zostały zaprojektowane do przesłania w podklasach, a funkcja chronionej dostępności to świetny sposób określania zakresu wszystkich wirtualnych punktów rozszerzalności, gdzie mogą być używane.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
