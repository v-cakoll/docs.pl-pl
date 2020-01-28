---
title: Projekt pola
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: c00929ca499e39bd4e24d482c9413beb9cccddc1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741606"
---
# <a name="field-design"></a>Projekt pola
Zasada hermetyzacji jest jednym z najważniejszych koncepcji w projekcie zorientowanym na obiekty. Ta zasada Określa, że dane przechowywane wewnątrz obiektu powinny być dostępne tylko dla tego obiektu.

 Przydatnym sposobem interpretacji zasady jest to, że typ powinien zostać zaprojektowany tak, aby zmiany w polach tego typu (zmiany nazwy lub typu) mogły zostać wykonane bez przerywania kodu innego niż dla elementów członkowskich typu. Ta interpretacja natychmiast oznacza, że wszystkie pola muszą być prywatne.

 Wykluczamy stałe i statyczne pola tylko do odczytu z tego rygorystycznego ograniczenia, ponieważ takie pola, prawie według definicji, nigdy nie są wymagane do zmiany.

 ❌ nie zapewniają publicznych lub chronionych pól wystąpień.

 Należy podać właściwości dostępu do pól zamiast udostępniać je publicznie lub chronionym.

 ✔️ Użyj pól stałych dla stałych, które nigdy nie ulegną zmianie.

 Kompilator pali wartości pól const bezpośrednio w kodzie wywołującym. W związku z tym nie można zmienić wartości stałych bez ryzyka naruszenia zgodności.

 ✔️ używać publicznych statycznych pól `readonly` dla wstępnie zdefiniowanych wystąpień obiektów.

 Jeśli istnieją wstępnie zdefiniowane wystąpienia typu, zadeklaruj je jako publiczne pola statyczne tylko do odczytu samego typu.

 ❌ nie przypisuj wystąpień modyfikowalnych typów do pól `readonly`.

 Typ modyfikowalny jest typem z wystąpieniami, które można zmodyfikować po utworzeniu wystąpienia. Na przykład tablice, większość kolekcji i strumienie są modyfikowalnymi typami, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>i <xref:System.String?displayProperty=nameWithType> są bardzo niezmienne. Modyfikator tylko do odczytu w polu Typ odwołania zapobiega zastąpieniu wystąpienia w polu, ale nie zapobiega modyfikowaniu danych wystąpienia pola przez wywoływanie elementów członkowskich, które zmieniają wystąpienie.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
