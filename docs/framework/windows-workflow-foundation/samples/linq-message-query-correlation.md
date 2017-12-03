---
title: "Korelacja kwerendy komunikatów LINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 124f76012f342eff9b11a7208df1103cded3843c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="linq-message-query-correlation"></a>Korelacja kwerendy komunikatów LINQ
W tym przykładzie pokazano, jak wykonać korelacji na podstawie zawartości przy użyciu niestandardowego <xref:System.ServiceModel.Dispatcher.MessageQuery> implementacji, a nie dostarczane przez system <xref:System.ServiceModel.XPathMessageQuery>.  
  
## <a name="demonstrates"></a>Demonstracje  
 Niestandardowe <xref:System.ServiceModel.Dispatcher.MessageQuery>, na podstawie zawartości korelacji.  
  
## <a name="discussion"></a>Omówienie  
 W tym przykładzie pokazano, jak rozszerzyć z <xref:System.ServiceModel.Dispatcher.MessageQuery> klasy podstawowej na potrzeby korelacji. Implementacja niestandardowa `LinqMessageQuery`, umożliwia użytkowników w celu zapewnienia XName można znaleźć w komunikacie przy użyciu XLinq. Dane pobrane przez zapytanie służy do wysłania wiadomości do wystąpienia przepływu pracy odpowiednie klucz korelacji.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Ten przykład przedstawia usługi przepływu pracy przy użyciu punktów końcowych HTTP. Można dodać do uruchomienia, to przykładowa, odpowiednich list ACL adresu URL (zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje), uruchamiając program Visual Studio jako Administrator lub, wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, aby dodać odpowiednich list ACL. Upewnij się, czy użytkownika domena i nazwa użytkownika są zastępowane.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  Po dodaniu listy ACL adresu URL, wykonaj następujące kroki.  
  
    1.  Skompiluj rozwiązanie.  
  
    2.  Ustawianie wielu projektów uruchamiania prawym przyciskiem myszy rozwiązanie i wybierając **Ustaw projekty startowe**. Dodaj **usługi** i **klienta** (w tej kolejności) jako wiele projektów rozruchu.  
  
    3.  Uruchom aplikację. W konsoli klienta przedstawia przepływ pracy zamówienia wysyłanie i odbieranie identyfikator zamówienia zakupu oraz następnie potwierdzenie zamówienia. W oknie usługi są wyświetlane aktualnie przetwarzanych żądań.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
