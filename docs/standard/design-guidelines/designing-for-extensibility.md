---
title: Projektowanie pod kątem rozszerzalności
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b643c33a1418839c8aabf06d681083232e61553a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="designing-for-extensibility"></a>Projektowanie pod kątem rozszerzalności
Ważnym aspektem Projektowanie struktury jest sprawdzanie, czy starannie przemyślane extensibility Framework. Wymaga to, że rozumiesz kosztów i korzyści związanych z różne mechanizmy rozszerzania. Ten rozdział pomaga w podjęciu decyzji, które mechanizmy rozszerzania — podklasy, zdarzenia wirtualne elementy członkowskie, wywołania zwrotne i tak dalej — mogą najlepiej spełnić wymagania Twojej platformy.  
  
 Istnieje wiele sposobów dozwolonych rozszerzalności w struktury. One należeć do zakresu od mniej wydajne, ale mniej kosztowne do bardzo zaawansowane, ale kosztowne. Wszystkie wymagania danego rozszerzalności należy wybrać najmniej kosztowne mechanizm rozszerzalności, która spełnia wymagania. Należy pamiętać, że jest zazwyczaj można później dodać więcej rozszerzeń, ale użytkownik może nigdy nie zabrać ją bez wprowadzania zmian, które psuły.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niezapieczętowane klasy](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Chronione elementy członkowskie](../../../docs/standard/design-guidelines/protected-members.md)  
 [Zdarzenia i wywołania zwrotne](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Wirtualne elementy członkowskie](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstrakcje (typy abstrakcyjne i interfejsy)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Klasy bazowe na potrzeby implementowania abstrakcji](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Pieczętowanie](../../../docs/standard/design-guidelines/sealing.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
