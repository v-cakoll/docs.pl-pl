---
title: "Framework — zalecenia dotyczące projektowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 38c344e4f4ede58fcb39dd638f6aa8e896e63da0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="framework-design-guidelines"></a>Framework — zalecenia dotyczące projektowania
Ta sekcja zawiera wskazówki dotyczące projektowania biblioteki, w których rozszerzanie i interakcję z programu .NET Framework. Celem jest pomoc projektantów biblioteki zapewnienia spójności interfejsu API i łatwość użycia przez zapewnienie ujednolicony model programowania, który jest niezależny od języka programowania, używany do tworzenia aplikacji. Zaleca się przestrzegać następujących wytycznych projektowych, podczas tworzenia klasy i składników, które rozszerzają programu .NET Framework. Projekt biblioteki niespójne niekorzystnie wpływa na wydajność deweloperów i odradza przyjęcia.  
  
 Wytyczne dzielą się na prosty zalecenia prefiksem warunki `Do`, `Consider`, `Avoid`, i `Do not`. Te wytyczne mają ułatwić zrozumienie kompromis między różnymi rozwiązaniami projektantów biblioteki klasy. Mogą wystąpić sytuacje, w którym dobrej biblioteki projektu wymaga naruszanie ich tych zaleceń dotyczących projektowania. Takiej sytuacji należy rzadkich i jest ważne, czy masz przejrzyste i istotne Przyczyna decyzji.  
  
 Niniejsze wytyczne pochodzą z książki *Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2*, Krzysztof Cwalina i Abrams Brada.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Zawiera wskazówki dotyczące nazewnictwa zestawy, obszary nazw, typy i elementy członkowskie w bibliotekach klas.  
  
 [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
 Wskazówki dotyczące używania statycznych i abstrakcyjnej klasy, interfejsy, wyliczenia, struktur i innych typów.  
  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 Wskazówki dotyczące projektowania i przy użyciu właściwości, metody konstruktorów, pola, zdarzenia, Operatorzy i parametry.  
  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Rozszerzalność funkcjom, takim jak podklasy, za pomocą zdarzeń, wirtualne elementy członkowskie i wywołania zwrotne i opisano sposób wybierania mechanizmy, które najlepiej spełnia wymagania dotyczące sieci w ramach.  
  
 [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)  
 W tym artykule opisano wskazówek dotyczących projektowania, wyrzucanie i połowowe wyjątków.  
  
 [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 W tym artykule opisano wskazówki dotyczące przy użyciu popularne typy tablic, atrybuty i kolekcje, obsługi serializacji i przeładowanie operatorów równości.  
  
 [Często używane wzorce projektowe](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Zawiera wskazówki dotyczące wybierania i wdrażanie właściwości zależności i wzorzec dispose.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../../../docs/framework/get-started/overview.md)  
 [Plan dla środowiska .NET Framework](http://msdn.microsoft.com/en-us/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [Podręcznik programowania](../../../docs/framework/development-guide.md)
