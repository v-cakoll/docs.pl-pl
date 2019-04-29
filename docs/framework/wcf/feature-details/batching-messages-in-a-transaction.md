---
title: Tworzenie partii komunikatów w ramach transakcji
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: 2d820087973e689514a0a19a7adc912f49e9d0a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596781"
---
# <a name="batching-messages-in-a-transaction"></a>Tworzenie partii komunikatów w ramach transakcji
Umieszczonych w kolejce aplikacji używać transakcji, aby zapewnić poprawność i niezawodne dostarczanie wiadomości. Transakcje, jednak są kosztownych operacji i może znacznie zmniejszyć wydajność obsługi wiadomości. Jednym ze sposobów, aby zwiększyć przepływność komunikatów jest korzystać z aplikacji, Odczyt i przetwarzanie wielu komunikatów w ramach jednej transakcji. Jest to kompromis między wydajnością i odzyskiwanie: w miarę zwiększania liczby wiadomości w partii to samo dotyczy ilość pracy odzyskiwania, który wymagany, jeśli wycofywania transakcji. Należy zauważyć różnicę między tworzenie partii komunikatów w transakcji i sesji. A *sesji* to grupa pokrewne wiadomości, które są przetwarzane przez jedną aplikację i zadeklarowane jako pojedyncza jednostka. Sesje są zazwyczaj stosowane, gdy grupy pokrewne wiadomości, które muszą być przetwarzane razem. Na przykład jest online zakupów witryna sieci Web. *Partie* będą używani do przetwarzania wielu, niepowiązanych komunikatów w taki sposób, że wzrost komunikatu przepływności. Aby uzyskać więcej informacji o sesjach, zobacz [grupowanie komunikatów w kolejce w sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Komunikaty w partii są również przetwarzane przez jedną aplikację i zadeklarowane jako pojedynczą jednostkę, ale może być Brak relacji między komunikatami w partii. Tworzenie partii komunikatów w ramach transakcji jest optymalizacji, która nie zmienia sposobu uruchamiania aplikacji.  
  
## <a name="entering-batching-mode"></a>Wprowadzanie tryb dzielenia na partie  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior> Formantów zachowanie punktu końcowego, przetwarzanie wsadowe. Dodawanie zachowania punktu końcowego do punktu końcowego usługi informuje Windows Communication Foundation (WCF) do komunikatów usługi batch w ramach transakcji. Nie wszystkie komunikaty wymagają transakcji, dzięki czemu tylko komunikaty, które wymagają transakcji są umieszczane w zadaniu wsadowym i wyłącznie wiadomości wysyłane z operacji oznaczone `TransactionScopeRequired`  =  `true` i `TransactionAutoComplete`  =  `true` są rozważyć partii. Jeśli wszystkie operacje na kontrakt usługi są oznaczone znakiem `TransactionScopeRequired`  =  `false` i `TransactionAutoComplete`  =  `false`, a następnie nigdy nie wprowadził przetwarzanie wsadowe w trybie.  
  
## <a name="committing-a-transaction"></a>Zatwierdzanie transakcji  
 Wsadowa transakcja została zatwierdzona, w oparciu o następujące czynności:  
  
- `MaxBatchSize`. Właściwość <xref:System.ServiceModel.Description.TransactedBatchingBehavior> zachowanie. Ta właściwość określa maksymalną liczbę wiadomości, które są umieszczane w zadaniu wsadowym. Po osiągnięciu tej liczby partii jest zatwierdzona. Jest to wartość nie jest ścisłe ograniczenie, istnieje możliwość zatwierdzić partii przed otrzymaniem tej liczby komunikatów.  
  
- `Transaction Timeout`. Po upływie limitu czasu transakcji 80 procent, dba partii i utworzono nową partię. Oznacza to, że jeśli 20 procent lub mniej czasu, biorąc pod uwagę dla transakcji ukończyć pozostaje, dba partii.  
  
- `TransactionScopeRequired`. Podczas przetwarzania partię komunikatów, jeśli WCF znajdzie taki, który ma `TransactionScopeRequired`  =  `false`, zatwierdzeń usługi batch i ponownie otwiera nową partię po otrzymaniu pierwszej wiadomości z `TransactionScopeRequired`  =  `true` i `TransactionAutoComplete`  = `true`.  
  
- Jeśli istnieją nie więcej wiadomości w kolejce, a następnie dba bieżącej partii nawet wtedy, gdy `MaxBatchSize` nie został osiągnięty lub nie upłynął limit czasu transakcji 80 procent.  
  
## <a name="leaving-batching-mode"></a>Pozostawienie tryb dzielenia na partie  
 Jeśli wiadomość w usłudze batch spowoduje przerwanie transakcji, wykonywane są następujące kroki:  
  
1. Całą partię komunikatów jest wycofywana.  
  
2. Komunikaty są odczytywane po kolei, dopóki liczba wiadomości, przeczytaj przekracza dwukrotnie maksymalny rozmiar partii.  
  
3. Tryb partii jest ponowne wprowadzenie.  
  
## <a name="choosing-the-batch-size"></a>Wybierając rozmiar partii  
 Rozmiar partii jest zależne od aplikacji. Metoda empiryczne jest najlepszym sposobem na rozmiar optymalne partii dla aplikacji. Należy pamiętać, wybierając rozmiar partii, aby wybrać rozmiar zgodnie z modelem rzeczywiste wdrożenie Twojej aplikacji. Na przykład podczas wdrażania aplikacji, jeśli potrzebujesz programu SQL server na komputerze zdalnym i transakcji, która obejmuje kolejki i programu SQL server, następnie rozmiar partii najlepiej zależy od tego dokładnej konfiguracji uruchamiania.  
  
## <a name="concurrency-and-batching"></a>Współbieżność i dzielenia na partie  
 W celu zwiększenia przepływności, możesz mieć wiele instancji uruchamiać jednocześnie. Ustawiając `ConcurrencyMode.Multiple` w `ServiceBehaviorAttribute`, możesz włączyć równoczesne przetwarzanie wsadowe.  
  
 *Usługa ograniczania* jest zachowanie usługi, który jest używany do wskazania, ile maksymalna współbieżnych wywołań w usłudze. W przypadku użycia za pomocą adapterów przetwarzania wsadowego, jest interpretowany jak można uruchamiać wiele równoczesnych partii. Jeśli nie ustawiono ograniczenie usługi, usługi WCF domyślnie maksymalna współbieżnych wywołań do 16. W związku z tym Jeśli przetwarzanie wsadowe zachowanie zostały dodane domyślnie, maksymalnie 16 partii może być aktywne w tym samym czasie. Zaleca się Dostosowywanie ograniczenie usługi i przetwarzanie wsadowe w oparciu o pojemności. Na przykład jeśli pożądane jest partii 20 kolejki jest 100 wiadomości, o maksymalnej współbieżnych wywołań, ustaw 16 nie jest przydatne ponieważ w zależności od przepustowości, 16 transakcji może być aktywny, podobnie jak niemający dzielenia na partie włączona. W związku z tym gdy dostrajanie wydajności, nie mają równoczesne przetwarzanie wsadowe lub mieć równoczesne przetwarzanie wsadowe o rozmiarze ograniczania prawidłowe usługi.  
  
## <a name="batching-and-multiple-endpoints"></a>Przetwarzanie wsadowe i wiele punktów końcowych  
 Punkt końcowy składa się z adresu i kontrakt. Może istnieć wiele punktów końcowych, które współużytkują tego samego powiązania. Istnieje możliwość dla dwóch punktach końcowych pozwala na udostępnianie tego samego powiązania i nasłuchiwania identyfikator (URI) lub adres kolejki. Jeśli dwa punkty końcowe są odczytywania z tej samej kolejki i transakcyjne dzielenia na partie zachowanie jest dodawany do konfliktu w usłudze batch, które mogą pojawić się rozmiary określone oba punkty końcowe. Ten problem jest rozwiązany przez zaimplementowanie dzielenia na partie przy użyciu wybranego rozmiaru partii minimalny między dwa zachowania łączenia we wsady transakcyjne. W tym scenariuszu jeśli jeden z punktów końcowych nie określa transakcyjnego przetwarzania wsadowego, następnie zarówno punkty końcowe nie użyje dzielenia na partie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić `TransactedBatchingBehavior` w pliku konfiguracji.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 Poniższy przykład pokazuje, jak określić <xref:System.ServiceModel.Description.TransactedBatchingBehavior> w kodzie.  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));
     
     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
