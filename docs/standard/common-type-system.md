---
title: System typu wspólnego i specyfikacja Common Language Specification
description: Dowiedz się, jak System typu wspólnego (CTS) i Common Language Specification (CLS) umożliwiają programowi .NET o obsłudze wielu języków.
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: d162a736b8f7b56293fc75a445c2a80cce597768
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664515"
---
# <a name="common-type-system--common-language-specification"></a>System typu wspólnego i specyfikacja Common Language Specification

Ponownie dwa terminy swobodnie używane w środowisku .NET, faktycznie są niezwykle istotne, aby zrozumieć, jak implementacji .NET umożliwia tworzenie wielojęzycznych i zrozumienie jego sposobu działania.

## <a name="common-type-system"></a>System typu wspólnego

Zacząć od początku, należy pamiętać, że implementacja .NET jest _niezależny od języka_. Nie oznacza to, po prostu programistą można napisać jej kod w dowolnym języku, który może być kompilowane, aby IL. Oznacza to również potrzebuje można było korzystać z kodu napisanego w innych językach, które mogą być używane w implementacji .NET.

Aby to zrobić w sposób niewidoczny dla użytkownika, musi istnieć typowym sposobem opisano wszystkie obsługiwane typy. Jest to, co odpowiada za to System typu wspólnego (CTS). Został on utworzony, aby wykonać kilka czynności:

* Ustanów umożliwiająca wykonanie wielu języków.
* Zapewnia model obiektowy umożliwiają wdrażanie różnych języków na implementacji .NET.
* Zdefiniuj zestaw reguł, które należy wykonać we wszystkich językach, jeśli chodzi o pracy z typami.
* Podaj bibliotekę, która zawiera podstawowe typy pierwotne, które są używane podczas tworzenia aplikacji (takich jak `Boolean`, `Byte`, `Char` itp.)

CTS definiuje dwa główne rodzaje typów, które powinny być obsługiwane: typy odwołań i wartości. Ich nazwy wskazują ich definicje.

Typy odwołań obiekty są reprezentowane przez odniesienie do rzeczywistej wartości obiektu; w tym miejscu odwołanie jest podobne do wskaźnika w języku C/C++. Po prostu odwołuje się on w lokalizacji pamięci, w których wartości obiektów. To ma poważny wpływ na sposób te typy są używane. Przypisać typu odwołania do zmiennej, a następnie przekazać tej zmiennej do metody, na przykład zmiany wprowadzone w obiekcie będzie odzwierciedlona w głównym obiekcie; nie ma żadnych kopiowanie.

Typy wartości są i na odwrót, w których obiekty są reprezentowane przez ich wartości. Jeśli przypisujesz typ wartości do zmiennej, kopiowane są zasadniczo wartość obiektu.

CTS definiuje kilka kategorii typów, z których każdy z ich określonych semantyki i użycia:

* Klasy
* Struktury
* Wyliczenia
* Interfejsy
* Delegaty

CTS definiuje również inne właściwości typów, takich jak modyfikatorów dostępu, co to są elementami członkowskimi prawidłowego typu, jak dziedziczenie i przeciążenie działa i tak dalej. Niestety, przechodząc bardziej szczegółowo omówiono żadnego z tych wykracza poza zakres artykułu wprowadzające, takich jak to, ale można zapoznać się [więcej zasobów](#more-resources) sekcji na końcu łącza do bardziej szczegółowej zawartości, która obejmuje następujące tematy.

## <a name="common-language-specification"></a>Specyfikacja języka wspólnego

Aby włączyć pełne współdziałanie scenariuszy, wszystkie obiekty, które są tworzone w kodzie muszą polegać na pozycjami w językach, które są z ich używaniem (są ich _wywołujących_). Ponieważ istnieje wiele różnych języków, .NET została określona tych commonalities w coś, co jest nazywane **specyfikacja Common Language Specification** (CLS). Zgodny ze specyfikacją definiuje zestaw funkcji, które są wymagane przez wiele typowych aplikacji. Umożliwia także sortowania przepisem dla dowolnego języka, który jest wdrażany w oparciu .NET na to, czego potrzebuje do obsługi.

Zgodny ze specyfikacją jest podzbiorem CTS. Oznacza to, że wszystkie reguły w CTS dotyczą również ze specyfikacją CLS, o ile nie są bardziej rygorystyczne reguły zgodne ze specyfikacją. Jeśli składnik został utworzony przy użyciu tylko reguł w specyfikację CLS, oznacza to, udostępnia tylko funkcje ze specyfikacją CLS w jego interfejsie API, jest określany jako **zgodne ze specyfikacją CLS**. Na przykład `<framework-librares>` są zgodne ze specyfikacją CLS, dokładnie, ponieważ muszą wykonywać pracę we wszystkich językach, które są obsługiwane na platformie .NET.

Należy zapoznać się dokumenty w [więcej zasobów](#more-resources) sekcji poniżej, aby uzyskać przegląd wszystkich funkcji w specyfikację CLS.

## <a name="more-resources"></a>Inne zasoby

* [System typu wspólnego](./base-types/common-type-system.md)
* [Specyfikacja Common Language Specification](language-independence-and-language-independent-components.md)
