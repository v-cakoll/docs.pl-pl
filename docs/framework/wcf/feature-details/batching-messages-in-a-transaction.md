---
title: Tworzenie partii komunikatów w ramach transakcji
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: 3b35d1de76587ce750bf73189eb37658c3d87a90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593623"
---
# <a name="batching-messages-in-a-transaction"></a>Tworzenie partii komunikatów w ramach transakcji
Aplikacje w kolejce używają transakcji w celu zapewnienia poprawnego i niezawodnego dostarczania komunikatów. Transakcje są jednak kosztowne i znacznie zmniejszają przepływność komunikatów. Jednym ze sposobów na zwiększenie przepływności komunikatów jest odczytanie i przetworzenie wielu komunikatów w ramach jednej transakcji. Różnica między wydajnością i odzyskiwaniem polega na tym, że liczba komunikatów w partii rośnie, więc ilość pracy odzyskiwania wymagana w przypadku wycofania transakcji. Ważne jest, aby zauważyć różnicę między wsadowymi komunikatami w transakcji i sesjach. *Sesja* jest grupą powiązanych komunikatów, które są przetwarzane przez pojedynczą aplikację i zatwierdzona jako pojedyncza jednostka. Sesje są zwykle używane, gdy grupa powiązanych komunikatów musi być przetwarzana razem. Przykładem jest witryna internetowa do kupowania w trybie online. *Partie* są używane do przetwarzania wielu niepowiązanych komunikatów w taki sposób, aby zwiększyć przepływność komunikatów. Aby uzyskać więcej informacji na temat sesji, zobacz [grupowanie komunikatów umieszczonych w kolejce w sesji](grouping-queued-messages-in-a-session.md). Komunikaty w partii są również przetwarzane przez pojedynczą aplikację i zatwierdzono jako pojedynczą jednostkę, ale nie może istnieć relacja między komunikatami w partii. Przetwarzanie wsadowe komunikatów w transakcji to Optymalizacja, która nie zmienia sposobu działania aplikacji.  
  
## <a name="entering-batching-mode"></a>Wchodzenie do trybu wsadowego  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>Zachowanie punktu końcowego steruje przetwarzaniem wsadowym. Dodanie tego zachowania punktu końcowego do punktu końcowego usługi informuje Windows Communication Foundation (WCF) o wiadomościach wsadowych w transakcji. Nie wszystkie komunikaty wymagają transakcji, dlatego tylko komunikaty, które wymagają transakcji, są umieszczane w partii, a tylko komunikaty wysyłane z operacji oznaczonych za pomocą `TransactionScopeRequired`  =  `true` i `TransactionAutoComplete`  =  `true` są brane pod uwagę dla partii. Jeśli wszystkie operacje na kontrakcie usługi są oznaczone za pomocą `TransactionScopeRequired`  =  `false` i `TransactionAutoComplete`  =  `false` , tryb tworzenia wsadowego nie zostanie nigdy wprowadzony.  
  
## <a name="committing-a-transaction"></a>Zatwierdzanie transakcji  
 Transakcja wsadowa jest zatwierdzana na podstawie następujących danych:  
  
- `MaxBatchSize`. Właściwość <xref:System.ServiceModel.Description.TransactedBatchingBehavior> zachowania. Ta właściwość określa maksymalną liczbę komunikatów, które są umieszczane w partii. Gdy ten numer zostanie osiągnięty, zadanie wsadowe zostanie zatwierdzone. Ta wartość nie jest ścisłym limitem, dlatego można zatwierdzić partię przed odebraniem tej liczby komunikatów.  
  
- `Transaction Timeout`. Po upływie 80 procent limitu czasu transakcji zadanie wsadowe zostanie zatwierdzone i zostanie utworzona nowa Partia zadań. Oznacza to, że w przypadku pozostawania przez 20% lub mniej czasu pozostałego do ukończenia transakcji zadanie wsadowe zostanie zatwierdzone.  
  
- `TransactionScopeRequired`. Podczas przetwarzania partii komunikatów, jeśli usługa WCF znajdzie taką, która z nich jest `TransactionScopeRequired`  =  `false` , zatwierdzi zadanie wsadowe i ponownie otworzy nową partię przy odbiorze pierwszej wiadomości z `TransactionScopeRequired`  =  `true` i `TransactionAutoComplete`  =  `true` .  
  
