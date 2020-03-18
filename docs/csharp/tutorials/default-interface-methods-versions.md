---
title: 'Bezpieczne aktualizowanie interfejsów przy użyciu domyślnych metod interfejsu w języku C #'
description: W tym zaawansowanym samouczku opisano, jak bezpiecznie dodawać nowe możliwości do istniejących definicji interfejsu bez przerywania wszystkich klas i struktur implementujących ten interfejs.
ms.date: 05/06/2019
ms.technlogy: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: 650aea78b421783b3f249b3670578aa60e800ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156782"
---
# <a name="tutorial-update-interfaces-with-default-interface-methods-in-c-80"></a>Samouczek: Aktualizowanie interfejsów za pomocą domyślnych metod interfejsu w języku C# 8.0

Począwszy od języka C# 8.0 w platformie .NET Core 3.0, można zdefiniować implementację podczas deklarowania członka interfejsu. Najbardziej typowym scenariuszem jest bezpieczne dodawanie elementów członkowskich do interfejsu już zwolniony i używany przez niezliczonych klientów.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Bezpiecznie rozszerzaj interfejsy, dodając metody z implementacjami.
> * Tworzenie sparametryzowanych implementacji w celu zapewnienia większej elastyczności.
> * Włącz implementatorów, aby zapewnić bardziej szczegółową implementację w postaci zastąpienia.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilator C# 8.0. Kompilator C# 8.0 jest dostępny począwszy od [programu Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [sdk .NET Core 3.0](https://dotnet.microsoft.com/download).

## <a name="scenario-overview"></a>Omówienie scenariusza

Ten samouczek rozpoczyna się od wersji 1 biblioteki relacji z klientem. Możesz uzyskać aplikację startową na naszym [reppo próbek na GitHub](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship). Firma, która zbudowała tę bibliotekę, zamierzała, aby klienci z istniejącymi aplikacjami przyjęli swoją bibliotekę. Pod warunkiem minimalnych definicji interfejsu dla użytkowników ich biblioteki do zaimplementowania. Oto definicja interfejsu dla klienta:

