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
ms.openlocfilehash: 3467851aa767efcd0557e8a412cd36316a48b9b0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709156"
---
# <a name="nested-types"></a>Zagnieżdżone typy
Typ zagnieżdżony jest typem zdefiniowanym w zakresie innego typu, który jest nazywany typem otaczającym. Typ zagnieżdżony ma dostęp do wszystkich elementów członkowskich jego typu otaczającego. Na przykład ma dostęp do prywatnych pól zdefiniowanych w typie otaczającym i do chronionych pól zdefiniowanych we wszystkich elementów nadrzędnych typu otaczającego.  
  
 Ogólnie rzecz biorąc, zagnieżdżone typy powinny być używane oszczędnie. Istnieje kilka przyczyn tego. Niektórzy deweloperzy nie są w pełni zaznajomieni z koncepcją. Tacy deweloperzy mogą na przykład mieć problemy z składnią deklarowania zmiennych typów zagnieżdżonych. Zagnieżdżone typy są również bardzo ściśle sprzężone z ich otaczającymi typami i nie są odpowiednie do typów ogólnego przeznaczenia.  
  
 Typy zagnieżdżone są najlepiej dopasowane do szczegółów implementacji modelowania ich typów otaczających. Użytkownik końcowy powinien rzadko musieli zadeklarować zmienne typu zagnieżdżonego i prawie nigdy nie powinien mieć jawnie utworzyć wystąpienia zagnieżdżonych typów. Na przykład moduł wyliczający kolekcji może być typem zagnieżdżonym tej kolekcji. Moduły wyliczające są zwykle tworzone przez ich typ otaczający, a ponieważ wiele języków obsługuje instrukcję foreach, zmienne modułu wyliczającego rzadko muszą być deklarowane przez użytkownika końcowego.  
  
 **✓ DO** używać zagnieżdżonych typów w przypadku relacji między typu zagnieżdżonego i jej typu zewnętrznego taki sposób, że dostępność elementu członkowskiego semantyka pożądane.  
  
 **X DO NOT** Użyj publicznego typów zagnieżdżonych jako logiczne grupowanie skonstruować; Użyj przestrzeni nazw dla tego.  
  
 **X AVOID** publicznie udostępnione typy zagnieżdżone. Jedynym wyjątkiem jest to, że zmienne typu zagnieżdżonego muszą być deklarowane tylko w rzadkich scenariuszach, takich jak podklasy lub inne zaawansowane scenariusze dostosowywania.  
  
 **X DO NOT** Użyj zagnieżdżone typy, jeśli typ może odwoływać się poza typu zawierającego.  
  
 Na przykład Wyliczenie przesłane do metody zdefiniowanej w klasie nie powinno być zdefiniowane jako typ zagnieżdżony w klasie.  
  
 **X DO NOT** używać zagnieżdżonych typów, jeśli muszą zostać utworzone przez kod klienta.  Jeśli typ ma konstruktora publicznego, prawdopodobnie nie powinien być zagnieżdżony.  
  
 Jeśli typ może być skonkretyzowany, który wydaje się wskazywać, że typ ma miejsce w strukturze na własny (można go utworzyć, działać z nim i zniszczyć bez użycia typu zewnętrznego) i dlatego nie powinien być zagnieżdżony. Typy wewnętrzne nie powinny być szeroko ponownie używane poza typem zewnętrznym bez żadnej relacji z typem zewnętrznym.  
  
 **X DO NOT** zagnieżdżony typ jako element członkowski interfejsu. W wielu językach nie jest obsługiwana taka konstrukcja.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
