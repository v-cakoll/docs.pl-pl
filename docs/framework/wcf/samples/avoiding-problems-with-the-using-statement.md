---
title: "Unikanie problemów z instrukcją Using"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 123081683f122f68fded94aed5735d7058496366
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="avoiding-problems-with-the-using-statement"></a>Unikanie problemów z instrukcją Using
W przykładzie pokazano, jak nie należy używać "using" — instrukcja automatycznie wyczyścić zasobów, korzystając z klienta typu C#. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator. W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład przedstawia dwa typowych problemów występujących podczas przy użyciu "Używanie" instrukcji z klientów typu, a także kod, który prawidłowo czyści po wyjątków języka C#.  
  
 C# instrukcję "using" powoduje wywołanie `Dispose`(). To jest taka sama jak `Close`(), który może zgłaszać wyjątki po wystąpieniu błędu sieci. Ponieważ wywołanie `Dispose`() odbywa się niejawnie na zamykający nawias klamrowy bloku "using", to źródło wyjątki prawdopodobne jest, aby przejść bez zwracania uwagi zarówno przez osoby pisanie kodu i odczytywania kod. Stanowi to potencjalne źródło błędów aplikacji.  
  
 Pierwszy problem, przedstawiono w `DemonstrateProblemUsingCanThrow` metoda, to czy zamykający nawias klamrowy zgłasza wyjątek i kod po nawias zamykający nie wykonuj:  
  
```  
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 Nawet jeśli żadne wewnątrz przy użyciu bloków zwraca wyjątek lub wszystkie wyjątki wewnątrz przy użyciu bloku są przechwytywane, `Console.Writeline` nie może być to, że niejawne `Dispose`wywołanie () w nawias zamykający może zgłosić wyjątek.  
  
 Drugi problem, przedstawiono w `DemonstrateProblemUsingCanThrowAndMask` metoda, jest inny wpływ na zamykający nawias klamrowy zgłoszeniu wyjątku:  
  
```  
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 Ponieważ `Dispose`(), wystąpi wewnątrz bloku "finally" `ApplicationException` nigdy nie jest widoczna poza przy użyciu zablokować, jeśli `Dispose`() nie powiedzie się. Jeśli kod poza musi wiedzieć o tym, kiedy `ApplicationException` występuje konstrukcji "przy użyciu" może spowodować problemy przez maskowania tego wyjątku.  
  
 Na koniec przykładzie pokazano, jak czyszczenie poprawnie, gdy wyjątki występują w `DemonstrateCleanupWithExceptions`. Używa bloku try/catch w celu przesłania raportów o błędach i wywołania `Abort`. Zobacz [oczekiwane wyjątki](../../../../docs/framework/wcf/samples/expected-exceptions.md) przykładowa, aby uzyskać więcej informacji o przechwytywanie wyjątków z wywołań klienta.  
  
```  
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  Przy użyciu instrukcji i ServiceHost: wiele aplikacji własnym hostingu nieco więcej niż obsługuje usługi i ServiceHost.Close rzadko zgłasza wyjątek, tak aby takich aplikacji bezpiecznie korzystać przy użyciu instrukcji z elementu ServiceHost. Należy jednak pamiętać, że może zgłosić ServiceHost.Close `CommunicationException`, więc jeśli aplikacja będzie nadal występować po zamknięciu usługi ServiceHost, należy unikać używania instrukcji i wykonaj wzorzec wcześniej podane.  
  
 Po uruchomieniu próbki odpowiedzi operacji i wyjątków są wyświetlane w oknie konsoli klienta.  
  
 Proces klienta uruchamia trzy scenariusze, każdy podejmuje próbę nawiązania `Divide`. Pierwszy scenariusz pokazuje pominięte z powodu wyjątku z kodu `Dispose`(). Drugi scenariusz przedstawiono ważne wyjątek maskowanego z powodu wyjątku z `Dispose`(). Trzeci scenariusz przedstawiono poprawne oczyszczania.  
  
 Oczekiwane dane wyjściowe z procesu klienta jest:  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a>Zobacz też
