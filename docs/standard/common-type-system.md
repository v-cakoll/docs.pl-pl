---
title: System typu wspólnego i specyfikacja języka wspólnego
description: Dowiedz się, jak system wspólnych typów (CTS) i specyfikacja języka wspólnego (CLS) umożliwiają programowi .NET obsługę wielu języków.
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: 8983e456b051ace434fda9f6ed9cf9028c2ec2d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187676"
---
# <a name="common-type-system--common-language-specification"></a>System typu wspólnego i specyfikacja języka wspólnego

Ponownie dwa terminy, które są swobodnie używane w świecie .NET, są one rzeczywiście kluczowe, aby zrozumieć, jak implementacja .NET umożliwia tworzenie wielu języków i zrozumieć, jak to działa.

## <a name="common-type-system"></a>System typu wspólnego

Aby rozpocząć od początku, należy pamiętać, że implementacja .NET jest _agnostyk języka_. Nie oznacza to tylko, że programista może napisać swój kod w dowolnym języku, który można skompilować do IL. Oznacza to również, że muszą być w stanie wchodzić w interakcje z kodem napisanym w innych językach, które mogą być używane w implementacji .NET.

Aby to zrobić w sposób przejrzysty, musi istnieć wspólny sposób opisywania wszystkich obsługiwanych typów. To jest to, co wspólny system typu (CTS) jest odpowiedzialny za to, co robi. Został on stworzony, aby zrobić kilka rzeczy:

* Ustanowienie struktury dla wykonywania w wielu językach.
* Podaj model obiektowy do obsługi implementacji różnych języków w implementacji .NET.
* Zdefiniuj zestaw reguł, których muszą przestrzegać wszystkie języki, jeśli chodzi o pracę z typami.
* Podaj bibliotekę zawierającą podstawowe typy pierwotne, które są `Boolean`używane `Byte` `Char` w tworzeniu aplikacji (takie jak , , itp.)

CTS definiuje dwa główne typy typów, które powinny być obsługiwane: typy odwołań i wartości. Ich nazwy wskazują na ich definicje.

Obiekty typów odwołań są reprezentowane przez odwołanie do rzeczywistej wartości obiektu; odwołanie w tym miejscu jest podobny do wskaźnika w C/C++. Po prostu odnosi się do lokalizacji pamięci, w której znajdują się wartości obiektów. Ma to ogromny wpływ na sposób korzystania z tych typów. Jeśli przypiszesz typ odwołania do zmiennej, a następnie przekażesz tę zmienną do metody, na przykład wszelkie zmiany w obiekcie zostaną odzwierciedlone w obiekcie głównym; nie ma kopiowania.

Typy wartości są odwrotne, gdzie obiekty są reprezentowane przez ich wartości. Jeśli typ wartości zostanie przypisany do zmiennej, zasadniczo kopiujesz wartość obiektu.

CTS definiuje kilka kategorii typów, z których każda ma specyficzną semantyką i zastosowanie:

* Klasy
* Struktury
* Wyliczenia
* Interfejsy
* Delegaty

CTS definiuje również wszystkie inne właściwości typów, takich jak modyfikatory dostępu, jakie są prawidłowe elementy członkowskie typu, jak dziedziczenie i przeciążenie działa i tak dalej. Niestety, wchodzenie w głąb któregokolwiek z nich wykracza poza zakres artykułu wprowadzającego, takiego jak ten, ale możesz zapoznać się z sekcją [Więcej zasobów](#more-resources) na końcu, aby uzyskać linki do bardziej szczegółowej zawartości obejmującej te tematy.

## <a name="common-language-specification"></a>Specyfikacja języka wspólnego

Aby włączyć pełne scenariusze współdziałania, wszystkie obiekty, które są tworzone w kodzie musi polegać na pewne wspólności w językach, które zużywają je (są ich _obiekty wywołujące)._ Ponieważ istnieje wiele różnych języków, .NET określił te podobieństwa w coś o nazwie **specyfikacji języka wspólnego** (CLS). CLS definiuje zestaw funkcji, które są potrzebne przez wiele typowych aplikacji. Zapewnia również rodzaj przepisu dla dowolnego języka, który jest implementowany na wierzchu .NET na co musi obsługiwać.

CLS jest podzbiorem CTS. Oznacza to, że wszystkie reguły w CTS mają również zastosowanie do CLS, chyba że reguły CLS są bardziej rygorystyczne. Jeśli składnik jest zbudowany przy użyciu tylko reguł w CLS, oznacza to, że udostępnia tylko funkcje CLS w swoim interfejsie API, mówi się, że **jest zgodny ze specyfikacją CLS**. Na przykład `<framework-librares>` są zgodne ze specyfikacją CLS właśnie dlatego, że muszą pracować we wszystkich językach, które są obsługiwane w .NET.

Możesz zapoznać się z dokumentami w sekcji [Więcej zasobów](#more-resources) poniżej, aby uzyskać przegląd wszystkich funkcji w cls.

## <a name="more-resources"></a>Więcej zasobów

* [System typu wspólnego](./base-types/common-type-system.md)
* [Specyfikacja języka wspólnego](language-independence-and-language-independent-components.md)
