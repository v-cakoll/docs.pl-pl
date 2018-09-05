---
title: Kanały programu WCF z obsługą elementu ReceiveContext
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: d7f80d0874606129876fbf7dfa30c0327680b922
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515933"
---
# <a name="receivecontext-enabled-wcf-channels"></a>Kanały programu WCF z obsługą elementu ReceiveContext
W tym przykładzie przedstawiono przydatność <xref:System.ServiceModel.Channels.ReceiveContext>— włączone kanały programu WCF. Przykład implementuje usługi można znaleźć iloczyn dwóch liczb przy użyciu kanału NetMSMQ.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> Klasa umożliwia aplikacji zdecyduj, czy dostęp do wiadomości, lub pozostaw to pole w kolejce do dalszego przetwarzania, nawet po zakończeniu poddane treści wiadomości. W tym przykładzie klient wysyła losowych liczb całkowitych do kolejkę transakcyjną. `ProductCalculator` Usługa odbiera komunikaty i sprawdza treść wiadomości, które są liczbami całkowitymi, aby ustalić, czy produkt może zostać obliczony. Jeśli operacja usługi nie może obliczyć produktu, komunikat jest ponownie umieszczone w kolejce i mogą być ponownie odbierane przez usługę nasłuchiwać kolejki.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Upewnij się, że zainstalowano program Microsoft usługi kolejkowania komunikatów (MSMQ).  
  
    1.  Aby zainstalować usługę MSMQ na [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:  
  
        1.  W **Menedżera serwera**, kliknij przycisk **funkcji**.  
  
        2.  W okienku po prawej stronie w obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.  
  
        3.  W oknie wynikowy rozwiń **usługi kolejkowania komunikatów**.  
  
        4.  Rozwiń **usługi kolejkowania komunikatów**.  
  
        5.  Kliknij przycisk **integracji z usługami katalogu** (na komputerach przyłączonych do domeny), a następnie kliknij przycisk **obsługi protokołu HTTP**.  
  
        6.  Kliknij przycisk **dalej**, a następnie kliknij przycisk **zainstalować**.  
  
    2.  Aby zainstalować usługę MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)]:  
  
        1.  Otwórz **Panel sterowania**.  
  
        2.  Kliknij przycisk **programy** a następnie w obszarze **programy i funkcje**, kliknij przycisk **Włącz lub wyłącz funkcje Windows**.  
  
        3.  Rozwiń **serwera Microsoft kolejki komunikatów (MSMQ)**, rozwiń węzeł **Microsoft kolejki komunikatów (MSMQ) Server Core**, a następnie zaznacz pola wyboru dla następujących funkcji usługi kolejkowania komunikatów do zainstalowania:  
  
            -   Serwer usługi kolejkowania komunikatów  
  
            -   Usługa MSMQ domeny integracji usług Active Directory (na komputery przyłączone do domeny)  
  
            -   Obsługa protokołu HTTP w usłudze MSMQ  
  
        4.  Kliknij przycisk **OK**.  
  
        5.  Jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, kliknij przycisk **OK** do ukończenia instalacji.  
  
2.  Upewnij się, że [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jest zainstalowany na komputerze.  
  
3.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania ReceiveContextProductGenerator.sln.  
  
4.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
5.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.
