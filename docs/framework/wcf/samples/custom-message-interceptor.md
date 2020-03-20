---
title: Niestandardowy element przechwytujący komunikaty
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 433b14433a7e2dd6edad551a2732e9049a9861ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145089"
---
# <a name="custom-message-interceptor"></a>Niestandardowy element przechwytujący komunikaty
W tym przykładzie pokazano użycie modelu rozszerzalności kanału. W szczególności pokazuje, jak zaimplementować niestandardowy element wiązania, który tworzy fabryki kanałów i odbiorników kanałów do przechwytywania wszystkich komunikatów przychodzących i wychodzących w określonym punkcie w stosie w czasie wykonywania. Przykład zawiera również klienta i serwera, które pokazują użycie tych fabryk niestandardowych.  
  
 W tym przykładzie zarówno klient, jak i usługa są programami konsoli (exe). Klient i usługa korzystają ze wspólnej biblioteki (.dll), która zawiera niestandardowy element wiązania i skojarzone z nim obiekty w czasie wykonywania.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 W przykładzie opisano zalecaną procedurę tworzenia niestandardowego kanału warstwowego w programie Windows Communication Foundation (WCF), przy użyciu struktury kanału i postępując zgodnie z najlepszymi rozwiązaniami WCF. Kroki tworzenia niestandardowego kanału warstwowego są następujące:  
  
1. Zdecyduj, który z kształtów kanału będzie obsługiwana przez fabrykę kanałów i odbiornik kanałów.  
  
2. Utwórz fabrykę kanałów i odbiornik kanałów, które obsługują kształty kanału.  
  
3. Dodaj element wiązania, który dodaje niestandardowy kanał warstwowy do stosu kanałów.  
  
4. Dodaj sekcję rozszerzenia elementu wiązania, aby udostępnić nowy element wiązania do systemu konfiguracji.  
  
## <a name="channel-shapes"></a>Kształty kanałów  
 Pierwszym krokiem w pisaniu niestandardowego kanału warstwowego jest podjęcie decyzji, które kształty są wymagane dla kanału. Dla naszego inspektora wiadomości, obsługujemy każdy kształt, który obsługuje warstwa <xref:System.ServiceModel.Channels.IOutputChannel> poniżej nas (na przykład, jeśli warstwa poniżej nas może zbudować, a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>następnie również wystawiać <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Fabryka kanałów i fabryka słuchaczy  
 Następnym krokiem w pisaniu niestandardowego kanału warstwowego jest utworzenie implementacji <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienckich <xref:System.ServiceModel.Channels.IChannelListener> i dla kanałów usług.  
  
 Te klasy wziąć wewnętrzną fabrykę i odbiornika i delegować wszystkie oprócz `OnCreateChannel` i `OnAcceptChannel` wywołania do wewnętrznej fabryki i odbiornika.  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu wiązania  
 Przykład definiuje niestandardowy element `InterceptingBindingElement`wiązania: . `InterceptingBindingElement`przyjmuje `ChannelMessageInterceptor` jako dane wejściowe i `ChannelMessageInterceptor` używa tego do manipulowania wiadomościami, które przechodzą przez niego. Jest to jedyna klasa, która musi być publiczna. Fabryczna, odbiornik i kanały mogą być wewnętrznymi implementacjami publicznych interfejsów w czasie wykonywania.  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a>Dodawanie obsługi konfiguracji  
 Aby zintegrować z konfiguracją powiązania, biblioteka definiuje program obsługi sekcji konfiguracji jako sekcję rozszerzenia elementu wiązania. Pliki konfiguracyjne klienta i serwera muszą zarejestrować rozszerzenie elementu powiązania w systemie konfiguracji. Implementatory, które chcą udostępnić ich element wiązania do systemu konfiguracji może pochodzić z tej klasy.  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a>Dodawanie zasad  
 Aby zintegrować się `InterceptingBindingElement` z naszym systemem zasad, implementuje IPolicyExportExtension, aby zasygnalizować, że powinniśmy uczestniczyć w generowaniu zasad. Aby obsługiwać zasady importowania na wygenerowanym kliencie, `InterceptingBindingElementImporter` `CreateMessageInterceptor`użytkownik może zarejestrować klasę pochodną i `ChannelMessageInterceptor` zastąpić (), aby wygenerować klasę z włączoną zasadą.  
  
## <a name="example-droppable-message-inspector"></a>Przykład: Inspektor wiadomości z wypuszczalny  
 Zawarte w przykładzie jest przykład `ChannelMessageInspector` implementacji, który porzuca wiadomości.  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Dostęp do niego można uzyskać z konfiguracji w następujący sposób:  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 Zarówno klient, jak i serwer używają tej nowo utworzonej sekcji konfiguracji, aby wstawić fabryki niestandardowe do najniższego poziomu ich stosów kanałów w czasie wykonywania (powyżej poziomu transportu).  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 Klient używa biblioteki, `MessageInterceptor` aby dodać niestandardowy nagłówek do wiadomości parzyste. Usługa z drugiej strony `MessageInterceptor` używa biblioteki do upuszczania wiadomości, które nie mają tego specjalnego nagłówka.  
  
 Po uruchomieniu usługi, a następnie na kliencie, powinny zostać wyświetlenia następujące dane wyjściowe klienta.  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 Klient zgłasza 10 różnych prędkości wiatru do usługi, ale tylko tagi połowę z nich ze specjalnym nagłówkiem.  
  
 W usłudze powinny zostać wyświetlene następujące dane wyjściowe:  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Najpierw uruchom program Service.exe, a następnie uruchom program Client.exe i obserwuj oba okna konsoli w celu uzyskania danych wyjściowych.  
