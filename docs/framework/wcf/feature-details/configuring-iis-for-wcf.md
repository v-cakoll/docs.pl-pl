---
title: "Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 511f5177e1b9d2660daf887cc13728aed2c9de0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation
Internet informacji Services (IIS) 7.0 ma modularny projekt, który umożliwia selektywną instalację składników, które są wymagane. Ten projekt jest oparta na nową technologią componentization oparte na manifest w [!INCLUDE[wv](../../../../includes/wv-md.md)]. Istnieje więcej niż 40 autonomiczny składników funkcji [!INCLUDE[iisver](../../../../includes/iisver-md.md)] instalowane niezależnie. Dzięki temu specjalistów IT łatwo dostosować instalacji zgodnie z wymaganiami. W tym temacie omówiono sposób konfigurowania [!INCLUDE[iisver](../../../../includes/iisver-md.md)] do użytku z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i określić, które składniki są wymagane.  
  
## <a name="minimal-installation-installing-was"></a>Minimalnej instalacji: Usługa WAS instalowanie  
 Minimalnej instalacji całego [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest pakiet do zainstalowania usługi aktywacji procesów systemu Windows (WAS). Funkcja autonomicznych i jest jedyną funkcją z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] dostępnej dla wszystkich [!INCLUDE[wv](../../../../includes/wv-md.md)] systemów operacyjnych (Home Basic, Home Premium, Business i Ultimate i Enterprise).  
  
 W Panelu sterowania kliknij **programy** , a następnie kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows** wymienione w obszarze **programy i funkcje**, składnik WAS jest wyświetlany w obszarze Lista, jak pokazano na poniższej ilustracji.  
  
 ![Włączanie funkcji lub Wyłącz okno dialogowe](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")  
  
 Ta funkcja zawiera następujące składniki podrzędne:  
  
-   Środowisko .NET  
  
-   Konfiguracyjne interfejsy API  
  
-   Model procesów  
  
 Jeśli wybierzesz węzeł główny WAS, tylko **Model procesu** węzła podrzędnego jest domyślnie zaznaczone. Należy pamiętać, że z tą instalacją tylko instalujesz WAS, ponieważ nie jest obsługiwane dla serwera sieci Web.  
  
 Aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lub [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji do pracy, sprawdź **środowiska .NET** wyboru. Oznacza to, że wszystkie składniki WAS są wymagane dokonanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] działał prawidłowo. Te automatycznie sprawdza, czy po zainstalowaniu dowolnego z tych składników.  
  
## <a name="iis-70-default-installation"></a>Usługi IIS 7.0: Domyślna instalacja  
 Sprawdzając **Internetowe usługi informacyjne** funkcji, niektóre węzły podrzędne są automatycznie sprawdzane, jak pokazano na poniższej ilustracji.  
  
 ![Domyślne ustawienia funkcji usług IIS 7.0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")  
  
 Jest to domyślna instalacja [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. W tej instalacji, możesz użyć [!INCLUDE[iisver](../../../../includes/iisver-md.md)] na zawartość statyczną usług (takich jak strony HTML i innej zawartości). Jednak nie można uruchomić [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] lub aplikacji CGI lub hosta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług.  
  
## <a name="iis-70-installation-with-aspnet-support"></a>Usług IIS 7.0: Instalacja z obsługą platformy ASP.NET  
 Musisz zainstalować [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dokonanie [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pracy w programie IIS 7.0. Po sprawdzeniu **ASP.NET**, na ekranie powinna wyglądać podobnie do poniższej ilustracji.  
  
 ![Asp.NET wymagane ustawienia](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")  
  
 Jest to minimalne środowisko dla obu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] działania aplikacji [!INCLUDE[iisver](../../../../includes/iisver-md.md)].  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>Usług IIS 7.0: Instalacja z składników usług IIS 6.0 zgodności  
 Podczas instalowania [!INCLUDE[iisver](../../../../includes/iisver-md.md)] w systemie z programu Visual Studio 2005 lub niektórych skryptów automatyzacji lub narzędzia (na przykład Adsutil.vbs), które konfigurują aplikacje wirtualne, które używają [!INCLUDE[iis601](../../../../includes/iis601-md.md)] metabazy interfejsu API, upewnij się, że sprawdzać [!INCLUDE[iis601](../../../../includes/iis601-md.md)]  **Narzędzia do tworzenia skryptów**. Automatycznie sprawdza inne węzły podrzędne elementu [!INCLUDE[iis601](../../../../includes/iis601-md.md)] **zgodność z narzędziami zarządzania**. Na poniższej ilustracji przedstawiono ekranu po odbywa się.  
  
 ![Ustawienia zgodności usług IIS 6.0 zarządzania](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")  
  
 W tej instalacji, masz wszystko, co jest wymagane do użycia [!INCLUDE[iisver](../../../../includes/iisver-md.md)], [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje i przykłady w sieci Web.  
  
## <a name="request-limits"></a>Limity żądań  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] z usług IIS 7 wartości domyślnej z `maxUri` i `maxQueryStringSize` ustawienia zostały zmienione. Domyślnie filtrowania żądań w usługach IIS 7.0 umożliwia długość adresu URL, liczbę znaków równą 4096 i długości ciągu zapytania 2048 znaków. Aby zmienić te ustawienia domyślne, należy dodać następujące XML do pliku App.config.  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura aktywacji WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [Konfigurowanie usługi WAS do użycia z programem WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Instrukcje: instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
