---
title: Buforowane odbieranie
ms.date: 03/30/2017
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
ms.openlocfilehash: b95577c71493275f30703b4366fab32a51097bd2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526807"
---
# <a name="buffered-receive"></a>Buforowane odbieranie
W tym przykładzie przedstawiono sposób instalowania i konfigurowania funkcji odbierania buforowaną w Windows Workflow Foundation (WF). Buforowane odbieranie umożliwia autorowi przepływu pracy utworzyć przepływ pracy bez konieczności martwienia się o kolejności, w jakiej komunikaty są odbierane. Funkcja odbierania buforowanego buforuje wiadomości lokalnie i przekazuje je, gdy przepływ pracy jest gotowa do ich odebrania.  
  
## <a name="demonstrates"></a>Demonstracje  
 Przetwarzanie komunikatów poza kolejnością przy użyciu buforowanego odbierać przy użyciu działań dotyczących komunikatów.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>Dyskusja  
 W tym przykładzie Usługa Windows Communication Foundation (WCF) jest implementowany przy użyciu [!INCLUDE[wf1](../../../../includes/wf1-md.md)] i ma sekwencji <xref:System.ServiceModel.Activities.Receive> działań. Ten przepływ pracy modeli pożyczki prosty proces zatwierdzania, gdy przepływ pracy oczekuje trzech powiadomienia dotyczące pożyczek w celu uzyskania zatwierdzenia. Aplikacja kliencka Windows Communication Foundation (WCF) wysyła trzy powiadomienia skorelowane w odwrotnej kolejności usługa oczekuje. Funkcją buforowaną odbierania jest włączony na usługę i każdy komunikat poza kolejnością jest buforowana na usługę i przetwarzane za pomocą przepływu pracy staje się gotowe do jej otrzymania.  
  
 Funkcja odbierania buforowanego wymaga <xref:System.ServiceModel.Activities.ReceiveContent> pomocy technicznej firmy powiązanie, w związku z tym usługa używa <xref:System.ServiceModel.NetMsmqBinding>. Żadna specjalna konfiguracja jest wymagana do powiązania, więc są używane wartości domyślne.  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 Usługa udostępnia również metadane dla usługi przy użyciu <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
 Podobnie, punkt końcowy klienta jest konfigurowana przy użyciu <xref:System.ServiceModel.NetMsmqBinding>. Kod klienta i konfiguracji jest generowany przy użyciu **Dodaj odwołanie do usługi** funkcji programu Visual Studio. Poniższy przykład jest punktem końcowym wygenerowanego klienta, w pliku App.config.  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 Ten przykładowy skrypt wymaga włączenia następujących składników Windows:  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Zgodność z narzędziami zarządzania, metabazy i zgodności konfiguracji  
  
3.  Usługi World Wide Web, funkcje tworzenia aplikacji i platformy ASP.NET  
  
4.  Microsoft Message kolejki serwer (MSMQ)  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1.  W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, Zarejestruj aplikację ASP.NET, wpisując `aspnet_regiis –I` i naciśnij klawisz ENTER.  
  
2.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako Administrator.  
  
3.  Otwórz LoanService.sln.  
  
4.  Po wyświetleniu monitu, jeśli chcesz tworzyć katalogi wirtualne LoanService projektu, wybierz opcję **tak**.  
  
#### <a name="to-set-up-the-service-queues"></a>Aby skonfigurować usługi kolejki  
  
1.  Naciśnij klawisz F5, aby uruchomić aplikację LoanClient, która tworzy kolejki i aktywuje usługę zdefiniowane w Service1.xamlx.  
  
2.  Otwórz **Zarządzanie komputerem** konsoli, uruchamiając Compmgmt.msc z poziomu wiersza polecenia.  
  
3.  W **Zarządzanie komputerem** konsoli, rozwiń **usługi**, **aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne** .  
  
4.  Kliknij prawym przyciskiem myszy kolejki loanservice/service1.xamlx, a następnie wybierz pozycję **właściwości**.  
  
5.  Wybierz **zabezpieczeń** karta i Dodaj **wszyscy odbiera komunikat o**, **wglądu do wiadomości** i **wysyłania komunikatu** uprawnienia.  
  
6.  Otwórz [!INCLUDE[iis60](../../../../includes/iis60-md.md)] menedżera.  
  
7.  Przejdź do **serwera**, **witryn**, **domyślnej witryny sieci Web**, **prywatnej**, **LoanService** i wybierz  **Opcje zaawansowane**  
  
8.  Zmiana **włączone protokoły** jako **http**, **net.msmq**.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Przejdź do http://localhost/private/loanservice/service1.xamlx aby upewnić się, że usługa jest uruchomiona.  
  
2.  Naciśnij klawisz F5, aby uruchomić aplikację LoanClient. Po ukończeniu przepływu pracy powinien zostać zapisany plik out.txt C:\Inbox zawierającego wynik wymianę komunikatów.  
  
#### <a name="to-clean-up"></a>Aby wyczyścić  
  
1.  Otwórz **Zarządzanie komputerem** konsoli, uruchamiając Compmgmt.msc z poziomu wiersza polecenia.  
  
2.  Rozwiń **usługi** i **aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.  
  
3.  Usuń kolejkę loanservice/service1.xamlx.  
  
4.  Usuń katalog C:\Inbox.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
