---
title: Punkty końcowe protokołów SOAP i HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: bf11563b937426c3c1701e7fed79e82e4e4669ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="soap-and-http-endpoints"></a>Punkty końcowe protokołów SOAP i HTTP
W tym przykładzie przedstawiono sposób implementacji usługi opartego na protokole RPC i udostępnić go w formacie protokołu SOAP i formatowanie "Zwykły starego pliku XML" (POX) przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania sieci Web. Zobacz [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) przykładowa, aby uzyskać więcej informacji o powiązanie HTTP dla usługi. Ten przykład dotyczy przede wszystkim szczegółowe informacje, które odnoszą się do udostępnianie tych samych usług za pośrednictwem protokołu SOAP i HTTP przy użyciu różnych powiązań.  
  
## <a name="demonstrates"></a>Demonstracje  
 Udostępnianie usługi RPC za pośrednictwem protokołu SOAP i HTTP przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="discussion"></a>Omówienie  
 Ten przykład zawiera dwa składniki: projekt aplikacji sieci Web (usługa), który zawiera [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług i aplikacji konsoli (klient), która wywołuje operacji usługi za pomocą powiązania SOAP i HTTP.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 2 operacje — udostępnia usługi`GetData` i `PutData` — która echo ciąg, który został przekazany jako dane wejściowe. Operacje usług są opatrzoną <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute>. Te atrybuty kontrolują projekcji HTTP z tych operacji. Ponadto mają adnotacje z <xref:System.ServiceModel.OperationContractAttribute>, co pozwala je, aby być uwidaczniany za pośrednictwem powiązania SOAP. Usługi `PutData` metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException>, które są wysyłane z powrotem przez serwer HTTP przy użyciu kodu stanu HTTP i są wysyłane z powrotem za pośrednictwem protokołu SOAP jako błąd protokołu SOAP.  
  
 Konfiguruje plik Web.config [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z punktami końcowymi 3:  
  
-   Punkt końcowy ~/service.svc/mex, który udostępnia metadane usługi dla dostępu klientów opartego na protokole SOAP.  
  
-   Punkt końcowy ~/service.svc/http, który umożliwia klientom dostęp do usługi za pomocą tego powiązania protokołu HTTP.  
  
-   Punkt końcowy ~/service.svc/soap, umożliwiający klientom dostęp do usługi przez powiązanie HTTP za pomocą protokołu SOAP.  
  
 Punkt końcowy HTTP jest skonfigurowany z <`webHttp`> Standardowy punkt końcowy, który ma `helpEnabled` ustawioną `true`. W związku z tym usługa przedstawia strona pomocy XHTML oparte na ~/service.svc/http/help używanego przez klientów oparte na protokole HTTP do uzyskania dostępu do usługi.  
  
 Projekt klienta demonstracja uzyskiwania dostępu do usługi przy użyciu serwera proxy protokołu SOAP (wygenerowane za pomocą **Dodaj odwołanie do usługi**) i uzyskiwania dostępu do usługi przy użyciu <xref:System.Net.WebClient>.  
  
 Próbka składa się z usługą hostowanych w sieci Web i aplikacji konsoli. Podczas działania aplikacji konsoli, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie SOAP i przykładowe punktów końcowych HTTP.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Jeśli go nie jest jeszcze otwarty, naciśnij kombinację klawiszy CTRL + W, S, aby otworzyć **Eksploratora rozwiązań** okna.  
  
4.  Z **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy **usługi** projektu, umieść kursor nad **debugowania** menu kontekstowego, aby **uruchomić nowy Wystąpienie** zostanie wyświetlone menu kontekstowego. Kliknij przycisk **uruchomić nowe wystąpienie**. Spowoduje to uruchomienie ASP.NET development server, który obsługuje usługę.  
  
5.  Eksplorator rozwiązań systemu Windows, kliknij prawym przyciskiem myszy projekt klienta i umieść kursor nad **debugowania** menu kontekstowego, aby **uruchomić nowe wystąpienie** zostanie wyświetlone menu kontekstowego. Kliknij przycisk **uruchomić nowe wystąpienie**.  
  
6.  Okno konsoli klienta pojawia się i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi. W dowolnym momencie można wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.  
  
7.  Jak działa próbki, klient zapisuje stan bieżącego działania.  
  
8.  Naciśnij dowolny klawisz, aby zakończyć działanie aplikacji konsoli klienta.  
  
9. Naciśnij klawisz SHIFT + F5, aby zatrzymać debugowanie usługi.  
  
10. W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę ASP.NET development serwera, a następnie wybierz **zatrzymać** z menu kontekstowego.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
