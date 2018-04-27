---
title: Wirtualne elementy członkowskie
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1b7abe1dbeb7f4888dd8ee4001b410cc583935c4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="virtual-members"></a>Wirtualne elementy członkowskie
Wirtualne elementy Członkowskie mogą zostać zastąpione, w związku z tym zmiany zachowania podklasy. Są bardzo podobne do wywołania zwrotne pod względem rozszerzania, które zapewniają, ale są one lepsze pod względem wydajności wykonywania i zmniejszenie zużycia pamięci. Ponadto wirtualne elementy członkowskie możesz bardziej naturalne w scenariuszach wymagających tworzenie specjalny rodzaj istniejącego typu (Specjalizacja).  
  
 Wirtualne elementy członkowskie lepiej niż wywołania zwrotne i zdarzeń, ale nie wykonuj lepiej niż metody-virtual.  
  
 Główną wadą wirtualnych elementów członkowskich jest, że zachowanie elementu członkowskiego wirtualnego można modyfikować tylko w czasie kompilacji. Zachowanie wywołania zwrotnego może być modyfikowany w czasie wykonywania.  
  
 Wirtualne elementy członkowskie, takie jak wywołania zwrotne i może być większa niż wywołań zwrotnych, są kosztowne do projektowania, testowania i konserwacji, ponieważ jakiekolwiek odwołania do elementu członkowskiego wirtualnego może zostać zastąpiona w sposób nieprzewidziany i może zostać uruchomiony dowolny kod. Ponadto znacznie więcej wysiłku jest zazwyczaj wymagane jasno zdefiniować kontrakt wirtualne elementy członkowskie, więc koszt projektowanie i dokumentowanie ich jest wyższy.  
  
 **X nie** tworzenie elementów członkowskich wirtualnego, chyba że masz powód, dla zrobić i poznać wszystkich kosztów związanych z projektowania i testowania oraz Obsługa wirtualnych elementów członkowskich.  
  
 Wirtualne elementy członkowskie są mniej forgiving pod względem zmiany wprowadzone do nich w bez przerywania zgodności. Ponadto są one wolniej niż członków-virtual, przede wszystkim, ponieważ wywołania wirtualne elementy członkowskie nie są wbudowane.  
  
 **ROZWAŻ ✓** ograniczanie rozszerzalności tylko co to jest bezwzględnie konieczne.  
  
 **CZY ✓** Preferuj dostępności chronione przed powszechnej dostępności dla wirtualnych elementów członkowskich. Publiczne elementy Członkowskie powinny rozszerzalność (jeśli jest to wymagane) przez wywołanie do chronionego członka wirtualnego.  
  
 Publiczne elementy członkowskie klasy powinien zapewnić prawidłowego zestawu funkcji do bezpośredniego konsumentów tej klasy. Wirtualne elementy członkowskie zaprojektowano do zastąpienia w podklasach i dostępność chronionych jest to dobry sposób na zakres wszystkie punkty rozszerzalności wirtualnego, gdzie mogą być używane.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
