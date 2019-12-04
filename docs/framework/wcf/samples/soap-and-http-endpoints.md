---
title: Punkty końcowe protokołów SOAP i HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 93f410b8b8632b0158d0a52b12845f1e8cec132c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716683"
---
# <a name="soap-and-http-endpoints"></a>Punkty końcowe protokołów SOAP i HTTP
Ten przykład pokazuje, jak wdrożyć usługę opartą na protokole RPC i udostępnić ją w formacie protokołu SOAP oraz formacie "zwykły stary kod XML" (POX) przy użyciu modelu programowania sieci Web WCF. Zapoznaj się z przykładem [podstawowej usługi http](../../../../docs/framework/wcf/samples/basic-http-service.md) , aby uzyskać więcej informacji na temat powiązania HTTP dla usługi. Ten przykład koncentruje się na szczegółach odnoszących się do ujawnienia tej samej usługi za pośrednictwem protokołów SOAP i HTTP przy użyciu różnych powiązań.  
  
## <a name="demonstrates"></a>Przedstawia  
 Uwidacznianie usługi RPC za pośrednictwem protokołu SOAP i protokołu HTTP przy użyciu programu WCF.  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład składa się z dwóch składników: projektu aplikacji sieci Web (usługi), który zawiera usługę WCF i aplikację konsoli (klienta), która wywołuje operacje usługi przy użyciu powiązań protokołu SOAP i HTTP.  
  
 Usługa WCF uwidacznia 2 operacje —`GetData` i `PutData` — ciąg, który został przesłany jako dane wejściowe. Operacje usługi są z adnotacjami <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute>. Te atrybuty kontrolują projekcję HTTP tych operacji. Ponadto są adnotacjami z <xref:System.ServiceModel.OperationContractAttribute>, co umożliwia ich uwidocznienie za pośrednictwem powiązań protokołu SOAP. Metoda `PutData` usługi zgłasza <xref:System.ServiceModel.Web.WebFaultException>, które są wysyłane z powrotem za pośrednictwem protokołu HTTP przy użyciu kodu stanu HTTP i pobiera z powrotem za pośrednictwem protokołu SOAP jako błąd protokołu SOAP.  
  
 Plik Web. config konfiguruje usługę WCF z trzema punktami końcowymi:  
  
- Punkt końcowy/Service.svc/Mex, który uwidacznia metadane usługi dla dostępu przez klientów opartych na protokole SOAP.  
  
- /Service.svc/http punkt końcowy, który umożliwia klientom dostęp do usługi przy użyciu powiązania HTTP.  
  
- /Service.svc/SOAP punkt końcowy, który umożliwia klientom dostęp do usługi przy użyciu powiązania protokołu SOAP over HTTP.  
  
 Punkt końcowy HTTP jest skonfigurowany przy użyciu <`webHttp`> standardowego punktu końcowego, który ma `helpEnabled` ustawiony na `true`. W związku z tym usługa uwidacznia stronę pomocy opartą na XHTML w lokalizacji ~/Service.svc/http/help, że klienci korzystający z protokołu HTTP mogą uzyskać dostęp do usługi.  
  
 Projekt klienta pokazuje dostęp do usługi przy użyciu serwera proxy SOAP (generowanego za pośrednictwem **Dodaj odwołanie do usługi**) i uzyskując dostęp do usługi przy użyciu <xref:System.Net.WebClient>.  
  
 Przykład składa się z usługi hostowanej w sieci Web i aplikacji konsolowej. Gdy aplikacja konsolowa zostanie uruchomiona, klient wysyła żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi do okna konsoli.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1. Otwórz rozwiązanie dla przykładu punktów końcowych protokołu SOAP i HTTP.  
  
2. Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
3. Jeśli nie jest jeszcze otwarty, naciśnij klawisze CTRL + W, aby otworzyć okno **Eksplorator rozwiązań** .  
  
4. W oknie **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **usługi** i umieść kursor nad opcją menu kontekstowego **debugowania** , aby pojawiło się menu kontekstowe **Uruchom nowe wystąpienie** . Kliknij przycisk **Uruchom nowe wystąpienie**. Spowoduje to uruchomienie serwera deweloperskiego ASP.NET, który jest hostem usługi.  
  
5. W Eksplorator rozwiązań Windows, kliknij prawym przyciskiem myszy projekt klienta i umieść kursor nad opcją menu kontekstowego **debugowania** , aby pojawiło się menu kontekstowe **Uruchom nowe wystąpienie** . Kliknij przycisk **Uruchom nowe wystąpienie**.  
  
6. Zostanie wyświetlone okno konsoli klienta z identyfikatorem URI uruchomionej usługi oraz identyfikatorem URI strony pomocy HTML dla działającej usługi. W dowolnym momencie możesz wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.  
  
7. W miarę uruchamiania przykładu klient zapisuje stan bieżącego działania.  
  
8. Naciśnij dowolny klawisz, aby zakończyć aplikację konsolową klienta.  
  
9. Naciśnij klawisze SHIFT + F5, aby zatrzymać debugowanie usługi.  
  
10. W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę ASP.NET Development Server i wybierz polecenie **stop** z menu kontekstowego.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
