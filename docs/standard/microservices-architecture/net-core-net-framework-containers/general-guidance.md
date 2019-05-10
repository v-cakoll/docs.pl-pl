---
title: Wskazówki ogólne
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Ogólne wskazówki
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: b75bede39f524ea55c77bdb94cd4f2ef94f4d06b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589824"
---
# <a name="general-guidance"></a>Wskazówki ogólne

Ta sekcja zawiera podsumowanie, kiedy należy wybrać .NET Core lub .NET Framework. Firma Microsoft zapewnia więcej szczegółów na temat tych opcji w kolejnych sekcjach.

Skorzystaj z platformy .NET Core z systemem Linux lub kontenerów Windows konteneryzowanej aplikacji serwera platformy Docker po:

- Masz wymagania dla wielu platform. Na przykład chcesz użyć kontenery Windows i Linux.

- Architektury aplikacji jest oparta na mikrousługach.

- Musisz szybko Uruchom kontenery i mają niewielkie rozmiary kontenera w celu osiągnięcia lepszej gęstości lub większej liczbie kontenerów na jednostkę sprzętu w celu obniżenia kosztów.

Krótko mówiąc podczas tworzenia nowych konteneryzowanych aplikacji platformy .NET, należy rozważyć platformy .NET Core jako domyślnego wyboru. Ma wiele zalet i najbardziej zgodnym z kontenerów filozofii i stylu pracy.

Następującą dodatkową korzyść: za pomocą platformy .NET Core jest uruchomienie obok siebie wersji platformy .NET dla aplikacji w ramach tej samej maszynie. Ta korzyść jest niezwykle ważne w przypadku serwerów lub maszyn wirtualnych, które nie korzystają z kontenerów, ponieważ kontenery izolowania wersji platformy .NET, która aplikacja potrzebuje. (Tak długo, jak są one zgodne z podstawowego systemu operacyjnego.)

Należy używać .NET Framework dla konteneryzowanych aplikacji serwera platformy Docker po:

- Aplikacja obecnie korzysta z .NET Framework i ma silną zależności od Windows.

- Musisz użyć interfejsów API Windows, które nie są obsługiwane przez .NET Core.

- Musisz użyć biblioteki .NET innych firm lub pakiety NuGet, które nie są dostępne dla platformy .NET Core.

Przy użyciu .NET Framework na platformy Docker można poprawić środowisko wdrażania, minimalizując problemów dotyczących wdrożenia. To [scenariusza "metodą lift and shift"](https://aka.ms/liftandshiftwithcontainersebook) jest ważne w przypadku konteneryzowania starsze aplikacje, które zostały pierwotnie opracowana tradycyjnym środowisku .NET Framework, takich jak formularzy sieci Web platformy ASP.NET, MVC sieci web aplikacji lub usługi WCF (Windows Communication Foundation ) usługi.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **eBook: Modernizacja istniejących aplikacji .NET Framework z platformą Azure i kontenerów Windows**  
    https://aka.ms/liftandshiftwithcontainersebook

- **Przykładowe aplikacje: Modernizacja starsze aplikacje sieci web ASP.NET za pomocą kontenerów Windows**  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](net-core-container-scenarios.md)