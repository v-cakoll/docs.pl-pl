---
title: Wirtualne składowe
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: KrzysztofCwalina
ms.openlocfilehash: 4943ddcdf1bc4e3e32c8d664cbcc5c50ae3959bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778712"
---
# <a name="virtual-members"></a>Wirtualne składowe
Wirtualne elementy członkowskie można zastąpić, zmieniając w ten sposób zachowanie podklasy. Są bardzo podobne do wywołania zwrotne pod kątem rozszerzalności, które zapewniają one, ale są one lepsze pod względem wydajności wykonywania i zużycie pamięci. Ponadto wirtualnych elementów członkowskich czuć się bardziej naturalne w scenariuszach wymagających tworzenia specjalnego rodzaju istniejącego typu (Specjalizacja).  
  
 Wirtualne elementy członkowskie mają lepszą wydajność niż wywołania zwrotne i zdarzenia, ale nie mają lepszą wydajność niż metod niewirtualnych.  
  
 Główną wadą wirtualnych elementów członkowskich jest, że zachowanie wirtualny element członkowski może być modyfikowane tylko w czasie kompilacji. Można zmodyfikować zachowanie wywołanie zwrotne w czasie wykonywania.  
  
 Wirtualne elementy członkowskie, takie jak wywołania zwrotne i może być większa niż wywołań zwrotnych, są kosztowne do projektowania, testowania i obsługi, ponieważ każde wywołanie wirtualny element członkowski może zostać przesłonięta w sposób nieprzewidziany i może wykonywać dowolny kod. Ponadto znacznie więcej nakładu pracy zwykle jest wymagany do jasno zdefiniować kontrakt wirtualnych elementów członkowskich, więc koszt projektowania i dokumentowanie ich jest wyższy.  
  
 **X DO NOT** tworzenie elementów członkowskich wirtualnego, chyba że masz powód, dla zrobić i poznać wszystkich kosztów związanych z projektowania i testowania oraz Obsługa wirtualnych elementów członkowskich.  
  
 Wirtualne elementy członkowskie są mniej forgiving pod względem zmiany wprowadzone do nich w bez przerywania zgodność. Ponadto są wolniejsze niż niewirtualną członków, przede wszystkim, ponieważ wywołania wirtualne elementy członkowskie nie są śródwierszowych.  
  
 **✓ CONSIDER** ograniczanie rozszerzalności tylko co to jest bezwzględnie konieczne.  
  
 **✓ DO** Preferuj dostępności chronione przed powszechnej dostępności dla wirtualnych elementów członkowskich. Publiczne elementy Członkowskie powinny rozszerzalność (jeśli jest to wymagane) przez wywołanie chronionych wirtualna elementu członkowskiego.  
  
 Publiczne elementy członkowskie klasy dostarczają właściwy zestaw funkcji dla bezpośrednich klientów tej klasy. Wirtualne elementy członkowskie są przeznaczone do zastąpienia w podklasy i chronionych ułatwień dostępu jest to doskonały sposób, aby ograniczyć zakres wszystkie punkty rozszerzalności wirtualny, gdzie mogą być używane do.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
