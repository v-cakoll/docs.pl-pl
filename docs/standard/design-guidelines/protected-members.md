---
title: Chronione elementy członkowskie
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: KrzysztofCwalina
ms.openlocfilehash: 7d940f10799df2efc6c6d031781e1ef7cf777dd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559346"
---
# <a name="protected-members"></a>Chronione elementy członkowskie
Chronione elementy członkowskie samodzielnie nie oferuje żadnych rozszerzeń, ale mogą robić więjsze rozszerzona funkcjonalność dzięki podklasy bardziej wydajne. One może służyć do udostępnienia Dostosowywanie zaawansowane opcje bez niepotrzebnego komplikowania kodu języka głównego interfejsu publicznego.  
  
 Projektanci Framework, należy być ostrożnym z chronionych elementów członkowskich, ponieważ nazwa "protected" można nadać fałszywe poczucie bezpieczeństwa. Każda osoba ma możliwość podklasy niezapieczętowane klasy i dostęp do chronionych elementów członkowskich, a więc ten sam bezpiecznego kodowania, używane do publicznych elementów członkowskich dotyczą chronionych elementów członkowskich.  
  
 **✓ CONSIDER** przy użyciu chronione elementy członkowskie dostosowania zaawansowanego.  
  
 **✓ DO** Traktuj chronionych elementów członkowskich w klasach otwarty jako public na potrzeby analizy zabezpieczeń, dokumentacji i zgodności.  
  
 Każdy może dziedziczyć z klasy i dostęp do chronionych elementów członkowskich.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
