---
title: Wskazówki ogólne
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Ogólne wytyczne
ms.date: 09/11/2018
ms.openlocfilehash: 2fa66d7593b764a8df4d9acc20f93d3f8fb26174
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089648"
---
# <a name="general-guidance"></a>Wskazówki ogólne

Ta sekcja zawiera podsumowanie, kiedy wybrać .NET Core lub .NET Framework. Więcej szczegółów na temat tych wyborów udostępniamy w poniższych sekcjach.

Aby kontenerowa aplikacja serwera Platformy Docker była używana w kontenerach do serwera Platformy Docker, należy używać programu .NET Core z kontenerami systemu Linux lub Kontenerów systemu Windows, gdy:

- Masz potrzeby wieloplatformowe. Na przykład chcesz używać kontenerów Linux i Windows.

- Architektura aplikacji jest oparta na mikrousługach.

- Musisz szybko uruchomić kontenery i chcesz mieć niewielką powierzchnię na kontener, aby osiągnąć lepszą gęstość lub więcej kontenerów na jednostkę sprzętową, aby obniżyć koszty.

Krótko mówiąc, podczas tworzenia nowych konteneryzowanych aplikacji .NET należy rozważyć .NET Core jako domyślny wybór. Ma wiele zalet i najlepiej pasuje do filozofii pojemników i stylu pracy.

Dodatkową zaletą korzystania z programu .NET Core jest możliwość uruchamiania obok siebie wersji .NET dla aplikacji na tym samym komputerze. Ta korzyść jest ważniejsza dla serwerów lub maszyn wirtualnych, które nie używają kontenerów, ponieważ kontenery izolują wersje .NET, których potrzebuje aplikacja. (Tak długo, jak są one zgodne z podstawowym systemem operacyjnym).

Należy użyć .NET Framework dla konteneryzowanej aplikacji serwera Platformy Docker, gdy:

- Aplikacja korzysta obecnie z platformy .NET Framework i ma silne zależności w systemie Windows.

- Należy użyć interfejsów API systemu Windows, które nie są obsługiwane przez program .NET Core.

- Należy użyć bibliotek .NET innych firm lub pakietów NuGet, które nie są dostępne dla .NET Core.

Za pomocą platformy .NET Framework na platformie Docker można poprawić środowisko wdrażania, minimalizując problemy z wdrażaniem. Ten [scenariusz "lift and shift"](https://aka.ms/liftandshiftwithcontainersebook) jest ważny dla konteneryzacji starszych aplikacji, które zostały pierwotnie opracowane przy tradycyjnych .NET Framework, takich jak ASP.NET WebForms, Aplikacje internetowe MVC lub Usługi WCF (Windows Communication Foundation).

### <a name="additional-resources"></a>Zasoby dodatkowe

- **E-book: Modernizacja istniejących aplikacji .NET Framework za pomocą platformy Azure i kontenerów systemu Windows**  
    https://aka.ms/liftandshiftwithcontainersebook

- **Przykładowe aplikacje: modernizacja starszych ASP.NET aplikacji sieci Web przy użyciu kontenerów systemu Windows**  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](net-core-container-scenarios.md)