[!code-csharp[InitialCustomerInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Zdefiniowali drugi interfejs, który reprezentuje kolejność:

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Z tych interfejsów zespół może utworzyć bibliotekę dla swoich użytkowników, aby stworzyć lepsze środowisko dla swoich klientów. Ich celem było stworzenie głębszych relacji z istniejącymi klientami i poprawa ich relacji z nowymi klientami.

Teraz nadszedł czas, aby uaktualnić bibliotekę do następnej wersji. Jedna z żądanych funkcji umożliwia rabat lojalnościowy dla klientów, którzy mają wiele zamówień. Ten nowy rabat lojalnościowy jest stosowany za każdym razem, gdy klient składa zamówienie. Określony rabat jest własnością każdego indywidualnego klienta. Każda implementacja `ICustomer` można ustawić różne reguły dla rabatu lojalnościowego.

Najbardziej naturalnym sposobem dodania tej funkcji `ICustomer` jest zwiększenie interfejsu za pomocą metody zastosowania dowolnego rabatu lojalnościowego. Ta sugestia projektowa wywołała niepokój wśród doświadczonych programistów: "Interfejsy są niezmienne po ich wydaniu! To przełomowa zmiana!" C# 8.0 dodaje *domyślne implementacje interfejsu* do uaktualniania interfejsów. Autorzy biblioteki można dodać nowe elementy członkowskie do interfejsu i zapewnić domyślną implementację dla tych elementów członkowskich.

Implementacje interfejsu domyślnego umożliwiają deweloperom uaktualnienie interfejsu, jednocześnie umożliwiając implementatorom zastąpienie tej implementacji. Użytkownicy biblioteki mogą akceptować domyślną implementację jako nieubijającą się zmianę. Jeśli ich reguły biznesowe są różne, mogą zastąpić.

## <a name="upgrade-with-default-interface-methods"></a>Uaktualnianie za pomocą domyślnych metod interfejsu

Zespół zgodził się na najbardziej prawdopodobną domyślną implementację: zniżkę lojalnościową dla klientów.

Uaktualnienie powinno zapewnić funkcjonalność, aby ustawić dwie właściwości: liczbę zamówień potrzebnych do zakwalifikowania się do rabatu i procent rabatu. To sprawia, że jest to idealny scenariusz dla domyślnych metod interfejsu. Można dodać metodę do `ICustomer` interfejsu i zapewnić najbardziej prawdopodobną implementację. Wszystkie istniejące i wszystkie nowe implementacje można użyć implementacji domyślnej lub podać własne.

Najpierw dodaj nową metodę do implementacji:

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

Autor biblioteki napisał pierwszy test, aby sprawdzić implementację:

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Należy zwrócić uwagę na następującą część badania:

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

To oddanych od `SampleCustomer` do `ICustomer` jest konieczne. Klasa `SampleCustomer` nie musi zapewniać implementacji `ComputeLoyaltyDiscount`dla ; który jest dostarczany `ICustomer` przez interfejs. Jednak `SampleCustomer` klasa nie dziedziczy członków z jego interfejsów. Ta zasada nie uległa zmianie. Aby wywołać dowolną metodę zadeklarowaną i zaimplementowaną w interfejsie, `ICustomer` zmienna musi być typem interfejsu, w tym przykładzie.

## <a name="provide-parameterization"></a>Podaj parametryzację

To dobry początek. Ale domyślna implementacja jest zbyt restrykcyjna. Wielu konsumentów tego systemu może wybrać różne progi dla liczby zakupów, inną długość członkostwa lub inną zniżkę procentową. Można zapewnić lepsze środowisko uaktualniania dla większej liczby klientów, zapewniając sposób, aby ustawić te parametry. Dodajmy metodę statyczną, która ustawia te trzy parametry kontrolujące domyślną implementację:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Istnieje wiele nowych funkcji języka pokazano w tym małym fragmentu kodu. Interfejsy mogą teraz zawierać elementy członkowskie statyczne, w tym pola i metody. Włączone są również różne modyfikatory dostępu. Dodatkowe pola są prywatne, nowa metoda jest publiczna. Wszystkie modyfikatory są dozwolone na elementy członkowskie interfejsu.

Aplikacje, które używają ogólnej formuły do obliczania rabatu lojalnościowego, ale różne parametry, nie muszą zapewniać implementacji niestandardowej; można ustawić argumenty za pomocą metody statycznej. Na przykład poniższy kod ustawia "uznanie klienta", które nagradza każdego klienta z więcej niż jednego miesiąca członkostwa:

[!code-csharp[SetLoyaltyThresholds](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Rozszerzanie implementacji domyślnej

Kod, który został dodany do tej pory dostarczył wygodną implementację dla tych scenariuszy, w których użytkownicy chcą coś w rodzaju domyślnej implementacji lub aby zapewnić niepowiązany zestaw reguł. W przypadku końcowej funkcji refaktoryzacji kodu nieco, aby włączyć scenariusze, w których użytkownicy mogą chcieć tworzyć na domyślnej implementacji.

Rozważmy startup, który chce przyciągnąć nowych klientów. Oferują one 50% zniżki na pierwsze zamówienie nowego klienta. W przeciwnym razie istniejący klienci otrzymują standardowy rabat. Autor biblioteki musi przenieść implementację `protected static` domyślną do metody, aby każda klasa implementująca ten interfejs mogła ponownie użyć kodu w swojej implementacji. Domyślna implementacja elementu członkowskiego interfejsu wywołuje tę metodę udostępnioną, jak również:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

W implementacji klasy, która implementuje ten interfejs, zastąpienie można wywołać metodę pomocnika statycznego i rozszerzyć tę logikę, aby zapewnić rabat "nowego klienta":

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Możesz zobaczyć cały gotowy kod w naszym [reppo przykładów na GitHub](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship). Możesz uzyskać aplikację startową na naszym [reppo próbek na GitHub](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship).

Te nowe funkcje oznaczają, że interfejsy mogą być aktualizowane bezpiecznie, gdy istnieje rozsądna domyślna implementacja dla tych nowych członków. Starannie projektuj interfejsy, aby wyrazić pojedyncze pomysły funkcjonalne, które mogą być implementowane przez wiele klas. Ułatwia to uaktualnienie tych definicji interfejsu, gdy zostaną wykryte nowe wymagania dla tego samego pomysłu funkcjonalnego.
