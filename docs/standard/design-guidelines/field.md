---
title: Projekt pola
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 3a5ae985ab161899fbb5e96f9b0ef0cfa90b957c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289749"
---
# <a name="field-design"></a>Projekt pola
Zasada hermetyzacji jest jednym z najważniejszych koncepcji w projekcie zorientowanym na obiekty. Ta zasada Określa, że dane przechowywane wewnątrz obiektu powinny być dostępne tylko dla tego obiektu.

 Przydatnym sposobem interpretacji zasady jest to, że typ powinien zostać zaprojektowany tak, aby zmiany w polach tego typu (zmiany nazwy lub typu) mogły zostać wykonane bez przerywania kodu innego niż dla elementów członkowskich typu. Ta interpretacja natychmiast oznacza, że wszystkie pola muszą być prywatne.

 Wykluczamy stałe i statyczne pola tylko do odczytu z tego rygorystycznego ograniczenia, ponieważ takie pola, prawie według definicji, nigdy nie są wymagane do zmiany.

 ❌Nie udostępniaj publicznych lub chronionych pól wystąpień.

 Należy podać właściwości dostępu do pól zamiast udostępniać je publicznie lub chronionym.

 ✔️ Użyj pól stałych dla stałych, które nigdy nie ulegną zmianie.

 Kompilator pali wartości pól const bezpośrednio w kodzie wywołującym. W związku z tym nie można zmienić wartości stałych bez ryzyka naruszenia zgodności.

 ✔️ używać publicznych pól statycznych `readonly` dla wstępnie zdefiniowanych wystąpień obiektów.

 Jeśli istnieją wstępnie zdefiniowane wystąpienia typu, zadeklaruj je jako publiczne pola statyczne tylko do odczytu samego typu.

 ❌Nie przypisuj wystąpień modyfikowalnych typów do `readonly` pól.

 Typ modyfikowalny jest typem z wystąpieniami, które można zmodyfikować po utworzeniu wystąpienia. Na przykład tablice, większość kolekcji i strumienie są modyfikowalnymi typami, ale <xref:System.Int32?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> i <xref:System.String?displayProperty=nameWithType> są zmienne. Modyfikator tylko do odczytu w polu Typ odwołania zapobiega zastąpieniu wystąpienia w polu, ale nie zapobiega modyfikowaniu danych wystąpienia pola przez wywoływanie elementów członkowskich, które zmieniają wystąpienie.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania elementów członkowskich](member.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
