---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 64a7cba7b1bbc55a4504e3af4784fcb2a84f0fa1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807231"
---
# <a name="httpcookiesession"></a>HttpCookieSession
W tym przykładzie pokazano, jak zbudować kanału używać plików cookie protokołu HTTP do zarządzania sesji protokołu niestandardowego. Ten kanał umożliwia komunikację między usług Windows Communication Foundation (WCF) i ASMX klientów lub między klientami programu WCF i usługami ASMX.  
  
 Kiedy klient wywołuje metody sieci Web w usługi sieci Web ASMX które jest oparte na sesji, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aparat wykonuje następujące czynności:  
  
-   Generuje unikatowy identyfikator (identyfikator sesji).  
  
-   Generuje obiekt sesji i kojarzy ją z unikatowego identyfikatora.  
  
-   Dodaje do odpowiedzi nagłówek HTTP Set-Cookie Unikatowy identyfikator i wysyła go do klienta.  
  
-   Identyfikuje klienta na kolejnych wywołań na podstawie Identyfikatora sesji wysyła do niego.  
  
 Klient dołącza ten identyfikator sesji w jego kolejnych żądań wysyłanych do serwera. Serwer używa Identyfikatora sesji z klienta można załadować obiektu session odpowiednie dla bieżącego kontekstu HTTP.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Kanał HttpCookieSession wymiany komunikatów  
 W tym przykładzie umożliwia sesji dla scenariuszy ASMX podobne. W dolnej części naszych stosu kanału, istnieje transportu HTTP, która obsługuje <xref:System.ServiceModel.Channels.IRequestChannel> i <xref:System.ServiceModel.Channels.IReplyChannel>. To zadanie kanału zapewnienie na wyższe poziomy stosu kanału sesji. Przykład implementuje dwa kanały (<xref:System.ServiceModel.Channels.IRequestSessionChannel> i <xref:System.ServiceModel.Channels.IReplySessionChannel>) obsługują sesji.  
  
## <a name="service-channel"></a>Kanał usługi  
 Przykład zawiera kanału usługi na `HttpCookieReplySessionChannelListener` klasy. Ta klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener> interfejsu i konwertuje <xref:System.ServiceModel.Channels.IReplyChannel> kanału z niższym w stosie kanału, aby <xref:System.ServiceModel.Channels.IReplySessionChannel>. Ten proces można podzielić na następujące elementy:  
  
-   Po otwarciu odbiornika kanałów akceptuje wewnętrzny kanał z jego wewnętrzny odbiornika. Ponieważ wewnętrzny odbiornika jest odbiornik datagram i okres istnienia zaakceptowanych kanałów jest całkowicie niezależna od istnienia odbiornika, możemy zamknąć wewnętrzny odbiornika i zawierać tylko wewnętrznym kanale  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   Po ukończeniu procesu otwierania skonfigurowanie pętli komunikatów odbierać komunikaty z kanału wewnętrzny.  
  
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
  
