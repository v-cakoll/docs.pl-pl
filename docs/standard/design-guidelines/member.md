---
title: Wytyczne dotyczące projektowania elementu członkowskiego
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f4e33735a934b1ac41c34ccb9698c172ada28e1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="member-design-guidelines"></a>Wytyczne dotyczące projektowania elementu członkowskiego
Metody, właściwości, zdarzenia, konstruktorów i pól zbiorowo są określane jako elementy członkowskie. Elementy członkowskie są ostatecznie oznacza za pomocą którego funkcji framework jest narażony na użytkowników końcowych RAM.  
  
 Elementy Członkowskie mogą być statyczne wirtualnych lub niewirtualne, konkretnych lub abstrakcyjny, lub wystąpienia, a może mieć kilka różnych zakresów ułatwień dostępu. Takiej odmiany zapewnia wyrazistość wyjątkowo, ale w tym samym czasie wymaga opieki ze strony projektanta framework.  
  
 Ten rozdział zawiera podstawowe wskazówki, które należy wykonać podczas projektowania elementów członkowskich dowolnego typu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przeciążanie elementu członkowskiego](../../../docs/standard/design-guidelines/member-overloading.md)  
 [Projekt właściwości](../../../docs/standard/design-guidelines/property.md)  
 [Projekt konstruktora](../../../docs/standard/design-guidelines/constructor.md)  
 [Projekt zdarzenia](../../../docs/standard/design-guidelines/event.md)  
 [Projekt pola](../../../docs/standard/design-guidelines/field.md)  
 [Metody rozszerzeń](../../../docs/standard/design-guidelines/extension-methods.md)  
 [Przeciążenia operatorów](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [Projekt parametrów](../../../docs/standard/design-guidelines/parameter-design.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
