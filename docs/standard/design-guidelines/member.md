---
title: "Wytyczne dotyczące projektowania elementu członkowskiego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5df4ad5f6c947d8b3bf62c3bf7eb8426419e5f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="member-design-guidelines"></a>Wytyczne dotyczące projektowania elementu członkowskiego
Metody, właściwości, zdarzenia, konstruktorów i pól zbiorowo są określane jako elementy członkowskie. Elementy członkowskie są ostatecznie oznacza za pomocą którego funkcji framework jest narażony na użytkowników końcowych RAM.  
  
 Elementy Członkowskie mogą być statyczne wirtualnych lub niewirtualne, konkretnych lub abstrakcyjny, lub wystąpienia, a może mieć kilka różnych zakresów ułatwień dostępu. Takiej odmiany zapewnia wyrazistość wyjątkowo, ale w tym samym czasie wymaga opieki ze strony projektanta framework.  
  
 Ten rozdział zawiera podstawowe wskazówki, które należy wykonać podczas projektowania elementów członkowskich dowolnego typu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przeciążenie elementu członkowskiego](../../../docs/standard/design-guidelines/member-overloading.md)  
 [Właściwości projektu](../../../docs/standard/design-guidelines/property.md)  
 [Projekt — Konstruktor](../../../docs/standard/design-guidelines/constructor.md)  
 [Projekt zdarzeń](../../../docs/standard/design-guidelines/event.md)  
 [Pole projektu](../../../docs/standard/design-guidelines/field.md)  
 [Metody rozszerzenia](../../../docs/standard/design-guidelines/extension-methods.md)  
 [Przeciążenia operatorów](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [Parametr projektu](../../../docs/standard/design-guidelines/parameter-design.md)  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)
