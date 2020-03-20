---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: f250e526b528adf0b67365ceb07f13e4087d773d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144712"
---
# <a name="expected-exceptions"></a>Oczekiwane wyjątki
W tym przykładzie pokazano, jak przechwytywać oczekiwane wyjątki podczas korzystania z wpisanego klienta. Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora. W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie pokazano, że wyłapywanie i `TimeoutException` `CommunicationException`obsługa dwóch oczekiwanych typów wyjątków, które muszą obsługiwać poprawne programy: i .  
  
 Wyjątki, które są generowane z metod komunikacji na kliencie Programu Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwane. Nieoczekiwane wyjątki obejmują `OutOfMemoryException` katastrofalne błędy, `ArgumentNullException` `InvalidOperationException`takie jak i błędy programowania, takie jak lub . Zazwyczaj nie ma użytecznego sposobu obsługi nieoczekiwanych błędów, więc zazwyczaj nie należy ich przechwytywać podczas wywoływania metody komunikacji klienta WCF.  
  
 Oczekiwane wyjątki od metod komunikacji na `TimeoutException` `CommunicationException`kliencie WCF `CommunicationException`obejmują , i dowolną klasę pochodną . Wskazują one na problem podczas komunikacji, które mogą być bezpiecznie obsługiwane przez przerwanie klienta WCF i raportowania awarii komunikacji. Ponieważ czynniki zewnętrzne mogą powodować te błędy w dowolnej aplikacji, poprawne aplikacje muszą przechwytywać te wyjątki i odzyskać, gdy wystąpią.  
  
 Istnieje kilka klas pochodnych, `CommunicationException` które klient może wrzucić. W niektórych przypadkach aplikacje również złapać niektóre z nich do specjalnej `CommunicationException`obsługi, ale niech inne być traktowane jako . Można to osiągnąć, przechwytywając najpierw bardziej `CommunicationException` szczegółowy typ wyjątku, a następnie przechwytywając w późniejszej klauzuli catch.This can be accomplished by catching the more specific exception type first and then catching in a later catch-clause.  
  
 Kod, który wywołuje metodę komunikacji `TimeoutException` `CommunicationException`klienta musi przechwytyć i . Jednym ze sposobów obsługi takich błędów jest przerwanie klienta i zgłoszenie awarii komunikacji.  
  
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
  
 Jeśli wystąpi oczekiwany wyjątek, klient może lub nie może być użyteczny później. Aby ustalić, czy klient jest nadal `State` użyteczny, sprawdź, czy właściwość jest `CommunicationState`. Otwarte. Jeśli jest nadal otwarty, to nadal nadaje się do użyteczności. W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.  
  
> [!CAUTION]
> Można zaobserwować, że klienci, którzy mają sesję często nie są już użyteczne po wyjątku i klientów, którzy nie mają sesji są często nadal użyteczne po wyjątku. Jednak żadna z nich nie jest gwarantowana, więc jeśli chcesz spróbować kontynuować `State` korzystanie z klienta po wyjątku aplikacja powinna sprawdzić właściwość, aby sprawdzić, czy klient jest nadal otwarty.  
  
 Po uruchomieniu przykładu odpowiedzi operacji i wyjątki są wyświetlane w oknie konsoli klienta.  
  
 Proces klienta uruchamia dwa scenariusze, z `Add` których `Divide`każdy próbuje wywołać, a następnie . Pierwszy scenariusz symuluje problem z siecią, przerywając `Divide`klienta przed wykonaniem połączenia z programem . Drugi scenariusz powoduje warunek limitu czasu, ustawiając limit czasu zbyt krótki dla metody, aby zakończyć. Oczekiwane dane wyjściowe z procesu klienta są następujące:  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
