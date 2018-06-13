---
title: Tworzenie partii komunikatów w ramach transakcji
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: 5c8a69c10ddb8b6be35bdd39e3feb91495279be3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493936"
---
# <a name="batching-messages-in-a-transaction"></a>Tworzenie partii komunikatów w ramach transakcji
Aplikacje umieszczonych w kolejce używać transakcji, aby zapewnić poprawność i niezawodne dostarczanie komunikatów. Transakcje, jednak operacje kosztowne i może znacznie zmniejszyć wydajność obsługi wiadomości. Jednym ze sposobów poprawy wydajności przesyłania wiadomości jest używana aplikacja odczytywać i przetwarzać wiele komunikatów w ramach jednej transakcji. Jest kompromis między wydajnością i odzyskiwanie: jak zwiększa liczbę komunikatów w partii, co powoduje ilość pracy odzyskiwania, który wymagany, jeśli wycofywania transakcji. Należy zauważyć różnicę między tworzenie partii komunikatów w transakcji i sesje. A *sesji* jest grupowanie powiązanych wiadomości, które są przetwarzane przez pojedynczą aplikacją i zatwierdzona jako pojedyncza jednostka. Sesje są zazwyczaj stosowane, gdy grupy powiązane komunikaty, które muszą zostać przetworzone jednocześnie. Na przykład jest online zakupów witryna sieci Web. *Partie* są używane do przetwarzania wielu, niepowiązanych wiadomości w taki sposób, że zwiększa komunikatu przepływności. Aby uzyskać więcej informacji o sesji, zobacz [grupowania w kolejce wiadomości w sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Komunikaty w partii są również przetwarzane przez pojedynczą aplikacją i zatwierdzone jako pojedyncza jednostka, ale może być Brak relacji między komunikatami w partii. Tworzenie partii komunikatów w ramach transakcji jest optymalizacji, która nie zmienia sposób uruchamiania aplikacji.  
  
## <a name="entering-batching-mode"></a>Wprowadzanie przetwarzanie wsadowe tryb  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior> Kontroli zachowania punktu końcowego przetwarzania wsadowego. Dodawanie tego zachowania punktu końcowego na punkt końcowy usługi określa, że Windows Communication Foundation (WCF) do partii komunikatów w ramach transakcji. Nie wszystkie wiadomości wymaga transakcji, dzięki czemu można tylko komunikaty, które wymagają transakcji są umieszczane w partii i oznaczone wyłącznie wiadomości wysyłane z operacji `TransactionScopeRequired`  =  `true` i `TransactionAutoComplete`  =  `true` są uwzględnione w partii. Jeśli wszystkie operacje w kontrakcie usługi są oznaczone ikoną z `TransactionScopeRequired`  =  `false` i `TransactionAutoComplete`  =  `false`, a następnie przetwarzanie wsadowe tryb nigdy nie wprowadzono.  
  
## <a name="committing-a-transaction"></a>Zatwierdzanie transakcji  
 Transakcji wsadowej dba oparte na następujących czynności:  
  
-   `MaxBatchSize`. Właściwość <xref:System.ServiceModel.Description.TransactedBatchingBehavior> zachowania. Ta właściwość określa maksymalną liczbę wiadomości, które są umieszczane w partii. Po osiągnięciu tej liczby dba partii. Jest to wartość nie jest ścisłym limit, można przekazać partii przed otrzymaniem to liczba komunikatów.  
  
-   `Transaction Timeout`. Po upływie limitu czasu transakcji 80 procent, dba partii i utworzeniu nowej instancji. Oznacza to, że jeśli 20% lub mniej czasu dla transakcji ukończyć pozostaje, dba partii.  
  
-   `TransactionScopeRequired`. Podczas przetwarzania wsadowego komunikatów, jeśli WCF znalezienia punktu, który ma `TransactionScopeRequired`  =  `false`, zatwierdza partii i ponownie otwiera nową instancję po otrzymaniu pierwszego komunikatu z `TransactionScopeRequired`  =  `true` i `TransactionAutoComplete`  = `true`.  
  
-   Jeśli nie więcej istnieją wiadomości w kolejce, a następnie bieżącej partii został przekazany, nawet jeśli `MaxBatchSize` nie został osiągnięty lub nie upłynął limit czasu transakcji 80 procent.  
  
## <a name="leaving-batching-mode"></a>Pozostawienie przetwarzanie wsadowe tryb  
 Jeśli komunikat w partii powoduje przerwanie transakcji, zostaną wykonane następujące kroki:  
  
1.  Całą partię komunikatów zostanie wycofana.  
  
2.  Wiadomości są odczytywane pojedynczo, dopóki liczba wiadomości przekracza dwukrotnie maksymalny rozmiar wsadu.  
  
3.  Tryb partii jest ponowne wprowadzenie.  
  
## <a name="choosing-the-batch-size"></a>Wybieranie rozmiaru partii  
 Rozmiar partii jest zależny od aplikacji. Metoda empiryczne jest najlepszym sposobem na rozmiar partii optymalne dla aplikacji. Należy pamiętać, wybierając rozmiar partii, aby wybrać rozmiar zgodnie z modelu rzeczywiste wdrożenie aplikacji. Na przykład w przypadku wdrażania aplikacji, jeśli potrzebujesz programu SQL server na komputerze zdalnym i transakcji obejmującej kolejki i SQL server, następnie rozmiar partii najlepiej zależy, uruchamiając tego dokładnej konfiguracji.  
  
## <a name="concurrency-and-batching"></a>Współbieżność i przetwarzanie wsadowe  
 W celu zwiększenia przepływności, może również mieć wiele instancji uruchamiać jednocześnie. Przez ustawienie `ConcurrencyMode.Multiple` w `ServiceBehaviorAttribute`, możesz włączyć równoczesnych przetwarzanie wsadowe.  
  
 *Usługa ograniczania* jest zachowanie usługi, który jest używany do określania, ile maksymalna współbieżnych wywołań w usłudze. W przypadku użycia z przetwarzanie wsadowe, jest interpretowany jak można uruchomić wiele równoczesnych partie. Jeśli nie ustawiono ograniczenie usługi, WCF domyślnie maksymalna równoczesnych wywołań 16. W związku z tym Jeśli przetwarzanie wsadowe zachowanie dodano domyślnie, maksymalnie 16 partii zadań mogą być aktywne w tym samym czasie. Najlepiej dostroić ograniczania usługi i przetwarzanie wsadowe oparte na wydajność. Na przykład jeśli kolejki jest 100 wiadomości i wymagane jest partii 20, o maksymalnej równoczesnych wywołań ustawioną 16 nie jest przydatne ponieważ w zależności od przepustowości, 16 transakcji może być aktywne, podobnie jak nie posiadają przetwarzanie wsadowe włączona. W związku z tym podczas dostosowywania wydajności, nie ma równoczesnych przetwarzanie wsadowe lub mieć równoczesnych przetwarzanie wsadowe o rozmiarze ograniczania prawidłowe usługi.  
  
## <a name="batching-and-multiple-endpoints"></a>Przetwarzanie wsadowe i wiele punktów końcowych  
 Punkt końcowy składa się z adresu i kontrakt. Może istnieć wiele punktów końcowych, które współużytkują to samo powiązanie. Istnieje możliwość dwa punkty końcowe udostępnianie tego samego powiązania do nasłuchiwania identyfikator URI (Uniform Resource) lub adres kolejki. Jeśli dwa punkty końcowe są czytania z tej samej kolejki i transakcyjnego przetwarzania wsadowego zachowanie jest dodawany do konflikt w partii, które mogą pojawić się rozmiary określone oba punkty końcowe. Jest to rozwiązane przez wdrożenie, przetwarzanie wsadowe przy użyciu podanego rozmiaru partii minimalnego między dwa transakcyjnego łączenia we wsady zachowania. W tym scenariuszu jeśli jeden z punktów końcowych nie określa transakcyjnego przetwarzania wsadowego, następnie oba punkty końcowe nie użyje przetwarzanie wsadowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób określić `TransactedBatchingBehavior` w pliku konfiguracji.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 Poniższy przykład przedstawia sposób określić <xref:System.ServiceModel.Description.TransactedBatchingBehavior> w kodzie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
