---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 801fc6baed623c920e5a20163782bc9d6551a6da
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344497"
---
# <a name="httpcookiesession"></a>HttpCookieSession
W tym przykładzie przedstawiono sposób tworzenia kanału niestandardowego protokołu na używanie plików cookie protokołu HTTP do zarządzania sesjami. Ten kanał umożliwia komunikację między usług Windows Communication Foundation (WCF) i ASMX klientów lub między klientami programu WCF i usługami ASMX.  
  
 Kiedy klient wywołuje metody sieci Web w usłudze sieci Web ASMX, jest oparte na sesji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aparatu wykonuje następujące czynności:  
  
-   Generuje unikatowy identyfikator (identyfikator sesji).  
  
-   Generuje obiekt sesji i kojarzy ją z unikatowego identyfikatora.  
  
-   Dodaje nagłówek odpowiedzi HTTP Set-Cookie Unikatowy identyfikator i wysyła go do klienta.  
  
-   Identyfikuje klienta w kolejnych wywołaniach na podstawie Identyfikatora sesji, że wysyła do niego.  
  
 Klient dołącza ten identyfikator sesji, w jego kolejnych żądań do serwera. Serwer używa Identyfikatora sesji z klienta można załadować obiektu session odpowiednie dla bieżącego kontekstu HTTP.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Wymiany komunikatów HttpCookieSession kanału  
 Ten przykład umożliwia sesji dla scenariuszy ASMX podobne. W dolnej części naszego stosu kanału Mamy transportu HTTP, która obsługuje <xref:System.ServiceModel.Channels.IRequestChannel> i <xref:System.ServiceModel.Channels.IReplyChannel>. To zadanie kanału w celu zapewnienia sesji do wyższych poziomów stosu kanału. Przykład implementuje dwa kanały (<xref:System.ServiceModel.Channels.IRequestSessionChannel> i <xref:System.ServiceModel.Channels.IReplySessionChannel>) obsługujące sesji.  
  
## <a name="service-channel"></a>Kanał usługi  
 Przykład zawiera kanału usługi na `HttpCookieReplySessionChannelListener` klasy. Ta klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener> interfejsu i konwertuje <xref:System.ServiceModel.Channels.IReplyChannel> kanał z niższym stosie kanału do <xref:System.ServiceModel.Channels.IReplySessionChannel>. Ten proces można podzielić na następujące elementy:  
  
