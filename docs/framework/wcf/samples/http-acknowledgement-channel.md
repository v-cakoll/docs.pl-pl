---
title: Kanał potwierdzania HTTP
ms.date: 03/30/2017
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
ms.openlocfilehash: d83f3aa590471aa3d83b8f7bd1464ec1e6e106fc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856239"
---
# <a name="http-acknowledgement-channel"></a>Kanał potwierdzania HTTP
Kanał potwierdzania HTTP jest przykładem warstwowej kanału, który zmienia jednokierunkowe wzorzec przesyłania komunikatów dotyczących, co umożliwia usłudze potwierdzić lub odmówić wiadomości przychodzących, a nie są automatycznie wysyłane potwierdzenie w przypadku otrzymania. Kanał potwierdzania HTTP umożliwia także usługi do potwierdzenia opóźnienie do momentu może sprawić, że gwarancji biznesowej, otrzymasz wiadomość.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Channels.ReceiveContext>, Przykład warstwowej channel (kanał potwierdzania HTTP).  
  
## <a name="discussion"></a>Dyskusja  
 Kanał potwierdzania HTTP implementuje <xref:System.ServiceModel.Channels.ReceiveContext> przekształcenie wzorzec przesyłania komunikatów dotyczących żądanie odpowiedź HTTP do wzorca jednokierunkowe opóźnione potwierdzenia. Za pomocą tego nowego wzorca, usługa zapewnia przetwarzanie komunikatów wysyłanie potwierdzenia w formie kod stanu HTTP OK, 200, bez blokowania klienta, aż do ukończenia przetwarzania wiadomości, lub wysłać komunikat o błędzie do klienta w postaci HTTP Wewnętrzny serwer błąd kod stanu 500. Na przykład usługi można wysyłać potwierdzenia po zapisaniu wiadomość do kolejki, a następnie kontynuować przetwarzanie wiadomości asynchronicznie. W tym scenariuszu klient może mieć pewność, że jego wiadomości zostały przetworzone przez usługę, w co najmniej raz Jeśli ponownie program wysyłane każdy komunikat do momentu otrzymania potwierdzenia z usługi. Należy zauważyć, że jeśli usługa wymaga komunikatów szybko asynchronicznych przetwarzania za pośrednictwem protokołu HTTP bez żadnych gwarancji, przetwarzania, a następnie <xref:System.ServiceModel.Channels.OneWayBindingElement> się bardziej odpowiednim wyborem.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> Służy do przechowywania wiadomości w miejscu, gdy okaże się, czy wiadomości mogą być przetwarzane w usłudze. Możliwość pomyślnie przetworzyć komunikatu usługi jest wskazywane za pomocą wywołania zakończone na <xref:System.ServiceModel.Channels.ReceiveContext> obiekt, który wysyła kod stanu HTTP OK i tego, czy usługa może przetwarzać komunikat jest wskazywany przez wywołanie metody <xref:System.ServiceModel.Channels.ReceiveContext>firmy `Abandon` Metoda <xref:System.ServiceModel.Channels.ReceiveContext> obiektu, który wysyła kod stanu błędu wewnętrznego serwera HTTP.  
  
 W tym przykładzie klient żąda informacji przetwarzania, wysyłając identyfikator pracownika. Po stronie usługi Jeśli otrzymany identyfikator pracownika jest większa niż 50, usługa wysyła kod stanu HTTP 500 (wewnętrzny błąd serwera) z powrotem do klienta, w przeciwnym razie zakłada się, że przetwarzanie może zostać wykonana pomyślnie i wysyła kod stanu HTTP 200 ( Pomyślne) do klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] z uprawnieniami administratora.  
  
2.  Otwórz **HttpAckChannel** rozwiązania.  
  
3.  Uruchom nowe wystąpienie klasy **usługi** projektu, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**i wybierając polecenie **debugowania**, **Uruchom nowe wystąpienie** z menu kontekstowego.  
  
4.  Uruchom nowe wystąpienie klasy **klienta** projektu, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**i wybierając polecenie **debugowania**, i **Uruchom nowe wystąpienie** z menu kontekstowego.  
  
5.  Gdy usługa została uruchomiona, naciśnij klawisz ENTER w oknie klienta, aby umożliwić klientowi wysłać komunikatu do usługi.  
  
6.  Pierwszy komunikat jest przetwarzany w usłudze, a kod stanu HTTP OK wysyłane z powrotem do klienta.  
  
7.  Drugi komunikat zakończy się niepowodzeniem, a kod stanu błędu wewnętrznego serwera HTTP wysyłane z powrotem do klienta, który wywołuje <xref:System.ServiceModel.CommunicationException> na komputerze klienckim.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
