---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 24bb9b483a3f26241f895d68b763a1974b02151b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716451"
---
# <a name="expected-exceptions"></a>Oczekiwane wyjątki
Ten przykład pokazuje, jak przechwytywać oczekiwane wyjątki przy użyciu klienta z określonym typem. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora. W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie pokazano, jak przechwytywać i obsługiwać dwa oczekiwane typy wyjątków, które muszą być obsługiwane przez poprawne programy: `TimeoutException` i `CommunicationException`.  
  
 Wyjątki generowane przez metody komunikacji na kliencie Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwane. Nieoczekiwane wyjątki obejmują błędy katastrofalne, takie jak `OutOfMemoryException` i programowanie błędów, takich jak `ArgumentNullException` lub `InvalidOperationException`. Zazwyczaj nie istnieje użyteczny sposób obsługi nieoczekiwanych błędów, więc zazwyczaj nie należy ich przechwytywać podczas wywoływania metody komunikacji z klientem WCF.  
  
 Oczekiwane wyjątki od metod komunikacji na kliencie programu WCF obejmują `TimeoutException`, `CommunicationException`i dowolną klasę pochodną `CommunicationException`. Wskazuje to na problem podczas komunikacji, która może być bezpiecznie obsługiwana przez przerwanie działania klienta programu WCF i Raportowanie błędu komunikacji. Ze względu na to, że zewnętrzne czynniki mogą spowodować te błędy w dowolnej aplikacji, poprawne aplikacje muszą przechwycić te wyjątki i odzyskać je po wystąpieniu.  
  
 Istnieje kilka klas pochodnych `CommunicationException`, które klient może zgłosić. W niektórych przypadkach aplikacje przechwytuje niektóre z nich w celu przeprowadzenia specjalnej obsługi, ale pozwól, aby inne były obsługiwane jako `CommunicationException`. Można to osiągnąć przez przechwycenie najpierw określonego typu wyjątku, a następnie przechwycenie `CommunicationException` w późniejszej klauzuli catch.  
  
 Kod, który wywołuje metodę komunikacji klienta, musi przechwycić `TimeoutException` i `CommunicationException`. Jednym ze sposobów obsługi takich błędów jest przerwanie działania klienta i zgłaszanie błędu komunikacji.  
  
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
  
 Jeśli wystąpi oczekiwany wyjątek, klient może lub nie może być później używany. Aby określić, czy klient jest nadal zdatny do użytku, sprawdź, czy właściwość `State` jest `CommunicationState`. Otworzyć. Jeśli nadal jest otwarty, nadal będzie można go użyć. W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.  
  
> [!CAUTION]
> Można zauważyć, że klienci, którzy mają sesję, często nie mogą już korzystać z programu po wystąpieniu wyjątku, a klienci, którzy nie mają sesji, często nadal mogą korzystać po wystąpieniu wyjątku. Jednak żadna z nich nie jest gwarantowana, więc jeśli chcesz spróbować kontynuować korzystanie z klienta po wystąpieniu wyjątku, aplikacja powinna sprawdzić Właściwość `State`, aby sprawdzić, czy klient jest nadal otwarty.  
  
 Po uruchomieniu przykładu odpowiedzi operacji i wyjątki są wyświetlane w oknie konsoli klienta.  
  
 Proces klienta uruchamia dwa scenariusze, z których każdy próbuje wywołać `Add` a następnie `Divide`. Pierwszy scenariusz symuluje problem z siecią, przerywając działanie klienta przed wywołaniem `Divide`. Drugi scenariusz powoduje przekroczenie limitu czasu przez ustawienie przekroczenia limitu czasu, aby można było ukończyć metodę. Oczekiwane dane wyjściowe procesu klienta to:  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
