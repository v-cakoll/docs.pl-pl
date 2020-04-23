---
title: Wybierz odpowiednią opcję hostingu platformy Azure
description: Dowiedz się, która ścieżka migracji platformy Azure jest odpowiednia dla aplikacji sieci Web ASP.NET.
author: CESARDELATORRE
ms.author: cesardl
ms.date: 03/01/2020
ms.openlocfilehash: a8ad946b03f97272cb8685620858af6b21a372dc
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "82072110"
---
# <a name="choose-the-right-azure-hosting-option"></a>Wybierz odpowiednią opcję hostingu platformy Azure

W tym artykule przedstawiono zagadnienia i porównania między wieloma wyborami na platformie Azure podczas migrowania istniejących aplikacji .NET Framework ze środowisk lokalnych na platformę Azure.

Podstawowe obszary, które należy wziąć pod uwagę podczas migrowania istniejących aplikacji .NET do platformy Azure:

1. Opcje obliczania
1. Opcje bazy danych
1. Zagadnienia dotyczące sieci i zabezpieczeń
1. Zagadnienia dotyczące uwierzytelniania i autoryzacji

## <a name="compute-choices"></a>Opcje obliczania

Podczas migrowania istniejących aplikacji .NET Framework na platformę Azure można wybrać wiele opcji. Jednak ponieważ .NET Framework zależy od systemu Windows, następujące wybory są ograniczone do usług obliczeniowych opartych na systemie Windows.

W poniższej tabeli przedstawiono kilka porównań i zaleceń, które ułatwiają wybranie odpowiedniej ścieżki migracji obliczeń dla istniejącej aplikacji platformy .NET.

