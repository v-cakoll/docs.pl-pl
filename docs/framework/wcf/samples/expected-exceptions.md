---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: a874b291202cb8c3c8752c13b357679c7fd5a556
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989974"
---
# <a name="expected-exceptions"></a>Oczekiwane wyjątki
Ten przykład pokazuje, jak przechwytywać oczekiwane wyjątki przy użyciu klienta z określonym typem. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora. W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie pokazano, jak przechwytywać i obsługiwać dwa oczekiwane typy wyjątków, które muszą `TimeoutException` być `CommunicationException`obsługiwane przez poprawne programy: i.  
  
 Wyjątki generowane przez metody komunikacji na kliencie Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwane. Nieoczekiwane wyjątki obejmują katastrofalne błędy, takie `OutOfMemoryException` jak `InvalidOperationException`i błędy programowania, takie jak `ArgumentNullException` lub. Zazwyczaj nie istnieje użyteczny sposób obsługi nieoczekiwanych błędów, więc zazwyczaj nie należy ich przechwytywać podczas wywoływania metody komunikacji z klientem WCF.  
  
 Oczekiwane wyjątki z metod komunikacji na kliencie WCF obejmują `TimeoutException`, `CommunicationException` `CommunicationException`i dowolną klasę pochodną. Wskazuje to na problem podczas komunikacji, która może być bezpiecznie obsługiwana przez przerwanie działania klienta programu WCF i Raportowanie błędu komunikacji. Ze względu na to, że zewnętrzne czynniki mogą spowodować te błędy w dowolnej aplikacji, poprawne aplikacje muszą przechwycić te wyjątki i odzyskać je po wystąpieniu.  
  
 Istnieje kilka klas `CommunicationException` pochodnych, które klient może zgłosić. W niektórych przypadkach aplikacje przechwytuje niektóre z nich w celu przeprowadzenia specjalnej obsługi, ale pozwól, aby inne osoby `CommunicationException`były obsługiwane jako. Można to osiągnąć przez przechwycenie najpierw określonego typu wyjątku, a następnie przechwycenie `CommunicationException` w późniejszej klauzuli catch.  
  
 Kod, który wywołuje metodę komunikacji klienta, musi `TimeoutException` przechwycić `CommunicationException`i. Jednym ze sposobów obsługi takich błędów jest przerwanie działania klienta i zgłaszanie błędu komunikacji.  
  
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
  
 Jeśli wystąpi oczekiwany wyjątek, klient może lub nie może być później używany. Aby określić, czy klient jest nadal zdatny do użytku, `State` Sprawdź, `CommunicationState`czy właściwość jest. Otworzyć. Jeśli nadal jest otwarty, nadal będzie można go użyć. W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.  
  
> [!CAUTION]
> Można zauważyć, że klienci, którzy mają sesję, często nie mogą już korzystać z programu po wystąpieniu wyjątku, a klienci, którzy nie mają sesji, często nadal mogą korzystać po wystąpieniu wyjątku. Jednak żadna z nich nie jest gwarantowana, więc jeśli chcesz spróbować kontynuować korzystanie z klienta po wystąpieniu wyjątku, aplikacja powinna sprawdzić `State` właściwość, aby sprawdzić, czy klient jest nadal otwarty.  
  
 Po uruchomieniu przykładu odpowiedzi operacji i wyjątki są wyświetlane w oknie konsoli klienta.  
  
 Proces klienta uruchamia dwa scenariusze, z których każdy próbuje wywołać wywołanie `Add`. `Divide` Pierwszy scenariusz symuluje problem z siecią, przerywając działanie klienta przed wywołaniem do `Divide`programu. Drugi scenariusz powoduje przekroczenie limitu czasu przez ustawienie przekroczenia limitu czasu, aby można było ukończyć metodę. Oczekiwane dane wyjściowe procesu klienta to:  
  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
