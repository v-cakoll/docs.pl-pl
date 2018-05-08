---
title: Wspólny System typów & Specyfikacja języka wspólnego
description: Dowiedz się, jak System typu wspólnego (CTS) i specyfikacja języka wspólnego (CLS) umożliwiają .NET do obsługi wielu języków.
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: 992f70cc7c2e55a0a2cfd08e08a3a9f16aad8c8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="common-type-system--common-language-specification"></a>Wspólny System typów & Specyfikacja języka wspólnego

Ponownie dwa warunki, za darmo używanych w środowisku .NET faktycznie są niezwykle istotne, aby zrozumieć, jak implementacja .NET umożliwia wielu języków programowania i zrozumieć, jak to działa.

## <a name="common-type-system"></a>System typu wspólnego

Zacząć od początku, należy pamiętać, że implementacja .NET jest _niezależny od języka_. To nie tylko oznacza, że programista może zapisywać jej kod w dowolnym języku, który może zostać skompilowany w IL. Oznacza to również, że użytkownik musi mieć możliwość interakcji z kodu napisanego w innych językach, które mogą być używane w implementacji programu .NET.

Aby to zrobić w sposób niewidoczny dla użytkownika, musi istnieć typowym sposobem opisano wszystkie obsługiwane typy. Jest to System typu wspólnego (CTS) jest odpowiedzialnym za operacje. Wprowadzono w celu wykonać kilka czynności:

*   Ustanów framework wykonywanie wielu języków.
*   Podaj zorientowany obiektowo model do obsługi wykonania różnych języków na implementacji programu .NET.
*   Zdefiniuj zestaw reguł, które należy wykonać we wszystkich językach, po przejściu do pracy z typami.
*   Podaj biblioteki, który zawiera podstawowe typy pierwotne, które są używane w aplikacjach (takich jak `Boolean`, `Byte`, `Char` itp.)

CTS definiuje dwa główne rodzaje typów, które powinny być obsługiwane: typów referencyjnych i wartość. Nazwy wskazują ich definicje.

Typy odwołań obiektów są reprezentowane przez odwołanie, do rzeczywistych wartości obiektu; w tym miejscu odwołanie jest podobne do wskaźnika w języku C/C++. Po prostu odnosi się do lokalizacji pamięci, których wartości obiektów. To ma poważny wpływ na korzystania z tych typów. Jeśli można przypisać typu odwołania do zmiennej, a następnie przekazać tej zmiennej do metody, na przykład zostaną odzwierciedlone wszystkie zmiany do obiektu w obiekcie głównym; nie ma żadnych kopiowania.

Typy wartości są przeciwieństwem, których obiekty są reprezentowane przez ich wartości. Po przypisaniu typu wartości do zmiennej, kopiowane są zasadniczo wartość obiektu.

CTS definiuje kilka kategorii z określonych semantykę i użycie typów:

*   Klasy
*   Struktury
*   Wyliczenia
*   Interfejsy
*   Delegaty

CTS definiuje również inne właściwości z typów, takie jak modyfikatory dostępu, co należą do prawidłowego typu, jak dziedziczenia i przeciążeniu działania i tak dalej. Niestety, przechodząc bezpośrednich do dowolnego z tych wykracza poza zakres wprowadzające artykułu, takich jak ta, ale należy zapoznać się [więcej zasobów](#more-resources) sekcji na końcu łącza do dodatkowej zawartości szczegółowych, który obejmuje następujące tematy.

## <a name="common-language-specification"></a>Specyfikacja języka wspólnego

Aby włączyć pełne współdziałanie scenariuszy, wszystkie obiekty, które są tworzone w kodzie muszą polegać na wspólne właściwości w językach, które wykorzystują je (są ich _wywołań_). Ponieważ istnieje wiele różnych języków, .NET została określona tych commonalities w coś o nazwie **specyfikacja języka wspólnego** (ze specyfikacją CLS). Ze specyfikacją CLS definiuje zestaw funkcji, które są wymagane przez wiele typowych zastosowań. Umożliwia także sortowania przepisu dla dowolnego języka, który jest wdrażany w oparciu o .NET na potrzebne do obsługi.

Ze specyfikacją CLS jest podzbiorem CTS. Oznacza to, że wszystkie reguły w CTS dotyczą również ze specyfikacją CLS, chyba że ściślejsze zasady ze specyfikacją CLS. Jeśli składnik jest zbudowany przy użyciu tylko reguł w ze specyfikacją CLS, oznacza to, eksponuje jego interfejsu API tylko funkcje ze specyfikacją CLS, jest określany jako **zgodne ze specyfikacją CLS**. Na przykład `<framework-librares>` są zgodne ze specyfikacją CLS, mówiąc, ponieważ muszą działać we wszystkich językach, które są obsługiwane na platformie .NET.

Należy zapoznać się z dokumentami w [więcej zasobów](#more-resources) poniżej, aby uzyskać przegląd wszystkich funkcji w ze specyfikacją CLS.

## <a name="more-resources"></a>Więcej zasobów

*   [System typu wspólnego](./base-types/common-type-system.md)
*   [Specyfikacja języka wspólnego](language-independence-and-language-independent-components.md)
