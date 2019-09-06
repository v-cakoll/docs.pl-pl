---
title: Wskazówki ogólne
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Ogólne wskazówki
ms.date: 09/11/2018
ms.openlocfilehash: 0981cb16d5aa2036391caba0cf6ad3ac5c44ed6f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296529"
---
# <a name="general-guidance"></a>Wskazówki ogólne

Ta sekcja zawiera podsumowanie, kiedy należy wybrać platformę .NET Core lub .NET Framework. Więcej informacji o tych opcjach znajduje się w poniższych sekcjach.

Należy używać platformy .NET Core z kontenerami systemu Linux lub Windows dla aplikacji serwera platformy Docker, gdy:

- Wymagania dotyczące wielu platform. Na przykład chcesz użyć kontenerów systemów Linux i Windows.

- Architektura aplikacji jest oparta na mikrousługach.

- Należy szybko rozpocząć pracę z kontenerami i mieć niewielki wpływ na kontener, aby osiągnąć lepszą gęstość lub więcej kontenerów na jednostkę sprzętową w celu obniżenia kosztów.

W krótkim czasie podczas tworzenia nowych kontenerów aplikacji .NET należy rozważyć wybór domyślny dla platformy .NET Core. Ma wiele korzyści i najlepiej pasuje do tej i stylu pracy kontenerów.

Dodatkową zaletą korzystania z platformy .NET Core jest możliwość uruchamiania równoległych wersji platformy .NET dla aplikacji znajdujących się na tym samym komputerze. Ta korzyść jest bardziej ważna w przypadku serwerów lub maszyn wirtualnych, które nie korzystają z kontenerów, ponieważ kontenery izolują wersje programu .NET, których potrzebuje aplikacja. (Pod warunkiem, że są one zgodne z bazowym systemem operacyjnym).

.NET Framework dla aplikacji serwera platformy Docker należy używać w przypadku:

- Obecnie aplikacja używa .NET Framework i ma silne zależności w systemie Windows.

- Należy używać interfejsów API systemu Windows, które nie są obsługiwane przez platformę .NET Core.

- Musisz użyć bibliotek .NET innych firm lub pakietów NuGet, które nie są dostępne dla platformy .NET Core.

Używanie .NET Framework na platformie Docker może ulepszyć środowisko wdrażania, minimalizując problemy z wdrażaniem. Ten [scenariusz "Unieś i Shift"](https://aka.ms/liftandshiftwithcontainersebook) jest istotny dla konteneryzowania starszych aplikacji, które zostały pierwotnie opracowane przy użyciu tradycyjnych .NET Framework, takich jak ASP.NET WebForms, Web Apps i WCF (Windows Communication Foundation).

### <a name="additional-resources"></a>Dodatkowe zasoby

- **eBook: Modernizacja istniejących aplikacji .NET Framework przy użyciu platformy Azure i kontenerów systemu Windows**  
    https://aka.ms/liftandshiftwithcontainersebook

- **Przykładowe aplikacje: Modernizacja starszych aplikacji internetowych ASP.NET przy użyciu kontenerów systemu Windows**  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
>[Poprzedni](index.md)Następny
>[](net-core-container-scenarios.md)
