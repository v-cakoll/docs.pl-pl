---
title: "Klasy podstawowe stosowania obiektów abstrakcyjnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 96264456ac6afc569c46caf5faed6c37ea22bc8e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="base-classes-for-implementing-abstractions"></a>Klasy podstawowe stosowania obiektów abstrakcyjnych
Mówiąc ściślej klasa staje się klasę podstawową, gdy inna klasa pochodzi od niego. Na potrzeby tej sekcji jednak klasa podstawowa jest przeznaczone głównie do zapewnienia wspólnej abstrakcji lub innych klas do ponownego użycia niektórych Domyślna implementacja jednak dziedziczenia klasy. Klasy podstawowe zwykle sit trakcie hierarchii dziedziczenia między abstrakcję elementu głównego hierarchii i kilka implementacji niestandardowych u dołu.  
  
 Służą one jako obiekty pomocnicze implementacji wykonywania obiektów abstrakcyjnych. Na przykład, jeden z obiektów abstrakcyjnych struktury uporządkowanej kolekcji elementów jest <xref:System.Collections.Generic.IList%601> interfejsu. Implementowanie <xref:System.Collections.Generic.IList%601> nie jest prosta, i w związku z tym Framework zapewnia kilka klas podstawowych, takich jak <xref:System.Collections.ObjectModel.Collection%601> i <xref:System.Collections.ObjectModel.KeyedCollection%602>, służące jako pomocników wykonywania kolekcje niestandardowe.  
  
 Klasy podstawowe zwykle nie są dostosowane do służyć jako obiekty abstrakcyjne samodzielnie, ponieważ mogą one zawierać zbyt wiele implementacji. Na przykład `Collection<T>` klasa podstawowa zawiera wiele implementacji związane z faktu, że implementuje nongeneric `IList` interfejsu (w celu lepszej integracji z kolekcjami nierodzajowe) i na fakt, że jest ona kolekcję elementów są przechowywane w pamięć w jednym z jego pól.  
  
 Jak już wspomniano klasy podstawowe zapewniają cenne pomocy dla użytkowników, którzy muszą implementować obiektów abstrakcyjnych, ale w tym samym czasie może być istotne odpowiedzialności. One Dodaj powierzchni i zwiększyć głębokość hierarchii dziedziczenia i dlatego koncepcyjnie skomplikować platformę. W związku z tym klas podstawowej należy używać tylko wtedy, gdy zawierają wartość użytkownikom platformy. Jeśli zawierają wartość tylko do obiektów implementujących RAM, w którym wielkość delegowania do wewnętrznej implementacji zamiast dziedziczenia z klasy podstawowej należy uznać należy unikać ich.  
  
 **ROZWAŻ ✓** wprowadzania base klasy abstrakcyjny, nawet jeśli nie zawierają żadnych abstrakcyjne elementy członkowskie. To wyraźnie komunikuje się dla użytkowników, że klasa jest przeznaczona wyłącznie do być dziedziczone z.  
  
 **ROZWAŻ ✓** umieszczenie w oddzielnych nazw typów połączeniach scenariusz klas podstawowych. Zgodnie z definicją klasy podstawowe są przeznaczone do rozszerzalności zaawansowanych scenariuszy i w związku z tym nie są interesujące większości użytkowników.  
  
 **X należy UNIKAĆ** nazw klas podstawowych z sufiksem "Podstawowy", jeśli klasa jest przeznaczona do użycia w publicznych interfejsach API.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
