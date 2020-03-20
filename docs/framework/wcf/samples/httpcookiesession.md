---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 6b7a72fdd814aa9d2e0f125cf4dbdaf63ba753e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183627"
---
# <a name="httpcookiesession"></a>HttpCookieSession
W tym przykładzie pokazano, jak utworzyć niestandardowy kanał protokołu do używania plików cookie HTTP do zarządzania sesjami. Ten kanał umożliwia komunikację między usługami Windows Communication Foundation (WCF) a klientami ASMX lub między klientami WCF a usługami ASMX.  
  
 Gdy klient wywołuje metodę sieci Web w usłudze sieci Web ASMX opartą na sesji, aparat ASP.NET wykonuje następujące czynności:  
  
- Generuje unikatowy identyfikator (identyfikator sesji).  
  
- Generuje obiekt sesji i kojarzy go z unikatowym identyfikatorem.  
  
- Dodaje unikatowy identyfikator do nagłówka odpowiedzi HTTP set-cookie i wysyła go do klienta.  
  
- Identyfikuje klienta na kolejnych wywołaniach na podstawie identyfikatora sesji, który wysyła do niego.  
  
 Klient zawiera ten identyfikator sesji w kolejnych żądaniach do serwera. Serwer używa identyfikatora sesji od klienta, aby załadować odpowiedni obiekt sesji dla bieżącego kontekstu HTTP.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Wzorzec wymiany komunikatów kanału HttpCookieSession  
 Ten przykład umożliwia sesje dla scenariuszy podobnych do ASMX. W dolnej części naszego stosu kanałów <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IReplyChannel>mamy transport HTTP, który obsługuje i . Zadaniem kanału jest zapewnienie sesji do wyższych poziomów stosu kanału. Przykład implementuje dwa kanały (<xref:System.ServiceModel.Channels.IRequestSessionChannel> i <xref:System.ServiceModel.Channels.IReplySessionChannel>), które obsługują sesje.  
  
## <a name="service-channel"></a>Kanał usługi  
 Przykład zapewnia kanał usługi `HttpCookieReplySessionChannelListener` w klasie. Ta klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener> interfejs i <xref:System.ServiceModel.Channels.IReplyChannel> konwertuje kanał z <xref:System.ServiceModel.Channels.IReplySessionChannel>dolnej w stosie kanału na . Proces ten można podzielić na następujące części:  
  
- Po otwarciu odbiornika kanału, akceptuje kanał wewnętrzny z jego odbiornika wewnętrznego. Ponieważ wewnętrzny odbiornik jest odbiornikiem datagramu, a okres istnienia akceptowanego kanału jest oddzielony od okresu istnienia odbiornika, możemy zamknąć odbiornik wewnętrzny i trzymać tylko kanał wewnętrzny  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- Po zakończeniu otwartego procesu skonfigurujemy pętlę komunikatów do odbierania wiadomości z kanału wewnętrznego.  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- Po odebraniu wiadomości kanał usługi sprawdza identyfikator sesji i de-multipleksy do odpowiedniego kanału sesji. Odbiornik kanału przechowuje słownik, który mapuje identyfikatory sesji do wystąpień kanału sesji.  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 Klasa `HttpCookieReplySessionChannel` implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel>. Wyższe poziomy stosu kanału <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> wywołać metodę odczytu żądań dla tej sesji. Każdy kanał sesji ma prywatną kolejkę komunikatów, która jest wypełniona przez kanał usługi.  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 W przypadku, gdy <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> ktoś wywołuje metodę i nie ma żadnych wiadomości w kolejce wiadomości, kanał czeka na określoną ilość czasu przed zamknięciem się. Spowoduje to oczyszczenie kanałów sesji utworzonych dla klientów innych niż WCF.  
  
 Używamy `channelMapping` do śledzenia `ReplySessionChannels`, i nie zamykamy `innerChannel` naszych podstawowych, dopóki wszystkie akceptowane kanały zostały zamknięte. W `HttpCookieReplySessionChannel` ten sposób może `HttpCookieReplySessionChannelListener`istnieć poza okresem istnienia . Nie musimy się również martwić o słuchacza coraz śmieci zebrane pod nami, ponieważ akceptowane `OnClosed` kanały zachować odniesienie do ich słuchacza poprzez wywołanie zwrotne.  
  
