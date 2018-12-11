---
title: Zagnieżdżone typy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
author: KrzysztofCwalina
ms.openlocfilehash: 7e5fe66106ad34e88bbf435794a08a159c045b02
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148879"
---
# <a name="nested-types"></a>Zagnieżdżone typy
Typ zagnieżdżony jest typ zdefiniowany w zakresie innego typu, która jest wywoływana typ otaczający. Zagnieżdżony typ ma dostęp do wszystkich elementów członkowskich w jego typie otaczającym. Na przykład ma dostęp do prywatnych pól zdefiniowanych w typie otaczającym i chronione pól zdefiniowanych w wszystkich nadrzędnych typu otaczającego.  
  
 Ogólnie rzecz biorąc zagnieżdżone typy powinny być używane rzadko. Istnieje kilka przyczyn. Niektórzy deweloperzy nie są w pełni zapoznać się z pojęciem. Tych deweloperów na przykład, Niewykluczone, problemy ze składnią zadeklarowania zmiennych typów zagnieżdżonych. Zagnieżdżone typy są również bardzo ściśle powiązane z ich typ otaczający i jako takie nie są odpowiednie, jako typów ogólnego przeznaczenia.  
  
 Zagnieżdżone typy są dopasowane do modelowania szczegóły implementacji ich typ otaczający. Użytkownik końcowy rzadko powinni być zmuszeni do deklarowania zmiennych typu zagnieżdżonego oraz prawie nigdy nie powinny mieć jawnie utworzyć typy zagnieżdżone. Na przykład moduł wyliczający kolekcji może być zagnieżdżony typ tej kolekcji. Moduły wyliczające są zwykle tworzone przez ich typ otaczający. Ponadto ponieważ wiele języków obsługują instrukcji foreach, zmiennych modułu wyliczającego rzadko muszą być zgłaszane przez użytkownika końcowego.  
  
 **✓ DO** używać zagnieżdżonych typów w przypadku relacji między typu zagnieżdżonego i jej typu zewnętrznego taki sposób, że dostępność elementu członkowskiego semantyka pożądane.  
  
 **X DO NOT** Użyj publicznego typów zagnieżdżonych jako logiczne grupowanie skonstruować; Użyj przestrzeni nazw dla tego.  
  
 **X AVOID** publicznie udostępnione typy zagnieżdżone. Jedynym wyjątkiem jest, jeśli zmienne typu zagnieżdżonego musi być zadeklarowany tylko w rzadkich scenariuszach, takich jak tworzenie podklasy lub innych scenariuszy zaawansowanych dostosowań.  
  
 **X DO NOT** Użyj zagnieżdżone typy, jeśli typ może odwoływać się poza typu zawierającego.  
  
 Na przykład wyliczenia przekazany do metody zdefiniowanej w klasie nie powinien być zdefiniowany jako typ zagnieżdżony w klasie.  
  
 **X DO NOT** używać zagnieżdżonych typów, jeśli muszą zostać utworzone przez kod klienta.  Jeśli typ ma on publicznego konstruktora, prawdopodobnie nie powinny być zagnieżdżone.  
  
 Jeśli można utworzyć wystąpienia typu, który wydaje się, że wskazuje typ ma miejsce w ramach samodzielnie (możesz można go utworzyć, pracować z nim i zniszczyć bez kiedykolwiek przy użyciu typu zewnętrznego), a zatem nie powinien być zagnieżdżone. Typy wewnętrzne nie powinna być powszechnie używana poza typu zewnętrznego bez żadnych relacji jakiejkolwiek do typu zewnętrznego.  
  
 **X DO NOT** zagnieżdżony typ jako element członkowski interfejsu. Wiele języków nie obsługują takich konstrukcji.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