- Jeśli w kolejce nie ma więcej komunikatów, bieżąca partia jest zatwierdzana, nawet jeśli `MaxBatchSize` nie został osiągnięty lub 80% czasu transakcji nie upłynął.  
  
## <a name="leaving-batching-mode"></a>Opuszczanie trybu wsadowego  
 Jeśli komunikat w partii powoduje przerwanie transakcji, wystąpią następujące czynności:  
  
1. Cała partia komunikatów jest wycofywana.  
  
2. Komunikaty są odczytywane pojedynczo, dopóki Liczba odczytanych komunikatów przekroczy dwukrotnie maksymalny rozmiar wsadu.  
  
3. Trwa ponowne wprowadzanie trybu wsadowego.  
  
## <a name="choosing-the-batch-size"></a>Wybieranie rozmiaru partii  
 Rozmiar partii zależy od aplikacji. Metoda doświadczalna jest najlepszym sposobem osiągnięcia optymalnego rozmiaru partii dla aplikacji. Należy pamiętać, że w przypadku wybrania rozmiaru partii w celu wybrania rozmiaru zgodnie z rzeczywistym modelem wdrażania aplikacji. Na przykład podczas wdrażania aplikacji, jeśli potrzebujesz programu SQL Server na komputerze zdalnym i transakcji obejmującej kolejkę i program SQL Server, rozmiar wsadu najlepiej określa się, uruchamiając dokładną konfigurację.  
  
## <a name="concurrency-and-batching"></a>Współbieżność i przetwarzanie wsadowe  
 Aby zwiększyć przepływność, można również korzystać z wielu partii jednocześnie. Ustawienie `ConcurrencyMode.Multiple` w programie `ServiceBehaviorAttribute` włącza współbieżne przetwarzanie wsadowe.  
  
 *Ograniczanie usługi* jest zachowaniem usługi, które służy do wskazywania, ile maksymalnej liczby współbieżnych wywołań można wykonać w usłudze. W przypadku użycia z przetwarzaniem wsadowym ta interpretacja jest interpretowana jako liczba współbieżnych partii, które mogą być uruchamiane. Jeśli ograniczanie usługi nie jest skonfigurowane, program WCF domyślnie ustawia maksymalną liczbę współbieżnych wywołań na 16. W takim przypadku, jeśli działanie wsadowe zostało dodane domyślnie, maksymalnie 16 partii może być aktywnych w tym samym czasie. Najlepszym rozwiązaniem jest dostrojenie ograniczenia przepustowości i przetwarzania wsadowego na podstawie wydajności. Na przykład, jeśli kolejka ma 100 komunikatów, a partia z 20 jest wymagana, a maksymalna liczba współbieżnych wywołań ustawiona na 16 nie jest przydatna, ponieważ, w zależności od przepływności, 16 transakcji może być aktywnych, podobnie jak nie ma włączonej usługi Batch. W związku z tym, gdy dostrajanie do wydajności nie jest wykonywane współbieżne przetwarzanie wsadowe lub współbieżne przetwarzanie wsadowe z prawidłowym rozmiarem przepustnicy usług.  
  
## <a name="batching-and-multiple-endpoints"></a>Tworzenie partii i wielu punktów końcowych  
 Punkt końcowy składa się z adresu i kontraktu. Może istnieć wiele punktów końcowych korzystających z tego samego powiązania. Możliwe jest, aby dwa punkty końcowe współdzielą te same powiązania i nasłuchiwanie Uniform Resource Identifier (URI) lub adres kolejki. Jeśli dwa punkty końcowe są odczytywane z tej samej kolejki, a w obu punktach końcowych jest dodawane transakcyjne zachowanie wsadowe, może wystąpić konflikt w określonych rozmiarach partii. Jest to rozwiązywane przez zaimplementowanie przetwarzania wsadowego przy użyciu minimalnego rozmiaru partii określonego między dwoma zachowań wsadowych transakcji. W tym scenariuszu, jeśli jeden z punktów końcowych nie określa transakcyjnego przetwarzania wsadowego, wówczas oba punkty końcowe nie będą używać operacji wsadowych.  
  
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
  
 Poniższy przykład pokazuje, jak określić <xref:System.ServiceModel.Description.TransactedBatchingBehavior> kod w kodzie.  
  
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

- [Omówienie kolejek](queues-overview.md)
- [Tworzenie kolejek w programie WCF](queuing-in-wcf.md)
