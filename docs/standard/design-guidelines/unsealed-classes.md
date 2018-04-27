---
title: Niezapieczętowanych klas
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c798c3cc93f08b77be7d0a5e0d1232d5598aed6b
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="unsealed-classes"></a>Niezapieczętowanych klas
Zapieczętowane klasy nie może być dziedziczona z i uniemożliwić ich rozszerzeń. Z kolei klasy, które mogą być dziedziczone z są nazywane niezapieczętowanych klas.  
  
 **ROZWAŻ ✓** przy użyciu niezapieczętowanych klas bez dodać wirtualnych lub chronionych elementów członkowskich, ponieważ doskonałym sposobem zapewnienia niedrogich jeszcze znacznie zwiększyć elastyczność w ramach.  
  
 Deweloperzy często ma być dziedziczona z klasy niezapieczętowany tak, aby dodawać członków wygody, takie jak niestandardowe konstruktorów, nowych metod lub przeciążenia metody. Na przykład `System.Messaging.MessageQueue` jest otwarty i w związku z tym umożliwia użytkownikom tworzenie niestandardowych kolejek domyślną wartość tego ścieżką określonej kolejki lub dodawanie metod niestandardowych, które upraszczają interfejsu API dla konkretnych scenariuszy.  
  
 Klasy niezapieczętowanego są domyślnie w językach programowania najbardziej i jest zalecane ustawienia domyślne dla większości klas struktury. Rozszerzalność zapewnianej przez typy niezapieczętowany jest znacznie zwiększyć przez użytkowników w ramach i dość niedrogich zapewnienie ze względu na małą testu kosztów związanych z niezapieczętowane typy.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Pieczętowanie](../../../docs/standard/design-guidelines/sealing.md)
