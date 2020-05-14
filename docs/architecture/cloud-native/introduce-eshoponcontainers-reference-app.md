---
title: Wprowadzenie do aplikacji referencyjnej eShopOnContainers
description: Wprowadzenie do aplikacji referencyjnej dla mikrousług eShopOnContainers Cloud Native dla ASP.NET Core i platformy Azure.
ms.date: 06/30/2019
ms.openlocfilehash: b97b62268db1d9990f762d9769233ad72551c226
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395397"
---
# <a name="introducing-eshoponcontainers-reference-app"></a>Wprowadzenie do aplikacji referencyjnej eShopOnContainers

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Firma Microsoft, w partnerstwie z wiodącymi ekspertami społecznościowymi, produkowała w pełni funkcjonalne, natywne aplikacje mikrousług, eShopOnContainers. Ta aplikacja jest zbudowana do pokazania przy użyciu platformy .NET Core i platformy Docker oraz opcjonalnie platform Azure, Kubernetes i Visual Studio, aby utworzyć sklep online.

![Zrzut ekranu przykładowej aplikacji eShopOnContainers.](./media/eshoponcontainers-sample-app-screenshot.png)

**Rysunek 2-1**. Zrzut ekranu przykładowej aplikacji eShopOnContainers.

Przed rozpoczęciem tego rozdziału zalecamy pobranie [aplikacji referencyjnej eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers). Jeśli tak zrobisz, powinno być łatwiejsze do obserwowania wraz z przedstawionymi informacjami.

## <a name="features-and-requirements"></a>Funkcje i wymagania

Zacznijmy od przejrzenia funkcji i wymagań aplikacji. Aplikacja eShopOnContainers reprezentuje sklep online, który sprzedaje różne produkty fizyczne, takie jak koszulki i mugs kawy. W przypadku zakupu wszystkiego w trybie online środowisko korzystania ze sklepu powinno być stosunkowo znane. Poniżej przedstawiono niektóre podstawowe funkcje implementowane przez Sklep:

- Wyświetl listę elementów katalogu
- Filtruj elementy według typu
- Filtruj elementy według marki
- Dodawanie elementów do koszyka zakupów
- Edytuj lub Usuń elementy z koszyka
- Checkout
- Rejestrowanie konta
- Zaloguj się
- Wyloguj
- Przejrzyj zamówienia

Aplikacja ma również następujące wymagania niefunkcjonalne:

- Musi być wysoce dostępny i należy ją skalować automatycznie, aby zaspokoić zwiększony ruch (i przeskalować je ponownie po podłączeniu ruchu).
- Powinno to ułatwić szybkie korzystanie z monitorowania kondycji i dzienników diagnostycznych, aby pomóc w rozwiązywaniu wszelkich napotkanych problemów.
- Powinien obsługiwać proces programowania Agile, w tym obsługę ciągłej integracji i wdrażania (CI/CD).
- Oprócz dwóch frontonów sieci Web (aplikacja tradycyjna i jednostronicowa) aplikacja musi również obsługiwać aplikacje klienckie mobilne z różnymi rodzajami systemów operacyjnych.
- Powinien obsługiwać hosting na wielu platformach i Międzyplatformowe programowanie.

![Architektura tworzenia aplikacji eShopOnContainers Reference.](./media/eshoponcontainers-development-architecture.png)

**Rysunek 2-2**. Architektura tworzenia aplikacji eShopOnContainers Reference.

Aplikacja eShopOnContainers jest dostępna z poziomu klientów sieci Web lub urządzeń przenośnych, które uzyskują dostęp do aplikacji za pośrednictwem protokołu HTTPS, jako aplikacji serwera ASP.NET Core MVC lub odpowiedniej bramy interfejsu API. Bramy interfejsu API oferują kilka korzyści, takich jak oddzielenie usług zaplecza od indywidualnych klientów frontonu i zapewnienie lepszych zabezpieczeń. Aplikacja używa również powiązanego wzorca znanego jako zaplecza (BFF), który zaleca Tworzenie oddzielnych bram interfejsu API dla każdego klienta frontonu. Architektura referencyjna pokazuje, jak należy rozdzielić bramy interfejsu API w zależności od tego, czy żądanie pochodzi z klienta sieci Web czy aplikacji mobilnej.

Funkcjonalność aplikacji jest dzielona na wiele różnych mikrousług. Istnieją usługi odpowiedzialne za uwierzytelnianie i tożsamość, wyświetlanie listy elementów z katalogu produktów, zarządzanie koszykami zakupów użytkowników oraz umieszczanie zamówień. Każda z tych odrębnych usług ma swój własny magazyn trwały. Nie istnieje pojedynczy magazyn danych głównych, za pomocą którego wszystkie usługi będą współdziałać. Zamiast tego, koordynacja i komunikacja między usługami odbywa się zgodnie z wymaganą zasadami oraz za pomocą magistrali komunikatów.

Poszczególne mikrousługi są zaprojektowane inaczej, na podstawie ich indywidualnych wymagań. Oznacza to, że ich stos technologii może się różnić, chociaż są one tworzone przy użyciu platformy .NET Core i zaprojektowanej dla chmury. Prostsze usługi zapewniają dostęp do podstawowych magazynów danych za pomocą metody Create-Read-Update-Delete (CRUD), natomiast bardziej zaawansowane usługi używają opartych na domenie podejścia i wzorców do zarządzania złożonością biznesową.

![Różne rodzaje mikrousług](./media/different-kinds-of-microservices.png)

**Rysunek 2-3**. Różne rodzaje mikrousług.

## <a name="overview-of-the-code"></a>Przegląd kodu

Ponieważ używa mikrousług, aplikacja eShopOnContainers obejmuje kilka oddzielnych projektów i rozwiązań w swoim repozytorium GitHub. Oprócz oddzielnych rozwiązań i plików wykonywalnych, różne usługi są przeznaczone do uruchamiania w ramach własnych kontenerów, zarówno podczas lokalnego tworzenia, jak i w czasie wykonywania w środowisku produkcyjnym. Na rysunku 2-4 przedstawiono pełne rozwiązanie programu Visual Studio, w którym są zorganizowane różne projekty.

![Projekty w rozwiązaniu Visual Studio.](./media/projects-in-visual-studio-solution.png)

**Rysunek 2-4**. Projekty w rozwiązaniu Visual Studio.

Kod jest zorganizowany do obsługi różnych mikrousług, a w każdej mikrousłudze kod jest podzielony na logikę domeny, zagadnienia dotyczące infrastruktury oraz interfejs użytkownika lub punkt końcowy usługi. W wielu przypadkach zależności każdej usługi mogą być spełnione przez usługi platformy Azure w środowisku produkcyjnym, a także alternatywne opcje rozwoju lokalnego. Sprawdźmy, jak wymagania aplikacji są mapowane na usługi platformy Azure.

## <a name="understanding-microservices"></a>Informacje o mikrousługach

Ta książka koncentruje się na aplikacjach natywnych w chmurze utworzonych przy użyciu technologii platformy Azure. Aby dowiedzieć się więcej o najlepszych rozwiązaniach mikrousług i sposobach tworzenia architektury aplikacji opartych na mikrousługach, przeczytaj książkę pomocniczą i [mikrousługi platformy .NET: architektura dla kontenerów aplikacji .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook).

>[!div class="step-by-step"]
>[Poprzedni](candidate-apps.md) 
> [Dalej](map-eshoponcontainers-azure-services.md)