-   Po nadejściu wiadomości, kanał usługi sprawdza identyfikator sesji i demultipleksowanie do kanału sesji odpowiednie. Odbiornik kanału przechowuje słownik, który mapuje identyfikatory sesji z wystąpieniami kanału sesji.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` Klasa implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel>. Wyższe poziomy kanału stosu wywołań <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metody żądań odczytu dla tej sesji. Każdy kanał sesji ma prywatną kolejkę komunikatów wypełniany przez kanał usługi.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 W przypadku, gdy ktoś wywołuje <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metody i nie ma żadnych komunikatów w kolejce wiadomości, kanał czeka na określoną ilość czasu, przed zamknięciem samej siebie. To spowoduje oczyszczenie kanały sesji dla klientów z systemem innym niż WCF.  
  
 Używamy `channelMapping` do śledzenia `ReplySessionChannels`, i firma Microsoft nie zamykaj naszych bazowy `innerChannel` dopóki zaakceptowanych kanałów zostały zamknięte. W ten sposób `HttpCookieReplySessionChannel` może występować poza okres istnienia `HttpCookieReplySessionChannelListener`. Możemy również nie trzeba martwić się odbiornika pobierania bezużytecznych poniżej nam, ponieważ zaakceptowanych kanałów zachować odwołanie do ich odbiornika za pomocą `OnClosed` wywołania zwrotnego.  
  
## <a name="client-channel"></a>Kanału klienta  
 Odpowiedni kanał klienta jest `HttpCookieSessionChannelFactory` klasy. Podczas tworzenia kanału fabryki kanałów opakowuje kanału wewnętrznego żądania z `HttpCookieRequestSessionChannel`. `HttpCookieRequestSessionChannel` Klasy przekazuje wywołań podstawowy kanał żądania. Jeśli klient zamyka serwera proxy, `HttpCookieRequestSessionChannel` wysyła komunikat do usługi, która wskazuje, że zamknięcie kanału. W związku z tym stosu kanału usługi można bezpiecznie zamknięcia kanału sesji, który jest używany.  
  
## <a name="binding-and-binding-element"></a>Powiązanie i Element powiązania  
 Po utworzeniu kanały usługi i klienta, następnym krokiem jest integrację środowiska uruchomieniowego usługi WCF. Kanały są widoczne dla usług WCF za pośrednictwem powiązania i elementy powiązań. Powiązanie składa się z jednego lub wielu elementów powiązania. Usługi WCF oferuje kilka powiązań zdefiniowanych przez system; na przykład klasy BasicHttpBinding lub WSHttpBinding albo obsługę. `HttpCookieSessionBindingElement` Klasa zawiera implementację elementu powiązania. Zastępuje ona, czy niezbędne kanału wystąpień fabryki odbiornika lub kanału odbiornika kanałów i metod tworzenia fabryki kanału.  
  
 W przykładzie użyto potwierdzeń zasad opisu usługi. Umożliwia to przykład, aby opublikować jej wymagań dotyczących kanału do innych klientów, którzy mogą korzystać z usługi. Na przykład ten element powiązania publikuje potwierdzeń zasad, aby umożliwić klientom potencjalnych wiedzieć, że aplikacja obsługuje sesji. Ponieważ próbki pozwala `ExchangeTerminateMessage` właściwości w Konfiguracja elementu powiązania, dodaje potwierdzenia niezbędne, aby pokazać, że usługa obsługuje akcję wymiany wiadomości dodatkowe zakończenie sesji konwersacji. Klienci mogą następnie użyj tej akcji. Poniższy kod WSDL przedstawia potwierdzenia zasady utworzone na podstawie `HttpCookieSessionBindingElement`.  
  
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
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Dodawanie kanału do systemu konfiguracji  
 Przykład zawiera dwie klasy, które udostępniają kanału próbki za pomocą konfiguracji. Pierwsza to <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> dla `HttpCookieSessionBindingElement`. Delegowane do zbiorczego wdrożenia `HttpCookieSessionBindingConfigurationElement`, która jest pochodną <xref:System.ServiceModel.Configuration.StandardBindingElement>. `HttpCookieSessionBindingConfigurationElement` Ma właściwości, które odpowiadają właściwościom na `HttpCookieSessionBindingElement`.  
  
### <a name="binding-element-extension-section"></a>Sekcja rozszerzenia elementu powiązania  
 Sekcja `HttpCookieSessionBindingElementSection` jest <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> który uwidacznia `HttpCookieSessionBindingElement` do konfiguracji systemu. Z kilku zastąpień zdefiniowanych nazwę sekcji konfiguracji, typ elementu powiązania i jak można utworzyć elementu powiązania. Firma Microsoft może następnie rejestrować sekcji rozszerzeń w pliku konfiguracji w następujący sposób:  
  
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
 Za pomocą tego transportu przykładowy kod testu jest dostępny w katalogach klienta i usługi. Składa się z dwóch testów — jeden test używa powiązania z `allowCookies` ustawioną `true` na kliencie. Drugi test umożliwia zamknięcie jawnego (używając przerwania wymianie wiadomości) dla powiązania.  
  
 Po uruchomieniu próbki powinny być widoczne następujące dane wyjściowe:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też
