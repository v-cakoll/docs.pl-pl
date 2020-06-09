---
title: Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 6343049e2a21b06965a8c7851d891303a49c82b5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597569"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation

Internet Information Services (IIS) 7,0 ma modularny projekt, który umożliwia selektywne instalowanie składników, które są wymagane. Ten projekt jest oparty na nowej technologii componentization opartej na manifestach wprowadzonej w systemie Windows Vista. Istnieje ponad 40 autonomicznych składników funkcji usług IIS 7,0, które mogą być instalowane niezależnie. Dzięki temu specjaliści IT mogą łatwo dostosować instalację zgodnie z potrzebami. W tym temacie omówiono sposób konfigurowania usług IIS 7,0 do użycia z programem Windows Communication Foundation (WCF) i określania, które składniki są wymagane.

## <a name="minimal-installation-installing-was"></a>Minimalna instalacja: Instalacja została
 Minimalna instalacja całego pakietu usług IIS 7,0 to zainstalowanie usługi aktywacji procesów systemu Windows (WAS). BYŁA funkcją autonomiczną i jest jedyną funkcją z usług IIS 7,0, która jest dostępna dla wszystkich systemów operacyjnych Windows Vista (Home Basic, Home Premium, Business i Ultimate i Enterprise).

 W panelu sterowania kliknij pozycję **programy** , a następnie kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows** , które są wyświetlane w obszarze **programy i funkcje**, składnik został wyświetlony na liście tak jak na poniższej ilustracji.

 ![Włącz lub wyłącz funkcje okna dialogowego](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 Ta funkcja ma następujące składniki podrzędne:

- Środowisko .NET

- Interfejsy API konfiguracji

- Model procesów

 W przypadku wybrania węzła głównego elementu, domyślnie sprawdzany jest tylko podrzędny węzeł **modelu procesu** . Należy pamiętać, że instalacja jest przeprowadzana tylko w przypadku instalacji, ponieważ nie ma żadnych obsługi dla serwera sieci Web.

 Aby program WCF lub dowolna aplikacja ASP.NET działała, zaznacz pole wyboru **środowisko .NET** . Oznacza to, że wszystkie składniki były wymagane do poprawnego działania usług WCF i ASP.NET. Są one automatycznie sprawdzane po zainstalowaniu któregokolwiek z tych składników.

## <a name="iis-70-default-installation"></a>IIS 7,0: Instalacja domyślna
 Sprawdzając funkcję **Internet Information Services** , niektóre węzły podrzędne są automatycznie sprawdzane, jak pokazano na poniższej ilustracji.

 ![Ustawienia domyślne dla funkcji usług IIS 7,0](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 Jest to domyślna instalacja usług IIS 7,0. Za pomocą tej instalacji można używać usług IIS 7,0 do obsługi zawartości statycznej (takiej jak strony HTML i inna zawartość). Nie można jednak uruchamiać aplikacji ASP.NET ani CGI ani hostować usług WCF.

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7,0: Instalacja z obsługą ASP.NET
 Aby ASP.NET działały w usługach IIS 7,0, należy zainstalować ASP.NET. Po sprawdzeniu **ASP.NET**ekran powinien wyglądać jak na poniższej ilustracji.

 ![Asp.NET wymagane ustawienia](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 Jest to minimalne środowisko dla aplikacji WCF i ASP.NET, które działają w usługach IIS 7,0.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7,0: Instalacja ze składnikami zgodności usług IIS 6,0
 Podczas instalowania usług IIS 7,0 w systemie z programem Visual Studio 2005 lub innymi skryptami lub narzędziami automatyzacji (na przykład Adsutil. vbs), które konfigurują aplikacje wirtualne korzystające z interfejsu API metabazy usług IIS 6,0, upewnij się, że zaznaczono **Narzędzia do obsługi skryptów**6,0 IIS. Spowoduje to automatyczne sprawdzenie innych podrzędnych węzłów **zgodności zarządzania**usług IIS 6,0. Na poniższej ilustracji przedstawiono ekran po wykonaniu tej czynności:

 ![Ustawienia zgodności zarządzania usługami IIS 6,0](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 W przypadku tej instalacji masz wszystko, co jest wymagane do korzystania z usług IIS 7,0, ASP.NET i funkcji WCF oraz przykładów dostępnych w sieci Web.

## <a name="request-limits"></a>Limity żądań
 W systemie Windows Vista z usługami IIS 7 wartość domyślna `maxUri` ustawień i `maxQueryStringSize` została zmieniona. Domyślnie Filtrowanie żądań w usługach IIS 7,0 zezwala na długość adresu URL 4096 znaków i długość ciągu zapytania wynoszącą 2048 znaków. Aby zmienić te ustawienia domyślne, Dodaj następujący kod XML do pliku App. config.

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a>Zobacz też

- [Architektura aktywacji WAS](was-activation-architecture.md)
- [Konfigurowanie usługi WAS do użycia z programem WCF](configuring-the-wpa--service-for-use-with-wcf.md)
- [Instrukcje: instalowanie i konfigurowanie składników aktywacji programu WCF](how-to-install-and-configure-wcf-activation-components.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
