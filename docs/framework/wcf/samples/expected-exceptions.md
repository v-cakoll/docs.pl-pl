---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: ea48a9c7393e809b4267f4e089998fa0e73b49fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163625"
---
# <a name="expected-exceptions"></a>Oczekiwane wyjątki
W tym przykładzie pokazano, jak przechwytywać wyjątki oczekiwane, korzystając z klient z typowaniem. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora. W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Niniejszy przykład pokazuje, przechwytywanie i dwa typy oczekiwanego wyjątku, które poprawić programy obsługi musi obsługiwać: `TimeoutException` i `CommunicationException`.  
  
 Wyjątki, które są generowane przez metody komunikacji w kliencie programu Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwany. Nieoczekiwane wyjątki obejmują katastrofalnych awarii, takich jak `OutOfMemoryException` i błędy programowania, takich jak `ArgumentNullException` lub `InvalidOperationException`. Zazwyczaj jest przydatny sposób obsługi nieoczekiwanych błędów, więc zazwyczaj nie należy przechwytywać je podczas wywoływania metody komunikacji klienta programu WCF.  
  
 Oczekiwane wyjątki od metod komunikacji klienta programu WCF obejmują `TimeoutException`, `CommunicationException`, oraz wszelkie otrzymane klasy `CommunicationException`. Oznaczają one problem podczas komunikacji, który może być bezpiecznie obsługiwane przez przerywanie klienta WCF i zgłaszanie błędu komunikacji. Ponieważ czynniki zewnętrzne mogą spowodować błędy w dowolnej aplikacji, poprawny aplikacji należy przechwytywać te wyjątki i odzyskiwanie po ich wystąpieniu.  
  
 Istnieje kilka klas pochodnych `CommunicationException` który klient może zgłosić. W niektórych przypadkach aplikacje również catch niektóre z nich są specjalnej obsługi, ale inni obsługiwany jako `CommunicationException`. Można to zrobić, najpierw Przechwytywanie bardziej specyficznego typu wyjątku i następnie Przechwytywanie `CommunicationException` w późniejszym klauzuli catch.  
  
 Kod, który wywołuje metodę komunikacji klienta należy wyłapać `TimeoutException` i `CommunicationException`. Jest jednym ze sposobów, aby obsłużyć takie błędy przerwać klienta i zgłoś błąd komunikacji.  
  
```csharp   
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 Jeśli wystąpi oczekiwanego wyjątku, klient może lub może nie dawać później. Aby ustalić, czy klient jest nadal można używać, sprawdź, czy `State` właściwość `CommunicationState`. Otwarty. Jeśli jest wciąż otwarty, jest nadal można używać. W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.  
  
> [!CAUTION]
>  Można zaobserwować, że klienci, którzy mają sesję często nie są już można używać po wystąpieniu wyjątku, i klienci, którzy nie mają sesji są często nadal można używać po wystąpieniu wyjątku. Jednak żadnej z tych metod jest gwarantowane, więc jeśli chcesz podjąć próbę kontynuowania działania przy użyciu klienta po wystąpieniu wyjątku, Twoja aplikacja ma sprawdzać `State` właściwości, aby sprawdzić, klient jest wciąż otwarty.  
  
 Po uruchomieniu przykładu odpowiedzi operacji i wyjątków są wyświetlane w oknie konsoli klienta.  
  
 Proces klienta jest uruchamiane dwa scenariusze, każda z których próby wywołania `Add` następuje `Divide`. Pierwszy scenariusz symuluje problem z siecią przerywanie klienta przed wprowadzeniem wywołanie `Divide`. Drugi scenariusz powoduje, że warunek limitu czasu przez ustawienie limitu czasu zbyt mała w przypadku metody, aby zakończyć. Oczekiwane dane wyjściowe z procesu klienta jest:  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
