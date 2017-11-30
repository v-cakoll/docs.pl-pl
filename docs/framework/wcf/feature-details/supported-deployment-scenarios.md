---
title: "Obsługiwane scenariusze wdrażania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22dcace51b2c73193356450b4b210d1c1a899e28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="supported-deployment-scenarios"></a>Obsługiwane scenariusze wdrażania
Podzbiór [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcje obsługiwane w przypadku użycia w częściowo zaufane aplikacje zaprojektowano w celu spełnienia wymagań niektórych, ale nie wszystkie scenariusze korzystania z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Na serwerze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spełnia wymagania dotyczące skali Internet udostępnionych dostawców usług hostingu, którzy korzystają z aplikacji innych firm w [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] trybie średniego zaufania uprawnienia ze względów bezpieczeństwa. Na komputerze klienckim [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obsługa częściowej relacji zaufania zaprojektowano w celu spełnienia wymagań wdrażania technologii, takich jak [wdrażania ClickOnce](http://go.microsoft.com/fwlink/?LinkId=83712) lub [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]w technologii aplikacja przeglądarki XAML, który umożliwia bezproblemową i bezpieczne wdrożenie aplikacji klasycznych z niezaufanej lokacji.  
  
## <a name="minimum-permission-requirements"></a>Wymagania dotyczące minimalnych uprawnień  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje podzbiór funkcji aplikacji uruchomionych w jednej z następujących zestawów standardowe uprawnienie o nazwie:  
  
-   Średnia uprawnień zaufania  
  
-   Uprawnienia strefy Internet  
  
 Podjęto próbę użycia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w częściowo zaufane aplikacje z bardziej restrykcyjnymi uprawnieniami może spowodować wystąpienie wyjątków zabezpieczeń w czasie wykonywania.  
  
 Aby uzyskać więcej informacji o funkcji obsługiwanych w tych zestawów uprawnień, zobacz [zgodność funkcji zaufania częściowego](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="partial-trust-on-the-server"></a>Częściowa relacja zaufania na serwerze  
 Wielu dostawców komercyjnych [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] obsługiwania aplikacji sieci Web usług upoważnienia uruchomienia aplikacji działających na serwerach w [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] zestaw uprawnień trybie średniego zaufania. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usługi mogą być uruchamiane w tych środowiskach, pod warunkiem używają <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WebHttpBinding>, lub <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> z zabezpieczeniami na poziomie transportu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usługi uruchomione w trybie średniego zaufania środowiskach hostingu mogą również działać jako usługi warstwy środkowej przez wysłanie wiadomości na inne serwery w odpowiedzi na żądania klientów. Scenariusze warstwy środkowej na serwerze są obsługiwane, jeśli środowisko macierzyste udzieliło aplikacji odpowiednie <xref:System.Net.WebPermission> na wysyłanie ruchu wychodzącego żądań z serwerem.  
  
 Oprócz obsługi wiadomości SOAP przy użyciu jednego z obsługiwanych powiązania SOAP, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje <xref:System.ServiceModel.WebHttpBinding> do tworzenia usług sieci Web stylu w częściowo zaufane aplikacje. [Modelu programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md), [syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md), i [integracji AJAX i obsługi JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md) funkcji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są obsługiwane w częściowej relacji zaufania.  
  
 Usługi przepływu pracy wymaga uprawnień pełnego zaufania i nie można używać w częściowo zaufane aplikacje.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Użyj trybie średniego zaufania w programie ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=84603).  
  
## <a name="partial-trust-on-the-client"></a>Częściowa relacja zaufania na kliencie  
 Należy podjąć pewne środki ostrożności podczas pobierania i uruchamiania kod z niezaufanej witryn internetowych. Zarówno [wdrażania ClickOnce](http://go.microsoft.com/fwlink/?LinkId=83712) i [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]XAML przeglądarki aplikacji (XBAP), wprowadź technologii używania częściowej relacji zaufania do przyznawania uprawnień ograniczone (strefy internetowej) kodzie niezaufanym.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]może służyć do komunikacji z serwerami zdalnymi z wewnątrz częściowo zaufane aplikacje wdrożone przez [wdrażania ClickOnce](http://go.microsoft.com/fwlink/?LinkId=83712) lub XBAP. Obejmuje zestaw uprawnień strefy internetowej <xref:System.Net.WebPermission> dla hosta źródłowego, dzięki czemu te aplikacje do komunikowania się z ich serwera pochodzenia przy użyciu dowolnego z obsługiwanych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania opisanego w [funkcji zaufania częściowego Zgodność](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia dostępu kodu](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Omówienie aplikacje obsługiwane w przeglądarce Windows Presentation Foundation](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [Częściowa relacja zaufania](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [Średnia liczba godzin ASP.Net zaufania](http://go.microsoft.com/fwlink/?LinkId=69328)
