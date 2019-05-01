---
title: Niestandardowy element przechwytujący komunikaty
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: d585e60c9b31e56873b0501425f55541bd647e02
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990746"
---
# <a name="custom-message-interceptor"></a>Niestandardowy element przechwytujący komunikaty
Niniejszy przykład pokazuje użycie kanału modelu rozszerzalności. W szczególności pokazuje sposób implementacji element niestandardowego powiązania, który pokazuje tworzenie fabryki kanałów i odbiorniki kanałów, aby przechwycić wszystkie komunikaty przychodzące i wychodzące w określonym punkcie w stosie czasu wykonywania. Przykład zawiera również klienta i serwera, które przedstawiają korzystanie z tych niestandardowych fabryk.  
  
 W tym przykładzie zarówno klient, jak i usługi są programy konsoli (.exe). Klient i usługa zarówno wprowadzić korzystanie z typowych biblioteki (.dll), który zawiera element niestandardowego powiązania i powiązane obiekty środowiska wykonawczego.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Przykład w tym artykule opisano zalecane procedury tworzenia niestandardowym kanale warstwowych w Windows Communication Foundation (WCF), używając struktura kanału i zgodnie z najlepszymi rozwiązaniami WCF. Kroki, aby utworzyć niestandardowy kanał warstwowe są następujące:  
  
1. Zdecyduj, które kształty kanału usługi fabryki kanałów i będzie obsługiwać odbiornika kanałów.  
  
2. Tworzenie fabryki kanałów i odbiornik kanału, który obsługuje kształty kanału.  
  
3. Dodaj element powiązania, który dodaje niestandardowy kanał warstwowej stos kanału.  
  
4. Dodaj sekcję rozszerzenia elementu powiązania do udostępnienia nowego elementu powiązania do konfiguracji systemu.  
  
## <a name="channel-shapes"></a>Kształty kanału  
 Pierwszym krokiem podczas zapisywania w niestandardowym kanale warstwowej jest podjęcie decyzji, które kształty są wymagane dla kanału. Dla naszych Inspektor wiadomości, firma Microsoft wspiera dowolnego kształtu, który obsługuje warstwy poniżej nam (na przykład, jeśli można tworzyć warstwy poniżej nam <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, a następnie możemy także ujawniać <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Fabryka kanałów i fabryki odbiornika  
 Następnym krokiem w niestandardowym kanale warstwowej pisaniu jest utworzenie implementacji klasy <xref:System.ServiceModel.Channels.IChannelFactory> kanały klientów i z <xref:System.ServiceModel.Channels.IChannelListener> kanałach usługi.  
  
 W ramach tych zajęć wewnętrzna fabryka i odbiornik i delegować wszystkie elementy oprócz `OnCreateChannel` i `OnAcceptChannel` wywołania wewnętrzna fabryka i odbiornika.  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Przykładowa aplikacja definiuje element powiązania niestandardowego: `InterceptingBindingElement`. `InterceptingBindingElement` Trwa `ChannelMessageInterceptor` jako dane wejściowe i używa tych informacji `ChannelMessageInterceptor` do manipulowania wiadomości, które przechodzą przez go. Jest to jedyna klasa, która musi być publiczny. Fabryka, odbiornik i kanałów wszystkie można wewnętrznych implementacji interfejsów publicznych czasu wykonywania.  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>Dodanie obsługi konfiguracji  
 Można zintegrować z usługą Konfiguracja powiązania, biblioteka definiuje obsługi sekcji konfiguracji powiązania sekcji rozszerzenia elementu. Pliki konfiguracji klienta i serwera, należy zarejestrować rozszerzenie elementu powiązania przy użyciu systemu konfiguracji. Implementujące obiekty, które chcesz udostępnić ich elementu powiązania do konfiguracji systemu może pochodzić z tej klasy.  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>Dodawanie zasad  
 Do integracji z naszego systemu zasad `InterceptingBindingElement` implementuje IPolicyExportExtension celu sygnalizowania, że firma Microsoft powinny uczestniczyć w Generowanie zasad. Aby obsługiwać zasady importowania na wygenerowanego klienta, użytkownik może zarejestrować klasy pochodnej z `InterceptingBindingElementImporter` i zastąpić `CreateMessageInterceptor`(), aby wygenerować ich włączone zasady `ChannelMessageInterceptor` klasy.  
  
## <a name="example-droppable-message-inspector"></a>Przykład: Inspektor droppable wiadomości  
 Zawarte w przykładzie jest przykładem implementacji `ChannelMessageInspector` która powoduje porzucenie wiadomości.  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Można do niego dostęp z konfiguracji w następujący sposób:  
  
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
  
 Na kliencie i serwerze umożliwiają wstawianie niestandardowych fabryk najniższy poziom ich stosów kanał w czasie wykonywania (na wyższym poziomie transportu) Ta sekcja konfiguracji nowo utworzony.  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 Klient używa `MessageInterceptor` biblioteki, aby dodać niestandardowy nagłówek do nawet numerowane wiadomości. Usługa korzysta z drugiej strony `MessageInterceptor` biblioteki, aby usunąć wszystkie komunikaty, które nie mają tego pliku nagłówkowego specjalne.  
  
 Następujące dane wyjściowe z klienta powinien być widoczny po uruchomieniu usługi, a następnie klienta.  
  
```  
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
  
 Klient raportuje 10 prędkość wiatru różnych do usługi, ale tylko połowę je za pomocą specjalnych nagłówków tagów.  
  
 W usłudze powinny zostać wyświetlone następujące dane wyjściowe:  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Uruchom najpierw Service.exe, a następnie uruchom Client.exe się i obejrzyj oba okna konsoli danych wyjściowych.  