|                 | Maszyny wirtualne platformy Azure | Azure App Service | Kontenery systemu Windows |
|-----------------|-----------|-------------------|--------------------|
|Kiedy stosować      |<ul><li>Aplikacja ma silne zależności od instalacji serwera i pliku Local. msi.</li><li>Chcesz najłatwiejszą ścieżkę migracji aplikacji</li></ul>|Aplikacja nie ma żadnych zależności na serwerze. jest to tylko czysta aplikacja sieci Web ASP.NET (MVC, WebForm) lub aplikacja N-warstwowa (Web API, WCf) uzyskujący dostęp do serwera bazy danych. |<ul><li>Aplikacja ma zależności na oryginalnym serwerze, ale te zależności można dołączać do obrazu platformy Docker systemu Windows.</li><li>Chcesz przeprowadzić modernizację aplikacji, tak aby była w [chmurze DevOps — gotowa](../../architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)</li></ul>|
|Specjaliści & korzyści  |<ul><li>Najprostsza ścieżka migracji</li><li>Znane środowisko. Środowisko wdrażania jest maszyną wirtualną, dlatego jest podobna do serwerów lokalnych.</li></ul> |Ciągła konserwacja PaaS, najprostszy sposób na zarządzanie aplikacjami i skalowanie ich na platformie Azure. |<ul><li>Przygotowana na przyszłość DevOps w chmurze z zależnościami zawartymi w kontenerach aplikacji.</li><li>Nie ma już potrzeby refaktoryzacji programu .NET/C # Code.</li></ul> |
|Wady             |Jest to IaaS. Konserwacja jest kosztowna. Należy zarządzać infrastrukturą maszyny wirtualnej dotyczącą sieci, równoważenia obciążenia, skalowania, zarządzania usługami IIS i tak dalej. |<ul><li>Nie wszystkie aplikacje są [obsługiwane](https://appmigration.microsoft.com/assessment)</li><li>Niektóre aplikacje mogą wymagać refaktoryzacji, a nawet w niewielkim stopniu, aby obsługiwały Azure App Service.</li></ul> |<ul><li>Krzywa szkoleniowa dotycząca umiejętności platformy Docker</li><li>Niektóre zmiany ustawień konfiguracji kodu i aplikacji</li></ul>|
|Wymagania |Maszyna wirtualna z systemem Windows Server z takimi samymi wymaganiami, jak w przypadku aplikacji lokalnych | Azure App Service wymagania określone w [kontrolach gotowości](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks). |<ul><li>[Aparat platformy Docker — Enterprise dla systemu Windows Server 2019](https://azuremarketplace.microsoft.com/marketplace/apps/cloud-infrastructure-services.docker-windows-2019)<br />lub</li><li>[Azure Container Service (AKS)](https://azure.microsoft.com/services/container-service/) (Kubernetes Orchestrator)<br />lub<li>[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) Orchestrator</li></ul> |
|Jak przeprowadzić migrację |Zobacz [Migrowanie do usługi Azure Virtual Machines](vm.md) | Zobacz [migrowanie Azure App Service](app-service.md) | Postępuj zgodnie z zagadnieniami, scenariuszami i instruktażami opisanymi w temacie [Modernizacja istniejących aplikacji .NET za pomocą platformy Azure i kontenerów systemu Windows w książek elektronicznej](https://aka.ms/liftandshiftwithcontainersebook) |

Poniższy diagram schematu blokowego przedstawia drzewo decyzyjne podczas planowania migracji na platformę Azure dla istniejących aplikacji .NET Framework. Jeśli jest to możliwe, wypróbuj najpierw opcję, ale opcja B jest najłatwiejszą ścieżką do wykonania.

![Schemat blokowy przedstawiający drzewo decyzyjne](../media/migration/choose/decision-tree.png)

## <a name="database-choices"></a>Opcje bazy danych

Podczas migrowania relacyjnych baz danych do platformy Azure można wybrać wiele opcji. Zobacz [Migrowanie bazy danych SQL Server na platformę Azure](sql.md) , aby ułatwić wybór odpowiedniej ścieżki migracji bazy danych dla istniejącej aplikacji platformy .NET.

## <a name="networking-and-security-considerations"></a>Zagadnienia dotyczące sieci i zabezpieczeń

Podczas wdrażania aplikacji w chmurze publicznej, takiej jak Microsoft Azure, można wyizolować i zabezpieczyć niektóre sieci, [tworząc stref DMZ sieci](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/), [na przykład strefę DMZ między platformą Azure i lokalną](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) lub [strefą DMZ między platformą Azure i Internetem](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz). Stref DMZ można zaimplementować przy użyciu [usługi Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

Usługa Azure Virtual Networks umożliwia:

- Tworzenie infrastruktury hybrydowej kontrolowanej przez użytkownika
- Przenoszenie własnych adresów IP i serwerów DNS
- Zabezpieczanie połączeń za pomocą sieci VPN IPsec lub ExpressRoute
- Uzyskaj szczegółową kontrolę nad ruchem między podsieciami
- Tworzenie zaawansowanych topologii sieci przy użyciu urządzeń wirtualnych
- Uzyskaj izolowane i wysoce bezpieczne środowisko dla aplikacji

Aby rozpocząć tworzenie własnej sieci wirtualnej, zapoznaj się z [dokumentacją usługi Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/).

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Zagadnienia dotyczące uwierzytelniania i autoryzacji podczas migracji na platformę Azure

Najważniejszym problemem w przypadku każdej organizacji przenoszonej do chmury jest bezpieczeństwo. Większość firm zainwestował znaczną ilość czasu, pieniędzy i inżynierii na projektowanie i opracowywanie modelu zabezpieczeń, a ważne jest, aby korzystać z istniejących inwestycji, takich jak magazyny tożsamości i rozwiązania do rejestracji jednokrotnej.

Wiele istniejących aplikacji B2E platformy .NET działających Active Directory lokalnie na potrzeby uwierzytelniania i zarządzania tożsamościami. Azure AD Connect umożliwia integrację katalogów lokalnych z Azure Active Directory. Aby rozpocząć, zobacz [integrowanie katalogów lokalnych z Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

Zapoznaj się z wymaganiami dotyczącymi [tożsamości hybrydowego rozwiązania](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs) do tworzenia tożsamości, aby kontynuować planowanie dotyczące Azure Active Directory.

Inne opcje protokołu uwierzytelniania to [OAuth](https://en.wikipedia.org/wiki/OAuth) i [OpenID Connect](https://en.wikipedia.org/wiki/OpenID), które są wspólne w aplikacjach przeznaczonych dla klientów. W przypadku korzystania z autonomicznych baz danych tożsamości, takich jak ASP.NET Identity baza danych SQL opakowana przy użyciu protokołu OAuth, nie jest zwykle wymagane połączenie z lokalnymi bazami danych lub katalogami.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Migrowanie aplikacji sieci Web ASP.NET do Azure App Service](app-service.md)
