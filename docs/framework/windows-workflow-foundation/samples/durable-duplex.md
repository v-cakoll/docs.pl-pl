---
title: Niezawodna komunikacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 107c617fa4a8ee0279dcaa07e495587c617b866e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513356"
---
# <a name="durable-duplex"></a>Niezawodna komunikacja dwukierunkowa
W tym przykładzie przedstawiono sposób instalowania i konfigurowania trwałe dwukierunkowego wiadomości programu exchange, przy użyciu działań dotyczących komunikatów w Windows Workflow Foundation (WF). Exchange trwałych wiadomości dwukierunkowego jest dwukierunkowej wiadomości programu exchange, która ma miejsce w długim okresie czasu. Okres istnienia wymiany komunikatów może być dłuższy niż okres istnienia kanał komunikacyjny i okresu istnienia wystąpienia usługi w pamięci.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W tym przykładzie dwie usługi Windows Communication Foundation (WCF) implementowane przy użyciu programu Windows Workflow Foundation są skonfigurowane do program exchange trwałych wiadomości dwukierunkowego. Wymiany trwałych wiadomości dwukierunkowego składa się z dwóch jednokierunkowe komunikaty wysyłane za pośrednictwem usługi MSMQ i korelować je przy użyciu [wymiana kontekstu .NET](https://go.microsoft.com/fwlink/?LinkID=166059). Komunikaty są wysyłane przy użyciu <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań dotyczących komunikatów. Wymiana kontekstu .NET jest używany do określenia adresu zwrotnego na wysłanych komunikatów. Obie te usługi są hostowane przy użyciu usługi aktywacji procesów Windows (WAS) i są skonfigurowane, aby włączyć opcję trwałości wystąpień usługi.  
  
 Pierwsza usługa (Service1.xamlx) wysyła żądanie do wysyłania usługi (Service2.xamlx) wykonania dodatkowych czynności. Po ukończeniu pracy Service2.xamlx wysyła powiadomienie do Service1.xamlx, aby wskazać, że praca została ukończona. Aplikacja konsoli przepływu pracy konfiguruje kolejki, które usługi nasłuchują i wysyła początkowy komunikat uruchomienia można aktywować Service1.xamlx. Po Service1.xamlx odbiera powiadomienia z Service2.xamlx czy żądanej pracy wykonanej, Service1.xamlx zapisuje wynik w pliku XML. Podczas oczekiwania na komunikat wywołania zwrotnego, Service1.xamlx będzie się powtarzał jego stan wystąpienia przy użyciu domyślnego <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>. Jego stan wystąpienia jako część ukończenia pracy nad żądaniem Service1.xamlx Service2.xamlx, będzie się powtarzać.  
  
 Aby skonfigurować usługi do użycia wymiana kontekstu platformy .NET za pośrednictwem usługi MSMQ, obie usługi są skonfigurowane do używania niestandardowego powiązania, który składa się z <xref:System.ServiceModel.Channels.ContextBindingElement> i <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>. Adres wywołania zwrotnego jest określony za pomocą <xref:System.ServiceModel.Channels.ContextBindingElement> i znajduje się w nagłówku Kontekst wywołania zwrotnego z wszystkie komunikaty wysyłane za pomocą niestandardowego powiązania. Poniższy kod definiuje niestandardowego powiązania.  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Wiązanie używane przez ten przykład nie jest bezpieczne. W przypadku wdrażania aplikacji należy skonfigurować Twoje powiązanie, w oparciu o wymagania dotyczące zabezpieczeń aplikacji.  
  
> [!NOTE]
>  Kolejki, używane w tym przykładzie nie są transakcyjne. Dla przykładu, który pokazuje, jak skonfigurować wymianę komunikatów WCF przy użyciu funkcji kolejek transakcji, zobacz [Aktywacja usługi MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md) próbki.  
  
 Komunikat wysyłany przez Service1.xamlx do Service2.xamlx są wysyłane przy użyciu klienta punktu końcowego, konfiguruje się adres Service2.xamlx i niestandardowego powiązania zdefiniowane wcześniej. Wywołania zwrotnego z Service2.xamlx Service1.xamlx są wysyłane przy użyciu punktu końcowego klienta przy użyciu nie jawnie skonfigurowanego adresu, ponieważ adres jest pobierana z kontekstu wywołanie zwrotne wysyłane przez Service1.xamlx. Poniższy kod definiuje punktów końcowych klienta.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 Poniższy przykład kodu przedstawia punktów końcowych przy użyciu tego niestandardowego powiązania, zmieniając domyślnego mapowania protokołu dla net.msmq adres podstawowy do użycia tego niestandardowego powiązania.  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 Poniższy przykład kodu umożliwia stanów trwałych dla obu usług, dodając <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> zachowanie do usług i określanie parametrów połączenia dla bazy danych trwałości.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a>Wymagania systemowe  
 Ten przykładowy skrypt wymaga następujących składników.  
  
1.  Internetowe usługi informacyjne.  
  
2.  Internetowe usługi informacyjne -> zgodność z narzędziami zarządzania usług IIS 6.0 -> zgodności konfiguracji metabazy usług IIS i usług IIS 6.0.  
  
3.  Usługi World Wide Web -> Tworzenie aplikacji funkcji -> ASP.NET.  
  
4.  Microsoft Message kolejki (MSMQ) serwer.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Konfigurowanie bazy danych trwałości i katalog wyników.  
  
    1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
    2.  Przejdź do folderu, w tym przykładzie, a następnie uruchom plik Setup.cmd.  
  
2.  Konfigurowanie aplikacji wirtualnej.  
  
    1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, Zarejestruj aplikację ASP.NET przy użyciu następującego polecenia.  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i wybierając polecenie **Uruchom jako administrator**.  
  
    3.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik DurableDuplex.sln.  
  
3.  Konfigurowanie usługi kolejki.  
  
    1.  Aby uruchomić klienta DurableDuplex, naciśnij klawisz F5.  
  
    2.  Otwórz **Zarządzanie komputerem** konsoli, uruchamiając `Compmgmt.msc` z poziomu wiersza polecenia.  
  
    3.  Rozwiń **usługi i aplikacje**, **usługi kolejkowania komunikatów**. **Kolejki prywatne**.  
  
    4.  Kliknij prawym przyciskiem myszy durableduplex/service1.xamlx i durableduplex/service2.xamlx kolejek, a następnie wybierz pozycję **właściwości**.  
  
    5.  Wybierz **zabezpieczeń** kartę i umożliwiają **wszyscy odbieranie wiadomości**, **wglądu do wiadomości** i **wysyłania komunikatu** uprawnienia dla obu kolejek.  
  
    6.  Otwórz Menedżera internetowych usług informacyjnych (IIS).  
  
    7.  Przejdź do **serwera**, **witryn**, **domyślnej witryny sieci Web**, **prywatnej**, **trwałe dwukierunkowego** i wybierz pozycję **Zaawansowane opcje**.  
  
    8.  Zmiana **włączone protokoły** do **http,net.msmq**.  
  
4.  Uruchamianie aplikacji przykładowej.  
  
    1.  Przejdź do http://localhost/private/durableduplex/service1.xamlx i http://localhost/private/durableduplex/service2.xamlx aby upewnić się, że obie te usługi są uruchomione.  
  
    2.  Naciśnij klawisz F5, aby uruchomić DurableDuplexClient.  
  
         Po zakończeniu wymiany trwałych wiadomości dwukierunkowego result.xml pliku zostanie zapisana w folderze C:\Inbox i zawiera wynik wymianę komunikatów.  
  
#### <a name="to-cleanup-optional"></a>Aby oczyścić (opcjonalnie)  
  
1.  Uruchom Cleanup.cmd.  
  
    1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
    2.  Przejdź do folderu, w tym przykładzie, a następnie uruchom Cleanup.cmd.  
  
2.  Usuń aplikację wirtualną dla usług.  
  
    1.  Otwórz Menedżera usług Internet Information Services (IIS), uruchamiając `Inetmgr.exe` z poziomu wiersza polecenia.  
  
    2.  Przejdź do domyślnej witryny sieci Web, a następnie usuń **prywatnej** katalogu wirtualnego.  
  
3.  Usunięcie kolejki, skonfiguruj dla tego przykładu.  
  
    1.  Otwórz konsolę Zarządzanie komputerem, uruchamiając `Compmgmt.msc` z poziomu wiersza polecenia.  
  
    2.  Rozwiń **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.  
  
    3.  Usuwanie kolejek durableduplex/service1.xamlx i durableduplex/service2.xamlx.  
  
4.  Usuń katalog C:\Inbox.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`