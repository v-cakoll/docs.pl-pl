---
title: Użyj Zamknij i Przerwij, aby zwolnić zasoby klienta WCF
description: Dispose może zakończyć się niepowodzeniem i zgłaszają wyjątki, gdy sieć nie powiedzie się. Który może spowodować niepożądane zachowanie. Zamiast tego użyj Zamknij i Przerwij, aby zwolnić zasoby klienta, gdy sieć nie powiodło się.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 58f828d9cd85806f5f04c349a7de18828ab5f6f2
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678972"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a>Zamknij i przerwania zwolnienia zasobów bezpiecznie w przypadku, gdy połączenia sieciowe zostały odrzucone

Ten przykład demonstruje użycie `Close` i `Abort` metody, aby wyczyścić zasoby, korzystając z klient z typowaniem. `using` Instrukcja powoduje wyjątki, gdy połączenie sieciowe działa niezawodnie. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora. W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).

> [!NOTE]
> Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.

W tym przykładzie przedstawiono dwie typowe problemy, które występuje w przypadku użycia "za pomocą" instrukcji z kontrolą typów klientów, a także kod, który prawidłowo czyści po wyjątków języka C#.

C# instrukcję "using" powoduje wywołanie `Dispose`(). To jest taka sama jak `Close`(), który może zgłaszać wyjątki, gdy wystąpi błąd sieci. Ponieważ wywołanie `Dispose`() odbywa się domyślnie na zamykający nawias klamrowy w bloku "za pomocą", to źródło wyjątków jest prawdopodobnie przejście bez zwracania uwagi zarówno przez osoby, pisanie kodu i kodu. Reprezentuje potencjalnym źródłem błędów aplikacji.

Pierwszy problem, przedstawionych `DemonstrateProblemUsingCanThrow` metody jest, że zamykającego nawiasu klamrowego zgłasza wyjątek i kod po nawias zamykający nie jest wykonywane:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

Nawet wtedy, gdy nic wewnątrz przy użyciu block, zgłasza wyjątek, który lub wszystkie wyjątki wewnątrz przy użyciu bloku zostały wykryte, `Console.WriteLine` nie może być to, że niejawny `Dispose`wywołania () w zamykającego nawiasu klamrowego może zgłosić wyjątek.

Drugi problem, przedstawionych `DemonstrateProblemUsingCanThrowAndMask` metody jest domniemanie innego elementu zamykającego nawiasu klamrowego, zostanie zgłoszony wyjątek:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

Ponieważ `Dispose`() odbywa się wewnątrz bloku "finally" `ApplicationException` nigdy nie są widoczne poza używając zablokować, jeśli `Dispose`() nie powiodło się. Jeśli kod poza musisz wiedzieć o tym, kiedy `ApplicationException` występuje w konstrukcji "using" może spowodować problemy, maskując tego wyjątku.

Ponadto w przykładzie pokazano jak wyczyścić poprawnie, gdy wyjątki występują w `DemonstrateCleanupWithExceptions`. Ta metoda korzysta z bloku try/catch, aby raportowanie błędów, a następnie wywołać `Abort`. Zobacz [oczekiwane wyjątki](../../../../docs/framework/wcf/samples/expected-exceptions.md) przykładowe więcej szczegółowych informacji dotyczących przechwytywania wyjątków z wywołań klienta.

```csharp
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
> Za pomocą instrukcji i ServiceHost: Wiele aplikacji samodzielnie hostingu nieco ponad hostowanie usługi i ServiceHost.Close rzadko zgłasza wyjątek, więc takie aplikacje mogą bezpiecznie korzystać przy użyciu instrukcji za pomocą elementu ServiceHost. Należy jednak pamiętać, że może zgłosić ServiceHost.Close `CommunicationException`, więc jeśli aplikacja będzie nadal występował po zamknięciu elementu ServiceHost, należy unikać używania instrukcji i postępuj zgodnie z wzorcem podane wcześniej.

Po uruchomieniu przykładu odpowiedzi operacji i wyjątków są wyświetlane w oknie konsoli klienta.

Proces klienta uruchamia trzy scenariusze, każda z których próby wywołania `Divide`. Pierwszy scenariusz pokazuje kod pominięte z powodu wyjątku z `Dispose`(). Drugi scenariusz pokazuje ważny wyjątek maskowaniu z powodu wyjątku z `Dispose`(). Trzeci scenariusz pokazuje poprawne oczyszczania.

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

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!IMPORTANT]
> Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
