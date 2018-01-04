---
title: "Zagnieżdżone typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 389ba73c4509f41f6c2cf86363e59ea720eb3c9f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="nested-types"></a>Zagnieżdżone typy
Zagnieżdżony typ jest typ zdefiniowany w zakresie innego typu, która jest wywoływana typu otaczającego. Zagnieżdżony typ ma dostęp do wszystkich elementów członkowskich jego typ otaczający. Na przykład ma dostęp do prywatnego pól zdefiniowane w typie otaczającym i chronione pola zdefiniowane w wszystkich nadrzędnych typu otaczającego.  
  
 Ogólnie rzecz biorąc zagnieżdżone typy powinny być używane rzadko. Istnieje kilka powodów. Niektórzy deweloperzy nie są w pełni zapoznać się z pojęciem. Te deweloperzy mogą na przykład wystąpić problemy z składni deklarowania zmiennych w zagnieżdżonych typów. Zagnieżdżone typy są również bardzo ściśle powiązane z ich typu otaczającego i jako takie nie są odpowiednie jako typów ogólnego przeznaczenia.  
  
 Zagnieżdżone typy są najbardziej odpowiednie dla modelowania szczegóły implementacji ich typu otaczającego. Użytkownik końcowy powinna rzadko muszą przeciążać Zadeklaruj zmienne typu zagnieżdżonego i prawie nigdy nie powinien mieć można jawnie utworzyć wystąpienia typów zagnieżdżonych. Na przykład moduł wyliczający kolekcji może być zagnieżdżony typ tej kolekcji. Moduły wyliczające wystąpienia są zazwyczaj tworzone przez ich typu otaczającego i ponieważ instrukcji foreach obsługuje wiele języków, zmienne modułu wyliczającego rzadko muszą być deklarowana przez użytkownika końcowego.  
  
 **CZY ✓** używać zagnieżdżonych typów w przypadku relacji między typu zagnieżdżonego i jej typu zewnętrznego taki sposób, że dostępność elementu członkowskiego semantyka pożądane.  
  
 **X nie** Użyj publicznego typów zagnieżdżonych jako logiczne grupowanie skonstruować; Użyj przestrzeni nazw dla tego.  
  
 **X należy UNIKAĆ** publicznie udostępnione typy zagnieżdżone. Jedynym wyjątkiem jest zmienne typu zagnieżdżonego muszą być deklarowane tylko w rzadkich scenariuszy, takich jak tworzenie podklas lub innych scenariuszy zaawansowanego dostosowania.  
  
 **X nie** Użyj zagnieżdżone typy, jeśli typ może odwoływać się poza typu zawierającego.  
  
 Na przykład wyliczenia przekazany do metody zdefiniowanej dla klasy, nie powinien być zdefiniowany jako typu zagnieżdżonego w klasie.  
  
 **X nie** używać zagnieżdżonych typów, jeśli muszą zostać utworzone przez kod klienta.  Jeśli typ ma konstruktora publicznego, prawdopodobnie nie powinien być zagnieżdżone.  
  
 Jeśli można utworzyć wystąpienia typu, który wydaje się, że wskazuje typ ma miejsce w ramach samodzielnie (można go utworzyć, z którą go, zniszczyć bez kiedykolwiek przy użyciu typu zewnętrznego) i dlatego nie powinny być zagnieżdżone. Typy wewnętrzne nie powinna być powszechnie używana poza typu zewnętrznego bez żadnej z relacji jakiejkolwiek do typu zewnętrznego.  
  
 **X nie** zagnieżdżony typ jako element członkowski interfejsu. Wiele języków nie obsługują takich konstrukcji.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
