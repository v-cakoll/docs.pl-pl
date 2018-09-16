---
title: Klasy bazowe na potrzeby implementowania abstrakcji
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f326ee895251678c7a23ea84a11e83951edf2cc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677074"
---
# <a name="base-classes-for-implementing-abstractions"></a>Klasy bazowe na potrzeby implementowania abstrakcji
Ściśle rzecz ujmując klasę staje się klasę bazową, gdy inna klasa pochodzi od niego. Na potrzeby tej sekcji jednak klasa bazowa jest przeznaczona głównie w celu przesłania wspólnej abstrakcji, lub dla innych klas ponownie użyć niektórych Domyślna implementacja jednak dziedziczenia klasy. Klasy bazowe znajdują się zwykle w środku hierarchii dziedziczenia między klasą abstrakcyjną w katalogu głównym hierarchii i kilka niestandardowych implementacji u dołu.  
  
 Służą one jako obiekty pomocnicze implementacji potrzeby implementowania abstrakcji. Na przykład jeden abstrakcje struktury uporządkowanej kolekcji elementów jest <xref:System.Collections.Generic.IList%601> interfejsu. Implementowanie <xref:System.Collections.Generic.IList%601> nie jest proste, i dlatego struktura zapewnia kilka klas podstawowych, takich jak <xref:System.Collections.ObjectModel.Collection%601> i <xref:System.Collections.ObjectModel.KeyedCollection%602>, które służą jako obiekty pomocnicze dotyczące implementowania kolekcje niestandardowe.  
  
 Klasy bazowe zwykle nie są odpowiednie, która będzie służyć jako elementy abstrakcji samodzielnie, ponieważ jest on zwykle zawiera zbyt wiele implementacji. Na przykład `Collection<T>` klasa bazowa zawiera wiele implementacji związane z faktu, że implementuje nongeneric `IList` interfejs (w celu lepszej integracji z kolekcjami nierodzajowymi) i na fakt, że jest to zbiór elementów przechowywanych w pamięć w jednym z jej pól.  
  
 Jak już wspomniano klasy bazowe może zapewnić bezcenne pomocy dla użytkowników, którzy muszą implementować abstrakcje, ale w tym samym czasie może być istotne odpowiedzialności. Oni dodawać obszaru powierzchni i zwiększyć głębokość hierarchii dziedziczenia i dlatego koncepcyjnie skomplikować platformę. W związku z tym klasy bazowe powinna służyć tylko wtedy, gdy zapewniają dużą wartość dla użytkowników w ramach. Jeśli zapewniają wartość tylko do implementacji RAM, w którym wielkość delegowania do wdrożenia wewnętrznego, zamiast dziedziczenia z klasy bazowej należy uznać należy unikać ich.  
  
 **✓ CONSIDER** wprowadzania base klasy abstrakcyjny, nawet jeśli nie zawierają żadnych abstrakcyjne elementy członkowskie. To wyraźnie komunikuje się użytkownikom przeznaczoną wyłącznie do być dziedziczone z klasy.  
  
 **✓ CONSIDER** umieszczenie w oddzielnych nazw typów połączeniach scenariusz klas podstawowych. Zgodnie z definicją klasy bazowe są przeznaczone dla scenariuszy zaawansowanych rozszerzeń i w związku z tym nie są interesujące dla większości użytkowników.  
  
 **X AVOID** nazw klas podstawowych z sufiksem "Podstawowy", jeśli klasa jest przeznaczona do użycia w publicznych interfejsach API.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
