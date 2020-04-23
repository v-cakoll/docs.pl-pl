---
title: Wybierz odpowiednią opcję hostingu platformy Azure
description: Dowiedz się, która ścieżka migracji platformy Azure jest odpowiednia dla twojej ASP.NET aplikacji sieci web.
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

Ten artykuł zawiera zagadnienia i porównania między wieloma możliwościami wyboru na platformie Azure podczas migracji istniejących aplikacji platformy .NET Framework z lokalnego programu Azure.

Podstawowe obszary, które należy wziąć pod uwagę podczas migracji istniejących aplikacji platformy .NET na platformę Azure, to:

1. Opcje obliczania
1. Wybór bazy danych
1. Zagadnienia dotyczące sieci i bezpieczeństwa
1. Zagadnienia dotyczące uwierzytelniania i autoryzacji

## <a name="compute-choices"></a>Opcje obliczania

Podczas migracji istniejących aplikacji .NET Framework na platformę Azure masz wiele możliwości wyboru. Jednak ponieważ program .NET Framework zależy od systemu Windows, następujące opcje są ograniczone do usług obliczeniowych opartych na systemie Windows.

W poniższej tabeli przedstawiono kilka porównań i zaleceń ułatwiające wybranie właściwej ścieżki migracji obliczeniowej dla istniejącej aplikacji .NET.

