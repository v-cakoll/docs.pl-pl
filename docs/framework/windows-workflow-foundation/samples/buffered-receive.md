---
title: Buforowane odbierania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 974c053c3d5aae517e6acbd0e61e1bb96340ee65
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="buffered-receive"></a>Buforowane odbierania
W tym przykładzie pokazano, jak instalowanie i konfigurowanie funkcję odbierania buforowane w [!INCLUDE[wf](../../../../includes/wf-md.md)]. Buforowane odbierania umożliwia autorowi przepływu pracy utworzyć przepływ pracy bez konieczności martwić o kolejność, w którym są odbierane wiadomości. Funkcja odbierania buforowanego buforuje wiadomości lokalnie i dostarcza je, gdy przepływ pracy jest gotowa do ich odebrania.  
  
## <a name="demonstrates"></a>Demonstracje  
 Przetwarzanie komunikatów poza kolejnością. przy użyciu buforowanych odbierać z działań dotyczących komunikatów.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>Omówienie  
 W tym przykładzie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługa jest wdrażana przy użyciu [!INCLUDE[wf1](../../../../includes/wf1-md.md)] i ma sekwencji <xref:System.ServiceModel.Activities.Receive> działań. Ten przepływ pracy modele pożyczki prosty proces zatwierdzania, gdy przepływ pracy oczekuje trzy powiadomienia pożyczki zatwierdzenia. A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacja kliencka wysyła trzy skorelowane powiadomienia w odwrotnej kolejności oczekuje usługi. Ponieważ funkcja buforowanego receive jest włączona w usłudze, każdy komunikat poza kolejnością jest buforowana w usłudze i przetwarzania przepływu pracy będzie gotowa do odbioru go.  
  
 Funkcja odbierania buforowanego wymaga <xref:System.ServiceModel.Activities.ReceiveContent> wsparciu powiązanie, w związku z tym usługa używa <xref:System.ServiceModel.NetMsmqBinding>. Konfiguracja nie specjalne jest wymagane dla tego powiązania, dlatego są używane wartości domyślne.  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 Usługa udostępnia również metadanych dla usługi przy użyciu <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
 Podobnie, klient punkt końcowy skonfigurowany przy użyciu <xref:System.ServiceModel.NetMsmqBinding>. Kod klienta i konfiguracji jest generowany przy użyciu **Dodaj odwołanie do usługi** funkcji [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Poniższy przykład jest punkt końcowy wygenerowanego klienta w pliku App.config.  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 W tym przykładzie wymaga włączenia następujące składniki systemu Windows:  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]Zgodność z narzędziami zarządzania metabazy i zgodności konfiguracji  
  
3.  Usługi sieci World Wide Web, funkcje tworzenia aplikacji i programu ASP.NET  
  
4.  Wiadomości firmy Microsoft (MSMQ) kolejek serwera  
  
#### <a name="to-set-up-and-build-the-sample"></a>Do ustawiania i tworzyć przykładowy kod  
  
1.  W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, zarejestrować platformę ASP.NET, wpisując `aspnet_regiis –I` i naciśnij klawisz ENTER.  
  
2.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako Administrator.  
  
3.  Otwórz LoanService.sln.  
  
4.  Po otrzymaniu monitu, jeśli chcesz utworzyć wirtualne katalogi dla projektu LoanService, wybierz **tak**.  
  
#### <a name="to-set-up-the-service-queues"></a>Aby skonfigurować usługi kolejki  
  
1.  Naciśnij klawisz F5, aby uruchomić aplikację LoanClient, która tworzy kolejek i aktywuje usługę zdefiniowane w Service1.xamlx.  
  
2.  Otwórz **Zarządzanie komputerem** konsoli, uruchamiając Compmgmt.msc z wiersza polecenia.  
  
3.  W **Zarządzanie komputerem** rozwiń **usługi**, **aplikacji**, **usługi kolejkowania komunikatów**, **kolejki prywatne** .  
  
4.  Kliknij prawym przyciskiem myszy kolejki loanservice/service1.xamlx i wybierz **właściwości**.  
  
5.  Wybierz **zabezpieczeń** karta i Dodaj **komunikat odbiera wszyscy**, **wglądu do wiadomości** i **wysyłania komunikatu** uprawnienia.  
  
6.  Otwórz [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.  
  
7.  Przejdź do **serwera**, **witryny**, **domyślnej witryny sieci Web**, **prywatnej**, **LoanService** i wybierz  **Opcje zaawansowane**  
  
8.  Zmień **włączone protokoły** jako **http**, **net.msmq**.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Przejdź do http://localhost/private/loanservice/service1.xamlx aby upewnić się, że usługa jest uruchomiona.  
  
2.  Naciśnij klawisz F5, aby uruchomić aplikację LoanClient. Po zakończeniu przepływu pracy należy można zapisać pliku out.txt C:\Inbox zawierający wynik wymiany wiadomości.  
  
#### <a name="to-clean-up"></a>Aby wyczyścić  
  
1.  Otwórz **Zarządzanie komputerem** konsoli, uruchamiając Compmgmt.msc z wiersza polecenia.  
  
2.  Rozwiń węzeł **usługi** i **aplikacji**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.  
  
3.  Usuwanie kolejki loanservice/service1.xamlx.  
  
4.  Usuń katalog C:\Inbox.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
