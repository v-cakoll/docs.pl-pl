---
title: Tworzenie partii komunikatów w ramach transakcji
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: be9661525c960ae558d21b05781007b81b8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185439"
---
# <a name="batching-messages-in-a-transaction"></a>Tworzenie partii komunikatów w ramach transakcji
Aplikacje umieszczone w kolejce używają transakcji, aby zapewnić poprawność i niezawodne dostarczanie wiadomości. Transakcje są jednak kosztowne operacje i może znacznie zmniejszyć przepływność wiadomości. Jednym ze sposobów poprawy przepływności wiadomości jest do odczytu i przetwarzania aplikacji wiele komunikatów w ramach jednej transakcji. Kompromis jest między wydajnością a odzyskiwaniem: wraz ze wzrostem liczby komunikatów w partii zwiększa się ilość pracy odzyskiwania, która jest wymagana, jeśli transakcje są przywracane. Należy zwrócić uwagę na różnicę między wsadowym wiadomościami w transakcji i sesjach. *Sesja* to grupowanie powiązanych wiadomości, które są przetwarzane przez jedną aplikację i zatwierdzone jako pojedyncza jednostka. Sesje są zwykle używane, gdy grupa powiązanych wiadomości musi być przetwarzane razem. Przykładem tego jest witryna sieci Web zakupów online. *Partie* są używane do przetwarzania wielu, niepowiązanych wiadomości w sposób, który zwiększa przepływność wiadomości. Aby uzyskać więcej informacji na temat sesji, zobacz [Grupowanie wiadomości w kolejce w sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Wiadomości w partii są również przetwarzane przez jedną aplikację i zatwierdzone jako pojedyncza jednostka, ale może nie być relacji między wiadomościami w partii. Przetwarzanie wsadowe wiadomości w transakcji jest optymalizacja, która nie zmienia sposobu działania aplikacji.  
  
## <a name="entering-batching-mode"></a>Wprowadzanie trybu wsadowego  
 Zachowanie <xref:System.ServiceModel.Description.TransactedBatchingBehavior> punktu końcowego kontroluje przetwarzanie wsadowe. Dodawanie tego zachowania punktu końcowego do punktu końcowego usługi informuje Windows Communication Foundation (WCF) do komunikatów wsadowych w transakcji. Nie wszystkie komunikaty wymagają transakcji, więc tylko wiadomości, które wymagają transakcji są umieszczane w partii i tylko wiadomości wysyłane z operacji oznaczonych `TransactionScopeRequired`  =  `true` i `TransactionAutoComplete`  =  `true` są uważane za partii. Jeśli wszystkie operacje w umowie `TransactionScopeRequired`  =  `false` serwisowej są oznaczone i `TransactionAutoComplete`  =  `false`, a następnie tryb wsadowego nigdy nie jest wprowadzany.  
  
## <a name="committing-a-transaction"></a>Zatwierdzanie transakcji  
 Transakcja wsadowa jest zatwierdzana na podstawie następujących czynności:  
  
- `MaxBatchSize`. Właściwość <xref:System.ServiceModel.Description.TransactedBatchingBehavior> zachowania. Ta właściwość określa maksymalną liczbę komunikatów, które są umieszczane w partii. Po osiągnięciu tej liczby partia jest zatwierdzana. Jest to wartość nie jest ścisły limit, jest możliwe, aby zatwierdzić partii przed odebraniem tej liczby komunikatów.  
  
- `Transaction Timeout`. Po upływie 80 procent limit czasu transakcji, partia jest zatwierdzana i tworzona jest nowa partia. Oznacza to, że jeśli 20 procent lub mniej czasu podanego dla transakcji do wykonania pozostaje, partia jest zatwierdzona.  
  
- `TransactionScopeRequired`. Podczas przetwarzania partii wiadomości, jeśli WCF `TransactionScopeRequired`  =  `false`znajdzie taki, który ma , zatwierdza partii i ponownie `TransactionScopeRequired`  =  `true` otwiera `TransactionAutoComplete`  = nową partię po otrzymaniu pierwszej wiadomości z i `true`.  
  
- Jeśli w kolejce nie ma więcej komunikatów, bieżąca `MaxBatchSize` partia jest zatwierdzana, nawet jeśli nie osiągnięto lub nie upłynęło 80 procent limit czasu transakcji.  
  
## <a name="leaving-batching-mode"></a>Pozostawienie trybu wsadowego  
 Jeśli komunikat w partii powoduje przerwanie transakcji, występują następujące kroki:  
  
1. Cała partia wiadomości jest przywracana.  
  
2. Wiadomości są odczytywane po jednym na raz, dopóki liczba odczytanych wiadomości nie przekroczy dwukrotnie maksymalnego rozmiaru partii.  
  
3. Tryb wsadowy zostanie ponownie wprowadzony.  
  
## <a name="choosing-the-batch-size"></a>Wybieranie rozmiaru partii  
 Rozmiar partii jest zależny od aplikacji. Metoda empiryczna jest najlepszym sposobem, aby osiągnąć optymalny rozmiar partii dla aplikacji. Należy pamiętać przy wyborze rozmiaru partii, aby wybrać rozmiar zgodnie z rzeczywistym modelu wdrażania aplikacji. Na przykład podczas wdrażania aplikacji, jeśli potrzebujesz serwera SQL na komputerze zdalnym i transakcji, która obejmuje kolejkę i serwer SQL, to rozmiar partii najlepiej jest określić na podstawie uruchomienia tej dokładnej konfiguracji.  
  
## <a name="concurrency-and-batching"></a>Współbieżność i wsadowanie  
 Aby zwiększyć przepływność, można również uruchomić wiele partii jednocześnie. Przez `ConcurrencyMode.Multiple` ustawienie `ServiceBehaviorAttribute`w , można włączyć równoczesnych partii.  
  
 *Ograniczanie usług* jest zachowanie usługi, która jest używana do wskazania, ile maksymalna równoczesnych wywołań mogą być wykonane w usłudze. W przypadku użycia z wsadowania, jest interpretowany jako ile równoczesnych partii można uruchomić. Jeśli ograniczanie usługi nie jest ustawiona, WCF domyślnie maksymalne równoczesnych wywołań do 16. W związku z tym jeśli zachowanie przetwarzania wsadowego zostały dodane domyślnie, maksymalnie 16 partii może być aktywny w tym samym czasie. Najlepiej jest dostroić ograniczanie i przetwarzanie wsadowe usługi w zależności od pojemności. Na przykład jeśli kolejka ma 100 komunikatów i partia 20 jest pożądana, o maksymalną równoczesne wywołania ustawione na 16 nie jest przydatne, ponieważ, w zależności od przepływności, 16 transakcji może być aktywny, podobnie jak nie z włączonym wsadowym. W związku z tym podczas dostrajania wydajności, albo nie mają równoczesnych partii lub równoczesnych partii z poprawnym rozmiarem przepustnicy usługi.  
  
## <a name="batching-and-multiple-endpoints"></a>Przetwarzanie wsadowe i wiele punktów końcowych  
 Punkt końcowy składa się z adresu i umowy. Może istnieć wiele punktów końcowych, które współużytkuje to samo powiązanie. Jest możliwe dla dwóch punktów końcowych do udostępniania tego samego powiązania i nasłuchiwać jednolity identyfikator zasobów (URI) lub adres kolejki. Jeśli dwa punkty końcowe są odczytywane z tej samej kolejki i transacted wsadowe zachowanie jest dodawany do obu punktów końcowych, konflikt w rozmiarach partii określonych może wystąpić. Jest to rozwiązywane przez implementowanie przetwarzania wsadowego przy użyciu minimalnego rozmiaru partii określonego między dwoma zachowaniami przetwarzania wsadowego. W tym scenariuszu jeśli jeden z punktów końcowych nie określa transacted przetwarzania wsadowego, a następnie oba punkty końcowe nie będzie używać przetwarzania wsadowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `TransactedBatchingBehavior` pokazano, jak określić w pliku konfiguracji.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 W poniższym przykładzie <xref:System.ServiceModel.Description.TransactedBatchingBehavior> pokazano, jak określić w kodzie.  
  
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

- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
