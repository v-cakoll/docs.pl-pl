---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 9552bf5178e3309d46e0f9220311c9e1a811c4b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expected-exceptions"></a>Oczekiwane wyjątki
W tym przykładzie pokazano, jak catch oczekiwane wyjątki, używając typu klienta. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator. W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie pokazano przechwytywanie i dwa typy oczekiwanego wyjątku, które Popraw programy obsługi musi obsługiwać: `TimeoutException` i `CommunicationException`.  
  
 Wyjątki, które są generowane z metody komunikacji na kliencie systemu Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwany. Nieoczekiwany wyjątków należą poważnej awarii, takich jak `OutOfMemoryException` i programowania błędów, takich jak `ArgumentNullException` lub `InvalidOperationException`. Zwykle nie istnieje sposób przydatne do obsługi błędów nieoczekiwany, dlatego zazwyczaj nie należy przechwytywać ich podczas wywoływania metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metodę komunikacji z klientem.  
  
 Oczekiwano wyjątki od metody komunikacji na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta obejmują `TimeoutException`, `CommunicationException`, oraz wszelkie otrzymane z klasy `CommunicationException`. Te wskazują na problem podczas komunikacji, który może być bezpiecznie obsługiwanych przez przerywanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta oraz raportowania błędów komunikacji. Ponieważ czynniki zewnętrzne mogą powodować błędy w dowolnej aplikacji, poprawne aplikacji należy przechwytywać tych wyjątków i odzyskać wystąpieniach.  
  
 Istnieje kilka klas pochodnych `CommunicationException` który klient może zgłosić. W niektórych przypadkach aplikacji również catch niektóre z nich, aby nie specjalnej obsługi, ale inni traktowane jako `CommunicationException`. Można to zrobić przez najpierw Przechwytywanie więcej określony typ wyjątku, a następnie Przechwytywanie `CommunicationException` w późniejszym klauzuli catch.  
  
 Kod, który wywołuje metodę komunikacji z klientem muszą catch `TimeoutException` i `CommunicationException`. Jednym ze sposobów obsługi tych błędów ma przerwać klienta i zgłoś błąd komunikacji.  
  
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
  
 Sytuacji oczekiwanego wyjątku klient może lub nie można używać później. Aby ustalić, czy klient jest nadal można używać, sprawdź, czy `State` jest właściwość `CommunicationState`. Otwarty. Jeśli jest wciąż otwarty, następnie jest nadal możliwe. W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.  
  
> [!CAUTION]
>  Można zauważyć, że klienci, którzy mają sesję często nie są już można używać po wystąpieniu wyjątku i klientów, którzy nie mają sesji są wciąż często można używać po wystąpieniu wyjątku. Jednak żadnej z tych jest gwarantowana, dlatego jeśli chcesz spróbować kontynuowanie po wystąpieniu wyjątku, zapoznaj się z aplikacji przy użyciu klienta `State` właściwości, aby sprawdzić, klient jest nadal otwarty.  
  
 Po uruchomieniu próbki odpowiedzi operacji i wyjątków są wyświetlane w oknie konsoli klienta.  
  
 Proces klienta uruchamia dwa scenariusze każdego podejmuje próbę nawiązania `Add` następuje `Divide`. Pierwszy scenariusz symuluje problem z siecią przez przerywanie klienta przed wprowadzeniem wywołanie `Divide`. Drugi scenariusz powoduje, że warunek limitu czasu przez ustawienie limitu czasu zbyt krótka dla metody, aby zakończyć. Oczekiwane dane wyjściowe z procesu klienta jest:  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a>Zobacz też
