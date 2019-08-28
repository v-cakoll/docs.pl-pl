---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: f0c6cee2eb7ed9552452f95b71db7e942e84bcb0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044926"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Ten przykład pokazuje, jak utworzyć niestandardowy kanał protokołu, aby używać plików cookie protokołu HTTP do zarządzania sesją. Ten kanał umożliwia komunikację między usługami Windows Communication Foundation (WCF) i klientami ASMX lub między klientami programu WCF i usługami ASMX.  
  
 Gdy klient wywołuje metodę sieci Web w usłudze sieci Web ASMX, która jest oparta na sesji, aparat ASP.NET wykonuje następujące czynności:  
  
- Generuje unikatowy identyfikator (identyfikator sesji).  
  
- Generuje obiekt sesji i kojarzy go z unikatowym IDENTYFIKATORem.  
  
- Dodaje unikatowy identyfikator do nagłówka odpowiedzi HTTP Set-cookie i wysyła go do klienta.  
  
- Identyfikuje klienta podczas kolejnych wywołań w oparciu o identyfikator sesji, który wysyła do niego.  
  
 Klient dołącza ten identyfikator sesji do kolejnych żądań do serwera. Serwer używa identyfikatora sesji z klienta programu w celu załadowania odpowiedniego obiektu sesji dla bieżącego kontekstu HTTP.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Wzorzec wymiany komunikatów kanału HttpCookieSession  
 Ten przykład umożliwia korzystanie z sesji dla scenariuszy w przeciwieństwie do ASMX. W dolnej części stosu kanału korzystamy z transportu HTTP, który obsługuje <xref:System.ServiceModel.Channels.IRequestChannel> i. <xref:System.ServiceModel.Channels.IReplyChannel> Jest to zadanie kanału umożliwiające dostarczenie sesji do wyższych poziomów stosu kanału. Przykład implementuje dwa kanały (<xref:System.ServiceModel.Channels.IRequestSessionChannel> i <xref:System.ServiceModel.Channels.IReplySessionChannel>), które obsługują sesje.  
  
## <a name="service-channel"></a>Kanał usługi  
 Przykład zawiera kanał usługi w `HttpCookieReplySessionChannelListener` klasie. Ta klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener> interfejs i <xref:System.ServiceModel.Channels.IReplyChannel> konwertuje kanał z niższego poziomu w stosie kanału na <xref:System.ServiceModel.Channels.IReplySessionChannel>. Ten proces można podzielić na następujące części:  
  
- Gdy odbiornik kanału zostanie otwarty, akceptuje wewnętrzny kanał od jego wewnętrznego odbiornika. Ponieważ odbiornik wewnętrzny jest odbiornikiem datagramów, a okres istnienia zaakceptowanego kanału jest odłączony od okresu istnienia odbiornika, możemy zamknąć odbiornik wewnętrzny i zawiesić się tylko w kanale wewnętrznym  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- Po zakończeniu procesu otwierania należy skonfigurować pętlę komunikatów, aby odbierać komunikaty z kanału wewnętrznego.  
  
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
  
