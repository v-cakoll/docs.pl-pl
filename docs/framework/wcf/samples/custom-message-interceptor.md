---
title: Niestandardowy element przechwytujący komunikaty
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 53005212bc834d73ab5cbb4545d1477112f29c75
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716812"
---
# <a name="custom-message-interceptor"></a>Niestandardowy element przechwytujący komunikaty
Ten przykład ilustruje użycie modelu rozszerzalności kanałów. W szczególności pokazano, jak zaimplementować niestandardowy element powiązania, który tworzy fabryki kanałów i odbiorniki kanałów do przechwytywania wszystkich komunikatów przychodzących i wychodzących w konkretnym momencie w stosie czasu wykonywania. Przykład zawiera również klienta i serwer, który pokazuje użycie tych niestandardowych fabryk.  
  
 W tym przykładzie zarówno klient, jak i usługa są programami konsolowymi (. exe). Klient i usługa korzystają ze wspólnej biblioteki (. dll), która zawiera niestandardowy element powiązania i powiązane z nim obiekty czasu wykonywania.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 W przykładzie opisano zalecaną procedurę tworzenia niestandardowego kanału warstwowego w Windows Communication Foundation (WCF), przy użyciu struktury kanału oraz najlepszych rozwiązań w zakresie usług WCF. Poniżej przedstawiono procedurę tworzenia niestandardowego kanału warstwowego:  
  
1. Określ, które kształty kanałów będą obsługiwane przez fabrykę kanałów i odbiornik kanału.  
  
2. Utwórz fabrykę kanałów i odbiornik kanału obsługujący kształty kanałów.  
  
3. Dodaj element powiązania, który dodaje niestandardowy kanał warstwowy do stosu kanału.  
  
4. Dodaj sekcję rozszerzenie elementu powiązania, aby udostępnić nowy element powiązania do systemu konfiguracji.  
  
## <a name="channel-shapes"></a>Kształty kanału  
 Pierwszym krokiem w przypadku pisania niestandardowego kanału warstwowego jest określenie, które kształty są wymagane dla kanału. Nasz Inspektor komunikatów obsługuje dowolny kształt, który obsługuje warstwa poniżej US (na przykład jeśli warstwa poniżej US może tworzyć <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, udostępniamy również <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Fabryka kanałów i fabryka odbiorników  
 Następnym krokiem przy tworzeniu niestandardowego kanału warstwowego jest utworzenie implementacji <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienta i <xref:System.ServiceModel.Channels.IChannelListener> dla kanałów usługi.  
  
 Te klasy przyjmują wewnętrzną fabrykę i odbiornik i umożliwiają delegowanie wszystkich, ale `OnCreateChannel` i `OnAcceptChannel` wywołań do wewnętrznej fabryki i odbiornika.  
  
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
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Przykład definiuje niestandardowy element powiązania: `InterceptingBindingElement`. `InterceptingBindingElement` pobiera `ChannelMessageInterceptor` jako dane wejściowe i używa tego `ChannelMessageInterceptor` do manipulowania wiadomościami, które przechodzą przez nią. Jest to jedyna klasa, która musi być publiczna. Fabryki, odbiornik i kanały mogą być wewnętrznymi implementacjami publicznych interfejsów czasu wykonywania.  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a>Dodawanie obsługi konfiguracji  
 W celu zintegrowania z konfiguracją powiązań Biblioteka definiuje procedurę obsługi sekcji konfiguracji jako element powiązania sekcji rozszerzenia. Pliki konfiguracji klienta i serwera muszą rejestrować rozszerzenie elementu powiązania z systemem konfiguracji. Realizatorzy, którzy chcą uwidocznić swój element powiązania w systemie konfiguracji, mogą pochodzić od tej klasy.  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement 
{ 
    //... 
}
```  
  
## <a name="adding-policy"></a>Dodawanie zasad  
 Aby przeprowadzić integrację z naszym systemem zasad, `InterceptingBindingElement` implementuje IPolicyExportExtension, aby sygnalizować, że będziemy uczestniczyć w generowaniu zasad. Aby umożliwić obsługę importowania zasad na wygenerowanym kliencie, użytkownik może zarejestrować klasę pochodną `InterceptingBindingElementImporter` i zastąpić `CreateMessageInterceptor`() w celu wygenerowania klasy `ChannelMessageInterceptor` z obsługą zasad.  
  
## <a name="example-droppable-message-inspector"></a>Przykład: droppable — Inspektor komunikatów  
 W przykładzie przedstawiono przykładową implementację `ChannelMessageInspector`, która odrzuca komunikaty.  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Możesz uzyskać do niego dostęp z konfiguracji w następujący sposób:  
  
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
  
 Zarówno klient, jak i serwer używają tej nowo utworzonej sekcji konfiguracji, aby wstawić niestandardowe fabryki do najniższego poziomu swoich stosów kanałów czasu wykonywania (powyżej poziomu transportu).  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 Klient używa biblioteki `MessageInterceptor` w celu dodania niestandardowego nagłówka do parzystych wiadomości. Usługa z drugiej strony używa biblioteki `MessageInterceptor` do usuwania wszelkich komunikatów, które nie mają tego nagłówka specjalnego.  
  
 Po uruchomieniu usługi należy zobaczyć następujące dane wyjściowe klienta programu, a następnie klienta.  
  
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
  
 Klient raportuje 10 różnych szybkości wiatru do usługi, ale tylko Tagi mające połowę z nagłówka specjalnego.  
  
 W usłudze powinny zostać wyświetlone następujące dane wyjściowe:  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Uruchom najpierw program Service. exe, a następnie uruchom program Client. exe i obejrzyj oba okna konsoli dla danych wyjściowych.  