## <a name="client-channel"></a>Kanał klienta  
 Odpowiedni kanał klienta znajduje `HttpCookieSessionChannelFactory` się w klasie. Podczas tworzenia kanału fabryka kanału zawija `HttpCookieRequestSessionChannel`wewnętrzny kanał żądania za pomocą pliku . Klasa `HttpCookieRequestSessionChannel` przekazuje wywołania do kanału żądania źródłowego. Gdy klient zamyka serwer `HttpCookieRequestSessionChannel` proxy, wysyła komunikat do usługi, który wskazuje, że kanał jest zamykany. W związku z tym stos kanału usługi można bezpiecznie zamknąć kanał sesji, który jest w użyciu.  
  
## <a name="binding-and-binding-element"></a>Element wiązania i wiązania  
 Po utworzeniu kanałów usługi i klienta następnym krokiem jest zintegrowanie ich ze środowiska wykonawczego WCF. Kanały są narażone na WCF za pośrednictwem wiązań i elementów wiązania. Powiązanie składa się z jednego lub wielu elementów wiązania. WCF oferuje kilka powiązań zdefiniowanych przez system; na przykład Podstawowehttpbinowanie lub WSHttpBinding. Klasa `HttpCookieSessionBindingElement` zawiera implementację dla elementu wiązania. Zastępuje odbiornik kanału i metody tworzenia fabryki kanałów, aby wykonać niezbędne metody odbiornika kanału lub wystąpienia fabryczne kanału.  
  
 W przykładzie użyto potwierdzeń zasad dla opisu usługi. Dzięki temu przykład opublikować jego wymagania dotyczące kanału do innych klientów, którzy mogą korzystać z usługi. Na przykład ten element wiązania publikuje potwierdzenia zasad, aby poinformować potencjalnych klientów, że obsługuje sesje. Ponieważ przykład umożliwia `ExchangeTerminateMessage` właściwość w konfiguracji elementu wiązania, dodaje niezbędne potwierdzenia, aby pokazać, że usługa obsługuje dodatkową akcję wymiany wiadomości, aby zakończyć konwersację sesji. Klienci mogą następnie użyć tej akcji. Poniższy kod WSDL pokazuje potwierdzenia zasad `HttpCookieSessionBindingElement`utworzone z pliku .  
  
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
  
 Klasa `HttpCookieSessionBinding` jest powiązanie dostarczone przez system, który używa elementu wiązania opisane wcześniej.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Dodawanie kanału do systemu konfiguracji  
 Próbka zawiera dwie klasy, które udostępniają kanał próbki za pośrednictwem konfiguracji. Pierwszy z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> nich `HttpCookieSessionBindingElement`to dla . Większość implementacji jest delegowana `HttpCookieSessionBindingConfigurationElement`do , który <xref:System.ServiceModel.Configuration.StandardBindingElement>pochodzi z . Ma `HttpCookieSessionBindingConfigurationElement` właściwości, które odpowiadają właściwości `HttpCookieSessionBindingElement`na .  
  
### <a name="binding-element-extension-section"></a>Sekcja rozszerzenia elementu wiązania  
 Sekcja `HttpCookieSessionBindingElementSection` <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> jest, która `HttpCookieSessionBindingElement` udostępnia do systemu konfiguracji. Z kilku zastępuje nazwę sekcji konfiguracji, typ elementu wiązania i jak utworzyć element wiązania są zdefiniowane. Następnie możemy zarejestrować sekcję rozszerzenia w pliku konfiguracyjnym w następujący sposób:  
  
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
 Kod testowy do korzystania z tego przykładowego transportu jest dostępny w katalogach klienta i usługi. Składa się z dwóch testów — jeden `allowCookies` test `true` używa powiązania z zestawem na kliencie. Drugi test umożliwia jawne zamknięcie (przy użyciu wymiany komunikatów zakończenia) na powiązanie.  
  
 Po uruchomieniu próbki powinny zostać wyświetlene następujące dane wyjściowe:  
  
```console  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