-   Po otwarciu odbiornika kanałów akceptuje kanał wewnętrzny z jego wewnętrznego odbiornika. Ponieważ wewnętrznego odbiornika jest odbiornika datagram i okresem istnienia kanał akceptowane rozdzielenie okres istnienia odbiornika, możesz zamknąć wewnętrznego odbiornika i przytrzymaj tylko do wewnętrznego kanału  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   Po ukończeniu procesu otwierania skonfigurujemy pętlę komunikatów do odbierania wiadomości z kanału wewnętrznego.  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   Po umieszczeniu komunikatu, kanału usługi sprawdza, czy identyfikator sesji i demultipleksowanie do kanału sesji odpowiednie. Odbiornik kanału zachowuje słownik, który mapuje identyfikatory sesji z wystąpieniami kanału sesji.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` Klasy implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel>. Wyższe poziomy kanału stosu wywołań <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodę w celu odczytania żądania dla tej sesji. Każdy kanału sesji ma prywatną kolejkę komunikatów, który jest wypełniana przez kanał usługi.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 W przypadku, gdy ktoś wywołuje <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metody i nie ma żadnych komunikatów w kolejce komunikatów, czeka określoną ilość czasu przed zamknięciem sam kanał. To spowoduje oczyszczenie kanały sesji dla klientów innych niż WCF.  
  
 Używamy `channelMapping` do śledzenia `ReplySessionChannels`, i firma Microsoft nie zamykaj naszych podstawowych `innerChannel` dopóki nie zostały zamknięte zaakceptowanych kanałów. W ten sposób `HttpCookieReplySessionChannel` może znajdować się poza okres istnienia `HttpCookieReplySessionChannelListener`. Firma Microsoft nie mają też martwić się o odbiornika wprowadzenie bezużyteczne poniżej nam, ponieważ zaakceptowanych kanałów utrzymywać odwołania do ich za pośrednictwem połączenia z odbiornikiem `OnClosed` wywołania zwrotnego.  
  
## <a name="client-channel"></a>Kanału klienta  
 Odpowiednie kanału klienta znajduje się w `HttpCookieSessionChannelFactory` klasy. Podczas tworzenia kanału fabryki kanałów opakowuje kanał wewnętrzny żądania z `HttpCookieRequestSessionChannel`. `HttpCookieRequestSessionChannel` Klasy przekazuje wywołania do kanału źródłowego żądania. Gdy klient zamyka serwera proxy, `HttpCookieRequestSessionChannel` wysyła komunikat do usługi, która wskazuje, że kanał jest zamknięty. W związku z tym stos kanału usługi mogą bez problemu zmieniała zamykania kanału sesji, który jest używany.  
  
## <a name="binding-and-binding-element"></a>Powiązanie i Element powiązania  
 Po utworzeniu kanały usługi i klienta, następnym krokiem jest zintegrować środowisko wykonawcze programu WCF. Kanały są udostępniane do programu WCF za pomocą powiązania i elementy powiązań. Powiązanie składa się z jednego lub wielu elementów powiązania. Usługi WCF oferuje kilka powiązań zdefiniowanych przez system; na przykład BasicHttpBinding lub WSHttpBinding. `HttpCookieSessionBindingElement` Klasa zawiera implementację elementu powiązania. Zastępuje ona odbiornika kanałów i metod tworzenia fabryki kanału wykonaj konieczne kanału wystąpień fabryki odbiornika lub kanału.  
  
 W przykładzie użyto asercji zasad opisu usługi. Dzięki temu próbki do publikowania swoich wymagań dotyczących kanału inni klienci, którzy mogą korzystać z usługi. Na przykład ten element powiązania publikuje asercji zasad, aby umożliwić potencjalnych klientów, o których wiadomo, że obsługuje ona sesji. Ponieważ próbki pozwala `ExchangeTerminateMessage` właściwości w konfiguracji elementu powiązania, dodaje niezbędne potwierdzenia, aby pokazać, że usługa obsługuje akcję exchange dodatkowych komunikatów, aby zakończyć sesję rozmowy. Klienci mogą następnie używać tej akcji. Poniższy kod WSDL przedstawia asercji zasad utworzone na podstawie `HttpCookieSessionBindingElement`.  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 `HttpCookieSessionBinding` Klasa jest powiązania dostarczane przez system, które używa elementu powiązania opisanych powyżej.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Dodawanie kanał do systemu konfiguracji  
 Przykład zawiera dwie klasy, które ujawniają kanału przykładowej konfiguracji. Pierwsza to <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> dla `HttpCookieSessionBindingElement`. Duża część wykonania jest delegowane do `HttpCookieSessionBindingConfigurationElement`, która jest pochodną <xref:System.ServiceModel.Configuration.StandardBindingElement>. `HttpCookieSessionBindingConfigurationElement` Ma właściwości, które odnoszą się do właściwości `HttpCookieSessionBindingElement`.  
  
### <a name="binding-element-extension-section"></a>Powiązania elementu rozszerzenia sekcji  
 Sekcja `HttpCookieSessionBindingElementSection` jest <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> który uwidacznia `HttpCookieSessionBindingElement` systemu konfiguracji. Za pomocą kilku przesłonięcia nazwa sekcji konfiguracji, typem elementu powiązania i jak można utworzyć elementu powiązania są zdefiniowane. Firma Microsoft może następnie zarejestruj sekcji rozszerzenia w pliku konfiguracji w następujący sposób:  
  
```xml  
<configuration>        
    <system.serviceModel>        
      <extensions>          
        <bindingElementExtensions>            
          <add name="httpCookieSession"   
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,   
                    HttpCookieSessionExtension, Version=1.0.0.0,   
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>        
    </system.serviceModel>    
</configuration>  
```  
  
## <a name="test-code"></a>Kod testu  
 Za pomocą transportu ten przykładowy kod testu jest dostępne w podkatalogach klienta i usługi. Składa się z dwóch testów — jeden test używa wiązania za pomocą `allowCookies` równa `true` na komputerze klienckim. Drugi test umożliwia jawne zamknięcia (przy użyciu Zakończ wymianę komunikatów) w powiązaniu.  
  
 Po uruchomieniu przykładu, powinny pojawić się następujące dane wyjściowe:  
  
```  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
