---
title: "Obsługą elementu ReceiveContext kanały programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 729bf8bd1371bf64b9b05a235331120608824083
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="receivecontext-enabled-wcf-channels"></a>Obsługą elementu ReceiveContext kanały programu WCF
W tym przykładzie pokazano przydatność <xref:System.ServiceModel.Channels.ReceiveContext>— włączone kanały programu WCF. Przykład implementuje usługi można znaleźć iloczyn dwóch liczb za pomocą kanału NetMSMQ.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> Klasa umożliwia aplikacji zdecyduj, czy dostęp do wiadomości lub pozostaw w kolejce dla dalszego przetwarzania, nawet po sprawdzeniu treści wiadomości. W tym przykładzie klient wysyła losowych liczb całkowitych do kolejką transakcyjną. `ProductCalculator` Usługa odbiera komunikaty i sprawdza treść wiadomości, które są liczbami całkowitymi, aby określić, czy można obliczyć produktu. Jeśli operacja usługi nie zawiera produktu, wiadomość jest przywracane do kolejki i mogą być ponownie odbierane przez usługę nasłuchiwania w kolejce.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Upewnij się, że zainstalowano usługi kolejkowania wiadomości firmy Microsoft (MSMQ).  
  
    1.  Aby zainstalować usługi MSMQ na [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:  
  
        1.  W **Menedżera serwera**, kliknij przycisk **funkcji**.  
  
        2.  W prawym okienku w obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.  
  
        3.  W oknie wynikowy rozwiń **usługi kolejkowania komunikatów**.  
  
        4.  Rozwiń węzeł **komunikatów usługi kolejkowania wiadomości**.  
  
        5.  Kliknij przycisk **integracji z usługami katalogu** (na komputerach przyłączonych do domeny), a następnie kliknij przycisk **obsługi protokołu HTTP**.  
  
        6.  Kliknij przycisk **dalej**, a następnie kliknij przycisk **zainstalować**.  
  
    2.  Aby zainstalować usługi MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)]:  
  
        1.  Otwórz **Panel sterowania**.  
  
        2.  Kliknij przycisk **programy** , a następnie w obszarze **programy i funkcje**, kliknij przycisk **włączyć lub wyłączyć funkcje systemu Windows**.  
  
        3.  Rozwiń węzeł **serwera Microsoft kolejki komunikatów (MSMQ)**, rozwiń węzeł **Microsoft kolejki komunikatów (MSMQ) Server Core**, a następnie zaznacz pola wyboru dla następujące funkcje usługi kolejkowania komunikatów do zainstalowania:  
  
            -   Serwer usługi kolejkowania komunikatów  
  
            -   Usługa MSMQ domeny integracji usług Active Directory (na komputerach przyłączonych do domeny)  
  
            -   Obsługa protokołu HTTP w usłudze MSMQ  
  
        4.  Kliknij przycisk **OK**.  
  
        5.  Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.  
  
2.  Upewnij się, że [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jest zainstalowany na komputerze.  
  
3.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania ReceiveContextProductGenerator.sln.  
  
4.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
5.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.