|                 | Maszyny wirtualne platformy Azure | Azure App Service | Kontenery systemu Windows |
|-----------------|-----------|-------------------|--------------------|
|Kiedy stosować      |<ul><li>Aplikacja ma silne zależności od serwera i lokalnych instalacji msi.</li><li>Chcesz najłatwiejszą ścieżkę migracji aplikacji</li></ul>|Aplikacja nie ma zależności na serwerze, jest to tylko czysta ASP.NET aplikacji sieci web (MVC, WebForm) lub N-Tier app (Web API, WCf) dostęp do serwera bazy danych. |<ul><li>Aplikacja ma zależności od oryginalnego serwera, ale te zależności mogą być zawarte w obrazie systemu Windows platformy Docker.</li><li>Chcesz zmodernizować aplikację tak, aby była [gotowa do pracy w chmurze](../../architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)</li></ul>|
|Plusy & korzyści  |<ul><li>Najłatwiejsza ścieżka migracji</li><li>Znane środowisko. Środowisko wdrażania jest maszyną wirtualną, więc jest podobne do serwerów lokalnych.</li></ul> |Ciągła konserwacja PaaS, najprostszy sposób zarządzania aplikacjami i skalowania ich na platformie Azure. |<ul><li>Przygotowany na przyszłość, Cloud DevOps-Ready z zależnościami zawartymi w kontenerach aplikacji.</li><li>Prawie nie ma potrzeby refaktoryzacji .NET /C# kod.</li></ul> |
|Wady             |To jest IaaS. Konserwacja jest kosztowna. Musisz zarządzać infrastrukturą maszyny Wirtualnej na temat sieci, modułu równoważenia obciążenia, skalowania w poziomie, zarządzania usługami IIS i tak dalej. |<ul><li>Nie wszystkie aplikacje są [obsługiwane](https://appmigration.microsoft.com/assessment)</li><li>Niektóre aplikacje mogą wymagać refaktoryzacji, a nawet nieco przeprojektowane, więc obsługują usługę Azure App Service.</li></ul> |<ul><li>Krzywa uczenia się umiejętności platformy Docker</li><li>Niektóre zmiany ustawień konfiguracji kodu i aplikacji</li></ul>|
|Wymagania |Maszyna wirtualna systemu Windows Server z tymi samymi wymaganiami niż aplikacja dla środowiska lokalnego | Wymagania usługi Azure App Service określone w [kontrolach gotowości](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks). |<ul><li>[Aparat platformy Docker — enterprise dla systemu Windows Server 2019](https://azuremarketplace.microsoft.com/marketplace/apps/cloud-infrastructure-services.docker-windows-2019)<br />lub</li><li>[Usługa kontenera azure (AKS)](https://azure.microsoft.com/services/container-service/) (to jest orchestrator Kubernetes)<br />lub<li>[Koordynator sieci szkieletowej usług Azure](https://azure.microsoft.com/services/service-fabric/)</li></ul> |
|Jak przeprowadzić migrację |Zobacz [Migracja do maszyn wirtualnych platformy Azure](vm.md) | Zobacz [Migrowanie usługi Azure App Service](app-service.md) | Postępuj zgodnie z zagadnieniami, scenariuszami i przewodnikami wyjaśnionymi w [programie Modernizowanie istniejących aplikacji platformy .NET za pomocą usługi Azure i witryny kontenerów systemu Windows w systemie eBook](https://aka.ms/liftandshiftwithcontainersebook) |

Na poniższym diagramie schematu blokowego przedstawiono drzewo decyzji podczas planowania migracji na platformę Azure dla istniejących aplikacji .NET Framework. Jeśli jest to opłacalne, najpierw wypróbuj opcję A, ale opcja B jest najłatwiejszą ścieżką do wykonania.

![Schemat blokowy przedstawiający drzewo decyzji hostingu](../media/migration/choose/decision-tree.png)

## <a name="database-choices"></a>Wybór bazy danych

Podczas migracji relacyjnych baz danych na platformę Azure masz wiele możliwości wyboru. Zobacz [Migrowanie bazy danych programu SQL Server na platformę Azure,](sql.md) aby ułatwić wybór właściwej ścieżki migracji bazy danych dla istniejącej aplikacji .NET.

## <a name="networking-and-security-considerations"></a>Zagadnienia dotyczące sieci i bezpieczeństwa

Podczas wdrażania aplikacji w chmurze publicznej, takiej jak Microsoft Azure, można wyizolować i zabezpieczyć niektóre sieci, [tworząc sieciowe strefy DMZ,](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/)takie jak [strefa DMZ między platformą Azure i lokalną](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) lub strefa [DMZ między platformą Azure a Internetem.](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz) Strefy DMZ można zaimplementować za pomocą [usługi Azure Virtual Network.](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)

Sieci wirtualne platformy Azure umożliwiają:

- Tworzenie kontrolowanej infrastruktury hybrydowej
- Przynieś własne adresy IP i serwery DNS
- Zabezpieczanie połączeń za pomocą sieci VPN IPsec lub usługi ExpressRoute
- Uzyskaj szczegółową kontrolę nad ruchem między podsieciami
- Tworzenie zaawansowanych topologii sieci przy użyciu urządzeń wirtualnych
- Uzyskaj odizolowane i wysoce bezpieczne środowisko dla swoich aplikacji

Aby rozpocząć tworzenie własnej sieci wirtualnej, zobacz [dokumentację sieci wirtualnej platformy Azure](https://docs.microsoft.com/azure/virtual-network/).

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Zagadnienia dotyczące uwierzytelniania i autoryzacji podczas migracji na platformę Azure

Głównym problemem każdej organizacji przechodzącej do chmury jest bezpieczeństwo. Większość firm zainwestowała znaczną ilość czasu, pieniędzy i inżynierii w projektowanie i rozwój modelu zabezpieczeń i ważne jest, aby były w stanie wykorzystać istniejące inwestycje, takie jak magazyny tożsamości i rozwiązania do logowania jednokrotnego.

Wiele istniejących aplikacji korporacyjnych B2E .NET działających lokalnie używa usługi Active Directory do uwierzytelniania i zarządzania tożsamościami. Usługa Azure AD Connect umożliwia integrację katalogów lokalnych z usługą Azure Active Directory. Aby rozpocząć, zobacz [Integrowanie katalogów lokalnych z usługą Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

Zobacz [wymagania dotyczące tożsamości dla rozwiązania tożsamości hybrydowej](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs) do dalszego planowania związanego z usługą Azure Active Directory.

Inne opcje protokołu uwierzytelniania to [OAuth](https://en.wikipedia.org/wiki/OAuth) i [OpenID](https://en.wikipedia.org/wiki/OpenID), które są powszechne w aplikacjach konsumenckich. W przypadku korzystania z autonomicznych baz danych tożsamości, takich jak baza danych SQL ASP.NET opakowane przez IdentityServer4 przy użyciu OAuth, zwykle nie jest wymagana łączność z lokalnymi bazami danych lub katalogami.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Migrowanie aplikacji sieci web ASP.NET do usługi Azure App Service](app-service.md)
