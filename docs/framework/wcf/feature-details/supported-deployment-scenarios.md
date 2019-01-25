---
title: Obsługiwane scenariusze wdrażania
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 605521cb91945812db178db3a82883b4d13bc636
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614487"
---
# <a name="supported-deployment-scenarios"></a>Obsługiwane scenariusze wdrażania
Podzbiór funkcji Windows Communication Foundation (WCF) obsługiwanych na częściowo zaufane aplikacje zaprojektowano w celu spełnienia wymagań niektórych, ale nie wszystkie scenariusze przy użyciu usługi WCF. Na serwerze, WCF, spełnia wymagania skali Internetu udostępniony dostawcy hostingu, którzy uruchamiają aplikacje innych producentów w [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] zestaw ze względów bezpieczeństwa uprawnień trybie średniego zaufania. Na komputerze klienckim, Obsługa częściowej relacji zaufania usługi WCF zaprojektowano w celu spełnienia wymagań technologie wdrażania, takie jak [wdrażania ClickOnce](https://go.microsoft.com/fwlink/?LinkId=83712) lub [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]w aplikacji przeglądarki XAML technologii, która umożliwia bezproblemową i bezpieczną Wdrażanie aplikacji dla komputerów osobistych z niezaufanych witryn.  
  
## <a name="minimum-permission-requirements"></a>Wymagania dotyczące minimalnych uprawnień  
 Usługi WCF obsługuje podzbiór funkcji w aplikacjach działających w ramach jednej z następujących standardowych nazwanych zestawów uprawnień:  
  
-   Średnie uprawnienia zaufania  
  
-   Uprawnień strefy Internet  
  
 Podjęto próbę użycia usługi WCF w częściowo zaufanych aplikacji przy użyciu bardziej restrykcyjne uprawnienia mogą spowodować wystąpienie wyjątków zabezpieczeń w czasie wykonywania.  
  
 Aby uzyskać więcej informacji na temat funkcji obsługiwanych w te zestawy uprawnień, zobacz [zgodność funkcji zaufania częściowego](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="partial-trust-on-the-server"></a>Częściowej relacji zaufania na serwerze  
 Wiele komercyjnych dostawców [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostowania aplikacji internetowych usług upoważnienie uruchamianą w aplikacje działające na serwerach w [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] trybie średniego zaufania zestawu uprawnień. Usługi WCF mogą być uruchamiane w tych środowiskach, pod warunkiem używają <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>, lub <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> z zabezpieczeniami na poziomie transportu.  
  
 Usługi WCF, uruchomiony w trybie średniego zaufania, środowiskach hostingu mogą również działać jako usługi warstwy środkowej przez wysyłanie komunikatów do innych serwerów w odpowiedzi na żądania klientów. Scenariusze warstwy środkowej na serwerze są obsługiwane, gdy środowisko hostingu przyznał aplikacji odpowiednie <xref:System.Net.WebPermission> na wysyłanie żądań wychodzących z serwerem.  
  
 Oprócz obsługi przy użyciu jednej z obsługiwanych powiązania protokołu SOAP wiadomości SOAP, obsługuje WCF <xref:System.ServiceModel.WebHttpBinding> do tworzenia usług internetowych w częściowo zaufanych aplikacji. [Modelu programowania protokołu HTTP sieci Web programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), i [JSON Obsługa integracji AJAX i](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) funkcji WCF jest obsługiwanych w częściowej relacji zaufania.  
  
 Usługi przepływu pracy wymaga uprawnień pełnego zaufania i nie można używać w częściowo zaufanych aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Użyj w trybie średniego zaufania w programie ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=84603).  
  
## <a name="partial-trust-on-the-client"></a>Częściowej relacji zaufania, na komputerze klienckim  
 Niektóre środki ostrożności zabezpieczeń należy podjąć w przypadku pobierania i uruchamiania kodu z niezaufanych witryn internetowych. Zarówno [wdrażania ClickOnce](https://go.microsoft.com/fwlink/?LinkId=83712) i [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]wprowadzić technologii XAML Browser aplikacji (XBAP) używania częściowej relacji zaufania przyznać ograniczone uprawnienia (strefy Internet) do niezaufanego kodu.  
  
 Usługi WCF może służyć do komunikacji z serwerami zdalnymi z w ramach częściowo zaufane aplikacje wdrożone przez [wdrażania ClickOnce](https://go.microsoft.com/fwlink/?LinkId=83712) lub XBAP. Obejmuje zestaw uprawnień strefy Internet <xref:System.Net.WebPermission> dla hosta źródłowego, co pozwala te aplikacje do komunikowania się z ich serwera pochodzenia przy użyciu dowolnej obsługiwanej wiązania WCF, opisane w [zgodność funkcji zaufania częściowego ](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia dostępu kodu](https://go.microsoft.com/fwlink/?LinkId=83717)
- [Windows Presentation Foundation aplikacje hostowane w przeglądarce Przegląd](https://go.microsoft.com/fwlink/?LinkId=98397)
- [Zaufanie częściowe](../../../../docs/framework/wcf/feature-details/partial-trust.md)
- [ASP.Net Medium Trust](https://go.microsoft.com/fwlink/?LinkId=69328)
