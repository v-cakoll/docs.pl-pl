---
title: "Niestandardowy element przechwytujący komunikaty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: acac4baa5be68d042dd1b0a11d7acfe609169e10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-interceptor"></a>Niestandardowy element przechwytujący komunikaty
W tym przykładzie przedstawiono stosowania modelu rozszerzalności kanału. W szczególności widoczny jest sposób implementuje element niestandardowego powiązania, który tworzy fabryk kanałów i odbiorników kanału do przechwycenia wszystkich wiadomości przychodzących i wychodzących w określonym punkcie w stosie czasu wykonywania. Przykład obejmuje również klienta i serwera, które przedstawiają sposób używania tych niestandardowych fabryki.  
  
 W tym przykładzie zarówno klient, jak i usługi są programy konsoli (.exe). Klient i usługa programu użycie wspólnej biblioteki (.dll), który zawiera element niestandardowego powiązania i powiązane obiekty środowiska wykonawczego.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Próbka opisuje zalecaną procedurą tworzenia w niestandardowym kanale warstwowego [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], przy użyciu platformy kanału i wykonując [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] najlepsze rozwiązania. Kroki, aby utworzyć niestandardowy kanał warstwowego są następujące:  
  
1.  Decyzji, które kształtów kanału będzie obsługiwać Twoje fabryki kanału i odbiornika kanałów.  
  
2.  Tworzenie fabryki kanałów i odbiornik kanału, który obsługuje kanał kształtów.  
  
3.  Dodaj element powiązania, który dodaje niestandardowym kanale warstwowego stos kanału.  
  
4.  Dodaj sekcję rozszerzenia elementu powiązania do udostępnienia element powiązania do konfiguracji systemu.  
  
## <a name="channel-shapes"></a>Kształty kanału  
 Pierwszą czynnością przy tworzeniu niestandardowym kanale warstwowego jest podjęcie decyzji, które kształty są wymagane dla kanału. Dla naszych inspektora komunikat obsługujemy dowolnego kształtu, który obsługuje warstwy poniżej nam (na przykład jeśli warstwa poniżej nam można tworzyć <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, a następnie możemy również ujawniać <xref:System.ServiceModel.Channels.IOutputChannel> i <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Fabryka kanałów i fabryki odbiornika  
 Następnym krokiem w niestandardowym kanale warstwowego pisaniu jest utworzenie implementacja <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienta oraz <xref:System.ServiceModel.Channels.IChannelListener> kanałów usługi.  
  
 Te klasy wewnętrzna fabryka i odbiornika i delegowanie wszystkie elementy oprócz `OnCreateChannel` i `OnAcceptChannel` wywołania wewnętrzna fabryka i odbiornika.  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Przykład definiuje element powiązania niestandardowego: `InterceptingBindingElement`. `InterceptingBindingElement`przyjmuje `ChannelMessageInterceptor` jako dane wejściowe i używa go `ChannelMessageInterceptor` do manipulowania wiadomości, które przechodzą przez go. Jest to jedyna klasa, która musi być publiczny. Fabryka odbiornika i kanały wszystkie może być wewnętrzny implementacje interfejsów publicznych czasu wykonywania.  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>Dodawanie obsługi konfiguracji  
 Aby zintegrować za pomocą konfiguracji powiązania, biblioteka definiuje modułu obsługi sekcji konfiguracji jako sekcja rozszerzenia elementu powiązania. Pliki konfiguracji klienta i serwera, należy zarejestrować element rozszerzenia powiązania przy użyciu systemu konfiguracji. Implementujące obiekty, które chcesz udostępnić ich elementu powiązania do konfiguracji systemu może dziedziczyć po tej klasie.  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>Dodawanie zasad  
 Integracja z naszym systemem zasad `InterceptingBindingElement` implementuje IPolicyExportExtension sygnalizują, możemy powinny uczestniczyć w generowania zasad. Do importowania zasady pomocy technicznej na wygenerowanego klienta, użytkownik może zarejestrować klasy pochodnej z `InterceptingBindingElementImporter` i zastąpić `CreateMessageInterceptor`(), aby wygenerować ich włączone zasady `ChannelMessageInterceptor` klasy.  
  
## <a name="example-droppable-message-inspector"></a>Przykład: Inspector Droppable wiadomości  
 Uwzględnione w próbce jest przykładem implementacji `ChannelMessageInspector` który porzuca wiadomości.  
  
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
  
 Klient i serwer Użyj tej sekcji konfiguracyjnej nowo utworzony, aby wstawić niestandardowych fabryki do najniższego poziomu ich stosów kanału czasu wykonywania (powyżej poziomu transportu).  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 Klient używa `MessageInterceptor` biblioteki nawet Dodawanie niestandardowego nagłówka do numerowane wiadomości. Z drugiej strony używa usługi `MessageInterceptor` biblioteki można usunąć wszystkie komunikaty, które nie mają tego specjalne nagłówka.  
  
 Po uruchomieniu usługi, a następnie klienta powinny być widoczne następujące dane wyjściowe klienta.  
  
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
  
 Klient raporty 10 knie różnych szybkościach do usługi, ale tylko tagów połowy je za pomocą specjalnych nagłówków.  
  
 W usłudze powinny być widoczne następujące dane wyjściowe:  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Uruchom najpierw Service.exe, a następnie uruchom Client.exe i obejrzyj oba okna konsoli dla danych wyjściowych.  
  
## <a name="see-also"></a>Zobacz też
