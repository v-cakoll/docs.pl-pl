---
title: Bezpiecznie aktualizować przy użyciu domyślnego interfejsu członków w interfejsachC#
description: Ta zaawansowana w tym samouczku przedstawiono sposób można bezpiecznie dodać nowe możliwości do istniejących definicji interfejsu bez przerywania wszystkich klas i struktur, które implementują ten interfejs.
ms.date: 05/06/2019
ms.custom: mvc
ms.openlocfilehash: 2daa40ead5902454c6d45390233e1491fe6d369b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877915"
---
# <a name="tutorial-update-interfaces-with-default-interface-members-in-c-80"></a>Samouczek: Zaktualizuj interfejsów przy użyciu domyślnego interfejsu członków w C# 8.0

Począwszy od C# 8.0 w programie .NET Core 3.0, można zdefiniować implementację przy deklarowaniu składową interfejsu. Najbardziej typowym scenariuszem jest bezpiecznie dodać elementy członkowskie do interfejsu już ogólnie dostępnych i używanych przez niezliczone klientów.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
> * Bezpiecznie Rozszerz interfejsów przez dodanie metod z implementacji.
> * Tworzenie sparametryzowanych implementacji, aby umożliwić większą elastyczność.
> * Włącz implementacji w celu zapewnienia bardziej szczegółowe implementacji w formie zastąpienia.

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować komputer do uruchamiania platformę .NET Core, w tym C# kompilatora 8.0 (wersja zapoznawcza). C# 8.0 kompilatora w wersji zapoznawczej jest dostępna, począwszy od [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), lub r [.NET Core 3.0 (wersja zapoznawcza) zestawu SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0). Domyślne elementy członkowskie z interfejsu są dostępne począwszy od programu .NET Core 3.0 w wersji zapoznawczej 4.

## <a name="scenario-overview"></a>Omówienie scenariusza

Ten samouczek rozpoczyna się od wersji 1 bibliotekę klienta relacji. Aplikacja startowa można uzyskać naszych [przykłady repozytorium w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship). Firmy, która wbudowana tę bibliotekę przeznaczone klienci z istniejącymi aplikacjami przyjęcie ich biblioteki. Definicje minimalny interfejs dla użytkowników w ich biblioteki, aby zaimplementować one udostępniane. Poniżej znajduje się definicja interfejsu dla klienta:

