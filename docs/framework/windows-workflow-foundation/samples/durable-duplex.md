---
title: Niezawodna komunikacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 3df5ba962ef33594df1eaebc20789fa9e2d35244
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="durable-duplex"></a>Niezawodna komunikacja dwukierunkowa
W tym przykładzie pokazano, jak instalowanie i konfigurowanie trwałe dupleksu wiadomości programu exchange przy użyciu działań obsługi wiadomości w systemie Windows Workflow Foundation (WF). Exchange trwałe komunikat dupleksu jest dwukierunkowe wiadomości programu exchange, która ma miejsce w długim okresie czasu. Okres istnienia wymiany komunikatów może być dłuższy niż okres istnienia kanał komunikacyjny i okresem istnienia w pamięci wystąpień usługi.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W tym przykładzie dwie usługi Windows Communication Foundation (WCF) implementowane za pomocą programu Windows Workflow Foundation są skonfigurowane do ma exchange trwałe dupleksu wiadomości. Exchange trwałe dupleksu komunikat składa się z dwóch jednokierunkowe komunikaty wysyłane przez usługę MSMQ i skorelowane przy użyciu [wymiana kontekstu .NET](http://go.microsoft.com/fwlink/?LinkID=166059). Komunikaty są wysyłane przy użyciu <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań dotyczących komunikatów. Wymiana kontekstu .NET jest Użyj, aby określić adres wywołania zwrotnego na wysłane wiadomości. Obie te usługi są obsługiwane przy użyciu usługi aktywacji procesów systemu Windows (WAS) i są skonfigurowane do włączenia trwałości wystąpień usługi.  
  
 Pierwszej usługi (Service1.xamlx) wysyła żądanie do wysyłania usługi (Service2.xamlx) do wykonania dodatkowych czynności. Po zakończeniu pracy Service2.xamlx wysyła powiadomienie do Service1.xamlx, aby wskazać, że ukończono pracę. Aplikacja konsoli przepływu pracy konfiguruje kolejki, które nasłuchują usługi na i wysyła początkowy komunikat uruchomienia aktywować Service1.xamlx. Po Service1.xamlx odbierze powiadomienie z Service2.xamlx zakończenie żądanej pracy, Service1.xamlx zapisuje wyniki w pliku XML. Podczas oczekiwania na wiadomość wywołania zwrotnego, Service1.xamlx utrwala swój stan wystąpienia, przy użyciu domyślnego <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>. Service2.xamlx utrwala swój stan wystąpienia jako część kończy pracę, żądane przez Service1.xamlx.  
  
 Aby skonfigurować usługi do użycia wymiana kontekstu .NET za pośrednictwem usługi MSMQ, obie te usługi są skonfigurowane do używania niestandardowego powiązania, który składa się z <xref:System.ServiceModel.Channels.ContextBindingElement> i <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>. Określono adres wywołania zwrotnego z <xref:System.ServiceModel.Channels.ContextBindingElement> i znajduje się w nagłówek kontekstu wywołania zwrotnego z wszystkich komunikatów wysyłanych za pomocą niestandardowego powiązania. Poniższy przykładowy kod definiuje niestandardowego powiązania.  
  
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
>  Powiązanie używane przez ten przykład nie jest bezpieczne. W przypadku wdrażania aplikacji, należy skonfigurować wiązania na podstawie wymagań zabezpieczeń aplikacji.  
  
> [!NOTE]
>  Kolejki używane w tym przykładzie nie są transakcyjne. Dla przykładu, który pokazuje, jak skonfigurować przy użyciu kolejki transakcji wymiany wiadomości WCF, zobacz [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md) próbki.  
  
 Komunikat wysyłany przez Service1.xamlx do Service2.xamlx są wysyłane przy użyciu punktu końcowego klienta z adresem Service2.xamlx i niestandardowego powiązania zdefiniowane wcześniej. Wywołanie zwrotne z Service2.xamlx do Service1.xamlx są wysyłane przy użyciu punktu końcowego klienta z żadnego jawnie skonfigurowanego adresu, ponieważ adres jest pobierana z kontekstu wywołania zwrotnego wysyłane przez Service1.xamlx. Poniższy przykładowy kod definiuje punkty końcowe klienta.  
  
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
  
 Poniższy przykładowy kod przedstawia punktów końcowych przy użyciu tego powiązania niestandardowego przez zmianę domyślnego mapowania protokołu dla net.msmq adres podstawowy do użycia tego niestandardowego powiązania.  
  
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
  
 Poniższy przykład kodu umożliwia włączenie trwałości dla obu usług przez dodanie <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> zachowania do usługi i określanie parametrów połączenia dla bazy danych trwałości.  
  
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
 W tym przykładzie wymaga następujących składników.  
  
1.  Internetowe usługi informacyjne.  
  
2.  Internetowe usługi informacyjne -> zgodność z narzędziami zarządzania usług IIS 6.0 -> Zgodność metabazy usług IIS 6.0 konfiguracji.  
  
3.  Usługi sieci World Wide Web -> Tworzenie aplikacji ASP.NET -> funkcje.  
  
4.  Serwer kolejki (MSMQ) wiadomości firmy Microsoft.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Konfigurowanie bazy danych trwałości i katalog wyników.  
  
    1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
    2.  Przejdź do folderu dla tego przykładu, a następnie uruchom Setup.cmd.  
  
2.  Konfigurowanie aplikacji wirtualnej.  
  
    1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, zarejestrować platformę ASP.NET, uruchamiając następujące polecenie.  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i wybierając **Uruchom jako administrator**.  
  
    3.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik DurableDuplex.sln.  
  
3.  Konfigurowanie usługi kolejki.  
  
    1.  Aby uruchomić klienta DurableDuplex, naciśnij klawisz F5.  
  
    2.  Otwórz **Zarządzanie komputerem** konsoli, uruchamiając `Compmgmt.msc` z wiersza polecenia.  
  
    3.  Rozwiń węzeł **usługi i aplikacje**, **usługi kolejkowania komunikatów**. **Kolejki prywatne**.  
  
    4.  Kliknij prawym przyciskiem myszy kolejek durableduplex/service1.xamlx i durableduplex/service2.xamlx i wybierz **właściwości**.  
  
    5.  Wybierz **zabezpieczeń** karcie i umożliwić **wszyscy odbieranie wiadomości**, **wglądu do wiadomości** i **wysyłania komunikatu** uprawnienia dla obu kolejek.  
  
    6.  Otwórz Menedżera internetowych usług informacyjnych (IIS).  
  
    7.  Przejdź do **serwera**, **witryny**, **domyślnej witryny sieci Web**, **prywatnej**, **trwałe dupleksu** i wybierz pozycję **Zaawansowane opcje**.  
  
    8.  Zmień **włączone protokoły** do **http,net.msmq**.  
  
4.  Uruchom próbkę.  
  
    1.  Przejdź do http://localhost/private/durableduplex/service1.xamlx i http://localhost/private/durableduplex/service2.xamlx aby upewnić się, że obie te usługi są uruchomione.  
  
    2.  Naciśnij klawisz F5, aby uruchomić DurableDuplexClient.  
  
         Po zakończeniu wymiany trwałe dupleksu wiadomości result.xml pliku zostanie zapisana w folderze C:\Inbox i zawiera wynik wymiany wiadomości.  
  
#### <a name="to-cleanup-optional"></a>Do oczyszczania (opcjonalnie)  
  
1.  Uruchom Cleanup.cmd.  
  
    1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
    2.  Przejdź do folderu dla tego przykładu, a następnie uruchom Cleanup.cmd.  
  
2.  Usuń aplikację wirtualną dla usług.  
  
    1.  Otwórz Menedżera usług Internet Information Services (IIS), uruchamiając `Inetmgr.exe` z wiersza polecenia.  
  
    2.  Przejdź do domyślnej witryny sieci Web i Usuń **prywatnej** katalogu wirtualnego.  
  
3.  Usuń kolejek skonfigurowanej na potrzeby tego przykładu.  
  
    1.  Otwórz konsolę Zarządzanie komputerem, uruchamiając `Compmgmt.msc` z wiersza polecenia.  
  
    2.  Rozwiń węzeł **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.  
  
    3.  Usuwanie kolejek durableduplex/service1.xamlx i durableduplex/service2.xamlx.  
  
4.  Usuń katalog C:\Inbox.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`