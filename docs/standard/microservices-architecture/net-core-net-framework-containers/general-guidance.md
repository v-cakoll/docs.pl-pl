---
title: "Ogólne wskazówki"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Ogólne wskazówki"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fa58d1d81b2d1523baf123d4963db2ca00fee15d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="general-guidance"></a>Ogólne wskazówki

Ta sekcja zawiera podsumowanie kiedy należy wybrać oprogramowanie .NET Core lub .NET Framework. Udostępniamy więcej szczegółów na temat tych opcji w kolejnych sekcjach.

Konteneryzowanych Docker aplikacji serwera należy używać .NET Core z systemem Linux lub kontenery systemu Windows, gdy:

-   Możesz korzystać z wielu platform. Na przykład chcesz używać kontenery systemu Windows i Linux.

-   Architektury aplikacji jest oparty na mikrousług.

-   Potrzebne do szybkiego uruchamiania kontenery i ma mało miejsca na kontener, aby osiągnąć lepszą gęstość lub więcej kontenerów na jednostkę sprzętu w celu zmniejszenia kosztów.

Krótko mówiąc podczas tworzenia nowych konteneryzowanych aplikacji .NET, należy rozważyć .NET Core jako domyślny wybór. Ma wiele korzyści i najbardziej zgodnym z zasady kontenery klas i stylu pracy.

Dodatkową korzyścią z używania platformy .NET Core jest uruchomienie obok siebie wersje programu .NET dla aplikacji w tym samym komputerze. Świadczenie jest większe znaczenie dla serwerów i maszyn wirtualnych, które nie korzystają z kontenerów, ponieważ kontenery izolować wersje programu .NET, który aplikacja potrzebuje. (O ile są one zgodne z podstawowego systemu operacyjnego.)

Konteneryzowanych Docker aplikacji serwera należy używać .NET Framework z kontenerami systemu Windows, gdy:

-   Aplikacja obecnie korzysta z platformy .NET Framework i ma silne zależności w systemie Windows.

-   Należy użyć interfejsów API systemu Windows, które nie są obsługiwane przez oprogramowanie .NET Core.

-   Należy użyć bibliotek .NET innych firm lub pakietów NuGet, które nie są dostępne dla platformy .NET Core.

Za pomocą .NET Framework na Docker może poprawić komfort pracy wdrażania zminimalizować problemy z wdrażaniem. To [ *scenariusza "przyrostu i przesunięcia"* ](https://aka.ms/liftandshiftwithcontainersebook) jest ważna w przypadku starszych aplikacji, które pierwotnie opracowano z tradycyjnego .NET Framework, takich jak formularzy sieci Web ASP.NET, MVC sieci web aplikacji lub usługi WCF (containerizing Usługi Windows Communication Foundation).

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Książka elektroniczna: modernizacji istniejących aplikacji .NET Framework z platformy Azure i kontenery Windows**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)

-   **Przykładowe aplikacje: modernizacji starsze aplikacje sieci web ASP.NET przy użyciu systemu Windows kontenery**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)


>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (net-core kontenera scenarios.md)