[!code-csharp[InitialCustomerInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Drugi interfejs, który reprezentuje kolejność one zdefiniowane:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Z tych interfejsów zespołu można utworzyć biblioteki dla swoich użytkowników tworzyć lepsze środowisko dla swoich klientów. Ich celem było utworzyć relację bardziej istniejących klientów i poprawy relacji między nimi przy użyciu nowych klientów.

Teraz nadszedł czas na uaktualnienie biblioteki dla następnej wersji. Jedna z pożądanych funkcji umożliwia rabat w wysokości lojalności dla użytkowników, którzy mają wiele zamówień. Ten nowy rabat lojalności stosowane zawsze, gdy klient tworzy zamówienie. Określony rabat jest właściwością poszczególnych klientów. Każda implementacja ICustomer można ustawić różne zasady dotyczące rabatowej lojalności. 

Jest to najbardziej naturalny sposób, aby dodać tę funkcjonalność udoskonalenie `ICustomer` interfejs za pomocą metody do stosowania rabatów lojalnościowych. Tę sugestię w projekt przyczyny dotyczą między doświadczonych deweloperów: "Interfejsy są niezmienne po po udostępnieniu! To jest istotną zmianę!" C#dodaje 8.0 *domyślne implementacje interfejsu* dla uaktualnienie interfejsów. Autorzy biblioteki można dodawać nowych członków do interfejsu i udostępnia domyślną implementację dla tych członków.

Implementacje interfejsu domyślne umożliwiają deweloperom uaktualnienie interfejsu, ograniczając wszelkie implementors przesłonić tę implementację. Użytkownicy biblioteki może zaakceptować domyślną implementację zmian niepowodujących niezgodności. Jeśli ich reguły biznesowe są różne, można zastąpić.

## <a name="upgrade-with-default-interface-members"></a>Uaktualnienie przy użyciu domyślnego składowych interfejsu

Zespół Zgadzam się na najbardziej prawdopodobne Domyślna implementacja: Rabat w wysokości lojalności klientów.

Uaktualnienia należy udostępniają funkcje, które można ustawić dwie właściwości: liczba zamówień potrzebne kwalifikował się do rabat i procent rabatu. Dzięki temu scenariusz doskonałe dla składowych interfejsu domyślnego. Możesz dodać metodę do interfejsu ICustomer i najprawdopodobniej implementacji. Wszystkich istniejących i wszelkich nowych implementacji można użyć w implementacji domyślnej, lub podaj swoje własne.

Najpierw dodaj nową metodę implementacji:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

Tworzenie biblioteki napisał pierwszy test, aby sprawdzić wdrożenia:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Zwróć uwagę, następujące części testu:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

Który rzutowanie z elementu `SampleCustomer` do `ICustomer` jest konieczne. `SampleCustomer` Klasy nie musi dostarczyć implementację `ComputeLoyaltyDiscount`; która jest dostarczona przez `ICustomer` interfejsu. Jednak `SampleCustomer` klasa nie dziedziczy członków z jego interfejsów. Tej reguły nie zmienił. Aby można było wywołać dowolną metodę zadeklarowana i zaimplementowane w interfejsie, zmienna musi być typu interfejsu, `ICustomer` w tym przykładzie.

## <a name="provide-parameterization"></a>Podaj parametryzacji

To dobry początek. Jednak w implementacji domyślnej jest zbyt restrykcyjne. Wielu klientów tego systemu mogą wybrać progi różnią się dla liczby zakupów, innej długości członkostwa lub inny procent rabatu. Możesz podać lepsze środowisko uaktualnienia większej liczby klientów, dzięki czemu można ustawić te parametry. Dodajmy statyczna metoda ustawia tych trzech parametrów, kontrolowanie domyślną implementację:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Istnieje wiele nowych możliwości języka przedstawione w tym fragmencie mały kod. Interfejsy mogą teraz zawierać statyczne elementy członkowskie, w tym pól i metod. Modyfikatory dostępu różnych również są włączone. Dodatkowe pola są prywatne, nowa metoda jest publiczny. Dowolny modyfikatorów są dozwolone w składowych interfejsu.

Aplikacje, które używają ogólny wzór dotyczących przeprowadzania obliczeń rabatu lojalności, ale różnych parametrów, trzeba podać implementacja niestandardowa; ustawiają argumenty za pośrednictwem metody statycznej. Na przykład poniższy kod ustawia "Ocena klienta", który nagradza każdego klienta z więcej niż jeden miesiąc członkostwa:

[!code-csharp[SetLoyaltyThresholds](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Rozszerzanie Domyślna implementacja

Kod, które zostały dodane do tej pory udostępnia wygodne implementacji dla tych scenariuszy, w której użytkownicy będą chcieli coś, np. Domyślna implementacja lub w celu udostępnienia niepowiązanych zbiór reguł. Dla funkcji powoduje końcowego umożliwia refaktoryzować kod nieco umożliwia scenariusze, w którym użytkownicy mogą chcieć tworzyć na domyślną implementację. 

Należy wziąć pod uwagę startowy, który chce przyciągnięcia nowych klientów. Oferują one 50% zniżki kolejność pierwszego nowego klienta. W przeciwnym razie istniejący klienci uzyskać rabat na wersję standard. Tworzenie biblioteki musi przenieść domyślną implementację do `protected static` metody, który każdy klasy implementującej interfejs ten można ponownie użyć kodu w ich realizacji. Domyślna implementacja elementu członkowskiego interfejsu wywołuje ten udostępnionej metody:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

W implementacji klasy, która implementuje ten interfejs zastępowania można wywołać metodę pomocnika statycznych i rozszerzyć tej logiki, aby zapewnić "nowego klienta" rabat w wysokości:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Widać cały kod zakończenia w naszym [przykłady repozytorium w serwisie GitHub] (aplikacja startowa można uzyskać naszych [przykłady repozytorium w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship).

Te nowe funkcje oznacza, że interfejsy mogą być aktualizowane bezpiecznie po uzasadnione Domyślna implementacja dla tych nowych członków. Dokładnie projektu interfejsach, express pojedynczego funkcjonalności pojęcia, które może być implementowana przez wiele klas. Ułatwia do uaktualnienia te definicje interfejsu, po odnalezieniu nowych wymagań dla tego samego idea funkcjonalności.
