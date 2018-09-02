---
title: Znajdowanie asynchroniczne — przykład
ms.date: 03/30/2017
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
ms.openlocfilehash: 37edcb4d1f04eb56d3f24ca3acc3543d7f9696f5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424394"
---
# <a name="asynchronous-find-sample"></a>Znajdowanie asynchroniczne — przykład
Ten przykład pokazuje, jak za pomocą operacji znajdowanie asynchroniczne od aplikacji klienckiej.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Zaletą zgodnie z tym wzorcu projektowym to, że klient zostanie powiadomiony asynchronicznie punktów końcowych znajdujących się w wyniku żądania wyszukiwania. Aby zobaczyć, jak to działa, otwórz plik Client.cs. Uwaga <xref:System.ServiceModel.Discovery.DiscoveryClient> obiekt ma dwa delegaty dołączone do swoich programów obsługi zdarzeń. Jednego delegata jest wywoływana, gdy <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> zdarzenie jest zgłaszane i inny jest wywoływana za każdym razem <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> zdarzenie jest wywoływane. Przykład pokazuje, jak możesz użyć tego wzorca w aplikacji.  
  
> [!NOTE]
>  W tym przykładzie użyto punktów końcowych HTTP i przeprowadzić, muszą zostać dodane odpowiednie listy ACL adresu URL. Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Wykonując następujące polecenie w podwyższonym poziomem uprawnień, należy dodać odpowiednie listy ACL. Można zastąpić Twoja domena i nazwa użytkownika o wprowadzenie następujących argumentów, jeśli polecenie nie działa, ponieważ jest. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AsyncFind.sln.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
3.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz polecenia i przejdź do katalogu \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug lub \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug i uruchom Service.exe.  
  
4.  Po uruchomieniu usługi, przejdź do katalogu WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug lub \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug i uruchom Client.exe.  
  
5.  Sprawdź, czy klient jest w stanie zlokalizować i wywołania tej usługi.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>Zobacz też