- Po nadejściu komunikatu kanał usługi bada identyfikator sesji i demultipleksery do odpowiedniego kanału sesji. Odbiornik kanału utrzymuje słownik, który mapuje identyfikatory sesji na wystąpienia kanału sesji.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` Klasa implementuje<xref:System.ServiceModel.Channels.IReplySessionChannel>. Wyższe poziomy stosu kanału wywołują <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodę odczytu żądania dla tej sesji. Każdy kanał sesji ma prywatną kolejkę komunikatów wypełnioną przez kanał usługi.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 W przypadku gdy ktoś wywołuje <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodę i nie ma żadnych komunikatów w kolejce komunikatów, kanał czeka przez określony czas przed zamknięciem samego siebie. Spowoduje to wyczyszczenie kanałów sesji utworzonych dla klientów nie korzystających z programu WCF.  
  
 Używamy `channelMapping` do `ReplySessionChannels`śledzenia i nie staramy się, aby nie zamykać `innerChannel` ich, dopóki nie zostaną zamknięte wszystkie zaakceptowane kanały. Ten sposób `HttpCookieReplySessionChannel` może występować poza `HttpCookieReplySessionChannelListener`okresem istnienia. Nie trzeba również martwić się o odbiornik odbierający elementy bezużyteczne ze względu na to, że zaakceptowane kanały zachowują odwołanie do `OnClosed` odbiornika za pomocą wywołania zwrotnego.  
  
## <a name="client-channel"></a>Kanał klienta  
 Odpowiedni kanał klienta znajduje się w `HttpCookieSessionChannelFactory` klasie. Podczas tworzenia kanału Fabryka kanałów otacza wewnętrzny kanał `HttpCookieRequestSessionChannel`żądania przez. `HttpCookieRequestSessionChannel` Klasa przekazuje wywołania do źródłowego kanału żądania. Gdy klient zamknie serwer proxy, `HttpCookieRequestSessionChannel` program wysyła do usługi komunikat informujący o tym, że kanał jest zamykany. W rezultacie stos kanału usługi może bezpiecznie zamknąć używany kanał sesji.  
  
## <a name="binding-and-binding-element"></a>Powiązanie i element powiązania  
 Następnym krokiem po utworzeniu kanałów usługi i klienta jest zintegrowanie ich ze środowiskiem uruchomieniowym WCF. Kanały są dostępne dla usługi WCF poprzez powiązania i elementy powiązania. Powiązanie składa się z jednego lub wielu elementów powiązania. Usługa WCF oferuje kilka powiązań zdefiniowanych przez system; na przykład BasicHttpBinding lub WSHttpBinding. `HttpCookieSessionBindingElement` Klasa zawiera implementację elementu Binding. Zastępuje on odbiornik kanału i metody tworzenia fabryki kanałów, aby wykonać niezbędne odbiorniki kanału lub fabryki kanałów.  
  
 Przykład używa potwierdzeń zasad dla opisu usługi. Dzięki temu przykładowi można opublikować wymagania dotyczące kanału dla innych klientów, którzy mogą korzystać z usługi. Na przykład ten element powiązania publikuje potwierdzenia zasad, aby umożliwić potencjalnym klientom znać, że obsługuje ona sesje. Ponieważ przykład włącza `ExchangeTerminateMessage` właściwość w konfiguracji elementu powiązania, dodaje niezbędne potwierdzenia, aby pokazać, że usługa obsługuje dodatkową akcję wymiany komunikatów, aby zakończyć konwersację sesji. Klienci mogą następnie użyć tej akcji. Poniższy kod WSDL przedstawia potwierdzenia zasad utworzone przy użyciu `HttpCookieSessionBindingElement`.  
  
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
  
 `HttpCookieSessionBinding` Klasa to powiązanie dostarczone z systemem, które używa wcześniej opisanego elementu Binding.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Dodawanie kanału do systemu konfiguracji  
 Przykład zawiera dwie klasy, które uwidaczniają przykładowego kanału za pośrednictwem konfiguracji. Pierwszy to a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> `HttpCookieSessionBindingElement`dla. Zbiorcza implementacja jest delegowana do `HttpCookieSessionBindingConfigurationElement`elementu, który pochodzi od. <xref:System.ServiceModel.Configuration.StandardBindingElement> Ma właściwości, które odpowiadają `HttpCookieSessionBindingElement`właściwościom. `HttpCookieSessionBindingConfigurationElement`  
  
### <a name="binding-element-extension-section"></a>Sekcja rozszerzenia elementu powiązania  
 Sekcja `HttpCookieSessionBindingElementSection` jest<xref:System.ServiceModel.Configuration.BindingElementExtensionElement> udostępniana`HttpCookieSessionBindingElement` systemowi konfiguracyjnemu. Za pomocą kilku zastąpień Nazwa sekcji konfiguracji, typ elementu powiązania oraz sposób tworzenia elementu powiązania są zdefiniowane. Następnie możemy zarejestrować sekcję rozszerzenia w pliku konfiguracji w następujący sposób:  
  
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
 Kod testowy służący do korzystania z tego przykładowego transportu jest dostępny w katalogach klienta i usług. Składa się z dwóch testów — jeden test używa powiązania z `allowCookies` `true` ustawionym na klienta. Drugi test umożliwia jawne zamknięcie (przy użyciu wymiany komunikatów zakończenia) dla powiązania.  
  
 Po uruchomieniu przykładu powinny zostać wyświetlone następujące dane wyjściowe:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
