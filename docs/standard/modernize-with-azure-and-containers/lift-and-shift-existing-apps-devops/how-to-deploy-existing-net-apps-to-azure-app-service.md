---
title: "Jak wdrożyć istniejących aplikacji .NET w usłudze Azure App Service"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Jak wdrożyć istniejących aplikacji .NET w usłudze Azure App Service"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84bffe7aad6bbffb40519c9146d8156159d55850
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a>Jak wdrożyć istniejących aplikacji .NET w usłudze Azure App Service 

Funkcja Web Apps w usłudze Azure App Service jest w pełni zarządzana platforma obliczeniowa zoptymalizowana pod kątem obsługi aplikacji sieci web i witryn sieci Web. Tej oferty PaaS w Microsoft Azure umożliwia można skupić się na logice biznesowej, podczas gdy platforma Azure jest odpowiedzialna infrastruktury do uruchamiania i skalowania aplikacji.

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a>Sprawdź poprawność witryn i migracji do usługi App Service przy użyciu Asystenta migracji usługi aplikacji Azure

Podczas tworzenia nowej aplikacji w programie Visual Studio, zwykle przenoszenie aplikacji do usługi App Service jest prosta. Jednak jeśli planujesz migrację istniejącej aplikacji do usługi App Service, należy najpierw ocenić, czy zależności wszystkich aplikacji są zgodne z usługi aplikacji. W tym zależności, takich jak system operacyjny serwera i oprogramowanie innych firm jest zainstalowany na serwerze.

Można użyć [Asystenta migracji usługi aplikacji Azure](https://www.migratetoazure.net/) do analizowania witryn i następnie ich migracja z systemu Windows i Linux serwerów sieci web do usługi App Service. W ramach migracji narzędzie tworzy aplikacje sieci web i baz danych na platformie Azure w razie potrzeby publikuje zawartości i publikuje bazy danych.

Azure App Service Asystenta migracji obsługuje migrację z usług IIS w systemie Windows Server do chmury. Usługi aplikacji obsługuje system Windows Server 2003 i nowszych wersjach.

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> **Rysunek 4 – 5.** Przy użyciu Asystenta migracji usługi aplikacji Azure

Aplikacja usługi migracji Asystent jest narzędziem do witryny sieci Web są przenoszone z serwerów sieci web w chmurze platformy Azure.

Po przeprowadzeniu migracji witryny sieci Web do usług aplikacji, witryna zawiera wszystko, co jest potrzebne do uruchomienia bezpiecznie i wydajne. Lokacje ustawiania i automatyczne uruchamianie w usłudze PaaS w chmurze Azure (usługa aplikacji).

Narzędzie migracji usługi aplikacji może analiza witryny sieci Web i raport dotyczący ich zgodność z narzędziami do przechodzenia do usługi App Service. W przypadku modyfikowania analizy, możesz pozwolić aplikacji usługi Asystenta migracji migracji zawartości, danych i ustawień dla Ciebie. Jeśli lokacja nie jest jeszcze zgodne, narzędzie do migracji informuje, należy dostosować do własnych preferencji.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Asystent migracji usługi aplikacji Azure**

    [https://www.migratetoazure.net/](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
[Poprzednie](what-about-cloud-optimized-applications.md)
[dalej](deploy-existing-net-apps-as-windows-containers.md)
