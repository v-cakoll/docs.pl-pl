---
title: Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 13fd068f7a058a0fbf4e15fc99a8de91671fb2d5
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664621"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation

Usług informacje internetowe (IIS) 7.0 ma modułowej, która umożliwia selektywną instalację składników, które są wymagane. Projekt będzie opierać się na nowej technologii oparte na manifeście componentization wprowadzona w [!INCLUDE[wv](../../../../includes/wv-md.md)]. Istnieje więcej niż 40 autonomiczny składników funkcji usług IIS 7.0, którą można zainstalować niezależnie. Dzięki temu specjaliści IT mogą więc łatwo dostosować instalację zgodnie z potrzebami. W tym temacie omówiono sposób konfigurowania usług IIS 7.0 do użycia przy użyciu programu Windows Communication Foundation (WCF) i określić, które składniki są wymagane.

## <a name="minimal-installation-installing-was"></a>Minimalnej instalacji: Instalowanie WAS
 Minimalnej instalacji cały pakiet usług IIS 7.0 polega na zainstalowaniu Windows Process Activation Service (WAS). BYŁ to funkcja autonomiczne i jest jedyną funkcją z usług IIS 7.0, który jest dostępny dla wszystkich [!INCLUDE[wv](../../../../includes/wv-md.md)] systemów operacyjnych (Home Basic, Home Premium, firm i Ultimate i Enterprise).

 W Panelu sterowania kliknij **programy** a następnie kliknij przycisk **Windows Włącz lub wyłącz funkcje** wymienionych w obszarze **programy i funkcje**, składnik WAS jest wyświetlany w Lista, tak jak na poniższej ilustracji.

 ![Włączanie funkcji lub wyłącz okna dialogowego](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 Ta funkcja obejmuje następujące składniki podrzędne:

-   Środowisko .NET

-   Interfejsy API konfiguracji

-   Model procesów

 Jeśli wybierzesz węzeł główny WAS, tylko **Model procesu** węzeł podrzędny jest zaznaczone domyślnie. Należy pamiętać, że tej instalacji tylko instalacja WAS, ponieważ nie jest obsługiwane dla serwera sieci Web.

 Aby upewnić się, WCF i wszelkie prace aplikacji ASP.NET, sprawdź **środowiska .NET** pola wyboru. Oznacza to, czy wszystkie składniki WAS wymagane dokonanie WCF i platforma ASP.NET, aby działać prawidłowo. Są one automatycznie sprawdzane, po zainstalowaniu dowolnego z tych składników.

## <a name="iis-70-default-installation"></a>Usługi IIS 7.0: Instalacja domyślna
 Sprawdzając **Internetowe usługi informacyjne** funkcji, niektóre węzły podrzędne są automatycznie sprawdzane, jak pokazano na poniższej ilustracji.

 ![Domyślne ustawienia funkcji usług IIS 7.0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 Jest to domyślna instalacja usług IIS 7.0. Za pomocą tej instalacji usług IIS 7.0 służy również do zawartości statycznej usługi (takie jak strony HTML i innej zawartości). Jednak nie można uruchomić aplikacji ASP.NET i CGI lub hosta usługi WCF.

## <a name="iis-70-installation-with-aspnet-support"></a>Usługi IIS 7.0: Instalacji z obsługą platformy ASP.NET
 Należy zainstalować program ASP.NET, aby ASP.NET działa przez usługi IIS 7.0. Po sprawdzeniu **ASP.NET**, ekran powinien wyglądać podobnie do poniższej ilustracji.

 ![Asp.NET wymagane ustawienia](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 Jest to minimalne środowisko dla aplikacji ASP.NET i WCF do pracy w usługach IIS 7.0.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>Usługi IIS 7.0: Instalacji za pomocą usług IIS 6.0 zgodności składników
 Podczas instalowania usług IIS 7.0 w systemie przy użyciu programu Visual Studio 2005 lub niektóre skrypty automatyzacji lub narzędzia (takie jak Adsutil.vbs), skonfigurowanych przez wirtualne aplikacje, które używają interfejsu API programu IIS 6.0 metabazy, upewnij się, sprawdzenie, czy usługi IIS 6.0 **narzędzia obsługi skryptów**. To automatycznie sprawdza, czy innych węzłów podrzędnych usług IIS 6.0 **zgodność z narzędziami zarządzania**. Na poniższej ilustracji przedstawiono ekran po tej operacji:

 ![Ustawienia zgodności programu IIS 6.0 zarządzania](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 Dzięki tej instalacji masz wszystko, co jest wymagane, aby korzystać z funkcji usług IIS 7.0, ASP.NET i WCF i przykładów dostępnych w sieci Web.

## <a name="request-limits"></a>Limity żądań
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] za pomocą usług IIS 7, wartość domyślna elementu `maxUri` i `maxQueryStringSize` ustawienia zostały zmienione. Domyślnie filtrowania żądań w usługach IIS 7.0 umożliwia długości adresu URL 4096 znaków i długość ciągu zapytania, 2048 znaków. Aby zmienić te ustawienia domyślne, należy dodać następujący kod XML do pliku App.config.

 `<system.webServer>`

 `<security>`

 `<requestFiltering>`

 `<requestLimits maxUrl="8192" maxQueryString="8192" />`

 `</requestFiltering>`

 `</security>`

 `</system.webServer>`

## <a name="see-also"></a>Zobacz też

- [Architektura aktywacji WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [Konfigurowanie usługi WAS do użycia z programem WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Instrukcje: instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
