---
title: Niezapieczętowane klasy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: 8d7b1500506ec73a0d33d5352756cb85039358e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153231"
---
# <a name="unsealed-classes"></a>Niezapieczętowane klasy
Zapieczętowane klasy nie może być dziedziczona z i zapobiegają one rozszerzalności. Z kolei klas, które mogą być dziedziczone z są nazywane niezapieczętowane klasy.  
  
 **✓ CONSIDER** przy użyciu niezapieczętowanych klas bez dodać wirtualnych lub chronionych elementów członkowskich, ponieważ doskonałym sposobem zapewnienia niedrogich jeszcze znacznie zwiększyć elastyczność w ramach.  
  
 Deweloperzy często ma być dziedziczona z niezapieczętowane klasy tak, aby dodać członków jako udogodnienie, takie jak niestandardowe konstruktorów, nowych metod lub przeciążenia metody. Na przykład `System.Messaging.MessageQueue` jest niezapieczętowany, dlatego. Umożliwia ono użytkownikom tworzenie niestandardowych kolejek tej wartości domyślnej ścieżki określonej kolejki lub dodawanie metod niestandardowych, które upraszczają interfejs API dla konkretnych scenariuszy.  
  
 Klasy są niezapieczętowany domyślnie w językach programowania najbardziej i jest zalecana domyślna dla większości klas w struktur. Rozszerzalność udostępnianych przez niezapieczętowane typy jest znacznie zwiększyć przez użytkowników w ramach dość niedrogie zapewnienie ze względu na koszty stosunkowo niska testów związane z niezapieczętowane typy.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Pieczętowanie](../../../docs/standard/design-guidelines/sealing.md)
