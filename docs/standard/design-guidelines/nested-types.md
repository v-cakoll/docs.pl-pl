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
ms.openlocfilehash: dd13116b13ac8e2d7a3af6ef014eb4f393909515
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743700"
---
# <a name="nested-types"></a>Zagnieżdżone typy
Typ zagnieżdżony jest typem zdefiniowanym w zakresie innego typu, który jest nazywany typem otaczającym. Typ zagnieżdżony ma dostęp do wszystkich elementów członkowskich jego typu otaczającego. Na przykład ma dostęp do prywatnych pól zdefiniowanych w typie otaczającym i do chronionych pól zdefiniowanych we wszystkich elementów nadrzędnych typu otaczającego.

 Ogólnie rzecz biorąc, zagnieżdżone typy powinny być używane oszczędnie. Istnieje kilka przyczyn tego. Niektórzy deweloperzy nie są w pełni zaznajomieni z koncepcją. Tacy deweloperzy mogą na przykład mieć problemy z składnią deklarowania zmiennych typów zagnieżdżonych. Zagnieżdżone typy są również bardzo ściśle sprzężone z ich otaczającymi typami i nie są odpowiednie do typów ogólnego przeznaczenia.

 Typy zagnieżdżone są najlepiej dopasowane do szczegółów implementacji modelowania ich typów otaczających. Użytkownik końcowy powinien rzadko musieli zadeklarować zmienne typu zagnieżdżonego i prawie nigdy nie powinien mieć jawnie utworzyć wystąpienia zagnieżdżonych typów. Na przykład moduł wyliczający kolekcji może być typem zagnieżdżonym tej kolekcji. Moduły wyliczające są zwykle tworzone przez ich typ otaczający, a ponieważ wiele języków obsługuje instrukcję foreach, zmienne modułu wyliczającego rzadko muszą być deklarowane przez użytkownika końcowego.

 ✔️ Używaj zagnieżdżonych typów, gdy relacja między typem zagnieżdżonym a jego zewnętrznym typem jest taka, że semantyka dostępności elementu członkowskiego jest pożądana.

 ❌ nie używać publicznych typów zagnieżdżonych jako konstrukcji grupowania logicznego; Użyj przestrzeni nazw dla tego programu.

 ❌ unikać publicznie uwidocznionych typów zagnieżdżonych. Jedynym wyjątkiem jest to, że zmienne typu zagnieżdżonego muszą być deklarowane tylko w rzadkich scenariuszach, takich jak podklasy lub inne zaawansowane scenariusze dostosowywania.

 ❌ nie używaj zagnieżdżonych typów, jeśli typ jest prawdopodobnie przywoływany poza typem zawierającym.

 Na przykład Wyliczenie przesłane do metody zdefiniowanej w klasie nie powinno być zdefiniowane jako typ zagnieżdżony w klasie.

 ❌ nie używaj zagnieżdżonych typów, jeśli muszą one być tworzone przez kod klienta.  Jeśli typ ma konstruktora publicznego, prawdopodobnie nie powinien być zagnieżdżony.

 Jeśli typ może być skonkretyzowany, który wydaje się wskazywać, że typ ma miejsce w strukturze na własny (można go utworzyć, działać z nim i zniszczyć bez użycia typu zewnętrznego) i dlatego nie powinien być zagnieżdżony. Typy wewnętrzne nie powinny być szeroko ponownie używane poza typem zewnętrznym bez żadnej relacji z typem zewnętrznym.

 ❌ nie definiują typu zagnieżdżonego jako elementu członkowskiego interfejsu. W wielu językach nie jest obsługiwana taka konstrukcja.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
