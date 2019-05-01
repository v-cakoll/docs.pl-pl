---
title: Projektowanie pod kątem rozszerzalności
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: KrzysztofCwalina
ms.openlocfilehash: 94900dee72230a1b9d099d78168acc508af62af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026461"
---
# <a name="designing-for-extensibility"></a>Projektowanie pod kątem rozszerzalności
Ważnym aspektem projektowania struktury jest upewnienie się, że starannie przemyślane extensibility Framework. Wymaga to, że rozumiesz, koszty i korzyści związanych z różnych mechanizmów rozszerzalności. Ten rozdział pomaga w podjęciu decyzji, które mechanizmy rozszerzania — podklasy, zdarzenia, wirtualnych elementów członkowskich, wywołania zwrotne i tak dalej, mogą najlepiej spełnić wymagania dotyczące platformy.  
  
 Istnieje wiele sposobów, aby umożliwić rozszerzalność w struktur. One w zakresie od mniej zaawansowane, ale mniej kosztowne do bardzo zaawansowanych, ale kosztowne. Wszystkie wymagania danego rozszerzalności należy wybrać najtańsze mechanizm rozszerzalności, która spełnia wymagania. Należy pamiętać, że zazwyczaj można później dodać więcej rozszerzeń, ale użytkownik może nigdy nie zabrać ją bez wprowadzania istotnych zmian.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niezapieczętowane klasy](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Chronione elementy członkowskie](../../../docs/standard/design-guidelines/protected-members.md)  
 [Zdarzenia i wywołania zwrotne](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Wirtualne elementy członkowskie](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstrakcje (typy abstrakcyjne i interfejsy)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Klasy bazowe na potrzeby implementowania abstrakcji](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Pieczętowanie](../../../docs/standard/design-guidelines/sealing.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
