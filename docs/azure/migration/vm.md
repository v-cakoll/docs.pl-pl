---
title: Migrowanie aplikacji sieci Web ASP.NET na maszynę wirtualną platformy Azure
description: Dowiedz się, jak przeprowadzić migrację ASP.NET aplikacji sieci Web z lokalnego urządzenia do maszyny wirtualnej platformy Azure.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: cc9477de92e6105762636ed3a2241949e69ac8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "82072124"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>Migrowanie aplikacji sieci Web ASP.NET do maszyny wirtualnej platformy Azure

Ten dokument zawiera omówienie sposobu migracji ASP.NET aplikacji sieci web z lokalnego do maszyny wirtualnej platformy Azure.

## <a name="quickstart"></a>Szybki start

Dowiedz się, jak utworzyć maszynę wirtualną i opublikować w niej aplikację: [publikowanie na maszynie wirtualnej platformy Azure](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>Rozpoczęcie pracy

Te samouczki pokazują kroki tworzenia (lub migracji) maszyny wirtualnej, publikowania aplikacji sieci web do niej i innych zadań, które mogą być wymagane do obsługi aplikacji na platformie Azure.

- Utwórz maszynę wirtualną dla aplikacji ASP.NET na platformie Azure, korzystając z jednej z następujących opcji:
  - [Tworzenie nowej maszyny wirtualnej dla aplikacji ASP.NET](https://go.microsoft.com/fwlink/?linkid=863237)
  - [Migrowanie istniejącej lokalnej maszyny wirtualnej VMWare](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware)
  - [Migrowanie istniejącej lokalnej maszyny wirtualnej funkcji Hyper-V](https://docs.microsoft.com/azure/migrate/tutorial-migrate-hyper-v)
- [Publikowanie aplikacji przy użyciu programu Visual Studio](https://go.microsoft.com/fwlink/?linkid=863240)
- [Tworzenie bezpiecznej sieci wirtualnej dla maszyn wirtualnych](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [Tworzenie potoku ciągłej integracji/ciągłego wdrażania dla aplikacji](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [Przejście do zestawu skalowania maszyny Wirtualnej w celu zapewnienia wysokiej dostępności i skalowalności](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>Zagadnienia do rozważenia

### <a name="benefits"></a>Korzyści

Maszyny wirtualne oferują najłatwiejszą ścieżkę do migracji aplikacji z lokalnego do chmury. Umożliwiają one replikację tego samego środowiska, którego aplikacja używa lokalnie, eliminując jednocześnie konieczność obsługi własnych centrów danych. Zestawy skalowania maszyny wirtualnej zapewniają wysoką dostępność i skalowalność aplikacji działających na maszynach wirtualnych.

### <a name="virtual-machine-size"></a>Rozmiar maszyny wirtualnej

Wybierz rozmiar i typ maszyny wirtualnej, który jest najlepiej zoptymalizowany pod kątem obciążenia. Aby uzyskać więcej informacji, zobacz [Rozmiary maszyn wirtualnych systemu Windows na platformie Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).

### <a name="maintenance"></a>Konserwacja

Podobnie jak na komputerze lokalnym, jesteś odpowiedzialny za utrzymanie i aktualizację maszyny wirtualnej<sup>&#42;</sup>. Jeśli aplikacja może działać w środowisku platformy jako usługi (PaaS), takich jak [usługa Azure App Service](https://docs.microsoft.com/azure/app-service/) lub w [kontenerze,](https://docs.microsoft.com/azure/app-service/containers/)które usuną tę potrzebę.

*<sup>&#42;</sup> [Automatyczne uaktualnienia systemu operacyjnego dla zestawów skalowania maszyny wirtualnej](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) są obecnie dostępne jako usługa w wersji zapoznawczej.*

### <a name="virtual-networks"></a>Sieci wirtualne

Sieci wirtualne platformy Azure umożliwiają:

- Tworzenie kontrolowanej infrastruktury hybrydowej
- Przynieś własne adresy IP i serwery DNS
- Tworzenie odizolowanego i wysoce bezpiecznego środowiska dla aplikacji
- Łączenie maszyny wirtualnej z siecią lokalną przy użyciu jednej z kilku [opcji łączności](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)
- Integracja maszyny wirtualnej z siecią lokalną przy użyciu usługi [ExpressRoute](https://azure.microsoft.com/services/expressroute/)

Aby rozpocząć, zapoznaj się z [dokumentacją sieci wirtualnej](https://docs.microsoft.com/azure/virtual-network/)

### <a name="active-directory"></a>Usługa Active Directory
Wiele aplikacji używa usługi Active Directory do uwierzytelniania i zarządzania tożsamościami.

- Usługa Azure AD Connect umożliwia integrację katalogów lokalnych z usługą Azure Active Directory. Aby rozpocząć, zobacz [Integrowanie katalogów lokalnych z usługą Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).
- Alternatywnie [usługa ExpressRoute](https://azure.microsoft.com/services/expressroute/) umożliwia aplikacji dostęp do lokalnej usługi Active Directory.

### <a name="sql-databases"></a>Bazy danych SQL

Jeśli aplikacja korzysta z lokalnej bazy danych, aplikacja nie będzie mogła domyślnie z nią rozmawiać. Można:

- Skonfiguruj sieć hybrydową, która umożliwia aplikacji dostęp do bazy danych działającej lokalnie.
- Migrowanie bazy danych na platformę Azure. Aby uzyskać więcej informacji, zobacz [Migrowanie bazy danych programu SQL Server na platformę Azure](sql.md).

### <a name="high-availability-and-scalability"></a>Wysoka dostępność i skalowalność

#### <a name="virtual-machine-scale-sets"></a>Zestawy skali maszyn wirtualnych
Chcesz upewnić się, że aplikacja jest wysoce dostępna i można skalować, migrować obraz maszyny wirtualnej do zestawu skalowania maszyny wirtualnej platformy Azure, aby zwiększyć dostępność i skalowalność aplikacji. Zestawy skalowania maszyny Wirtualnej zapewniają możliwość używania istniejącej maszyny Wirtualnej, która została już skonfigurowana lub skonfigurowania potoku kompilacji w celu utworzenia obrazu za pomocą aplikacji.

Aby rozpocząć, zobacz [Wdrażanie aplikacji w zestawach skalowania maszyny wirtualnej](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).

#### <a name="centralized-logging"></a>Scentralizowane rejestrowanie
Podczas uruchamiania aplikacji w wielu wystąpieniach należy rozważyć przechowywanie dzienników w scentralizowanej lokalizacji, takiej jak [usługa Azure Storage.](https://docs.microsoft.com/azure/storage/)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Migrowanie bazy danych programu SQL Server na platformę Azure](sql.md)
