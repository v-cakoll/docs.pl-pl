---
title: Zwalnianie zasobów klienta programu WCF za pomocą poleceń Zamknij i Przerwij
description: Metody Dispose mogą kończyć się niepowodzeniem i generować wyjątki w przypadku niepowodzenia sieci. Może to spowodować niepożądane zachowanie. Zamiast tego należy użyć Zamknij i Przerwij, aby zwolnić zasoby klienta w przypadku niepowodzenia sieci.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: b338b760f461d7b773f43dd1f5e6dbce98f9e15a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599922"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a>Bezpieczne zamykanie i przerywanie zasobów wydań po porzucenia połączeń sieciowych

Ten przykład ilustruje użycie `Close` metod i `Abort` do czyszczenia zasobów przy użyciu klienta z określonym typem. `using`Instrukcja powoduje wyjątki, gdy połączenie sieciowe nie jest niezawodne. Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md) , który implementuje usługę kalkulatora. W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

W tym przykładzie przedstawiono dwa typowe problemy występujące podczas korzystania z instrukcji języka C# "Using" z typami klientów, jak również kod, który poprawnie czyści po wyjątkach.

Instrukcja języka C# "Using" powoduje wywołanie `Dispose` (). Jest to taka sama jak `Close` (), która może generować wyjątki w przypadku wystąpienia błędu sieci. Ponieważ wywołanie `Dispose` () występuje niejawnie w zamykającym nawiasie klamrowym bloku "Using", to źródło wyjątków może być niezauważalne, przez co ludzie piszą kod i odczytując kod. Reprezentuje to potencjalne źródło błędów aplikacji.

Pierwszym problemem, przedstawionym w `DemonstrateProblemUsingCanThrow` metodzie, jest to, że zamykający nawias klamrowy zgłasza wyjątek, a kod po zamykającym nawiasie klamrowym nie jest wykonywany:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

Nawet jeśli żadne elementy wewnątrz bloku using nie zgłasza wyjątku lub wszystkie wyjątki wewnątrz bloku using są przechwytywane, może to nie być spowodowane tym, że `Console.WriteLine` wywołanie niejawne `Dispose` () w zamykającym nawiasie klamrowym może zgłosić wyjątek.

Drugi problem, przedstawiony w `DemonstrateProblemUsingCanThrowAndMask` metodzie, jest kolejną implikacją zamykającego nawiasu klamrowego, który zgłasza wyjątek:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

Ponieważ `Dispose` () występuje wewnątrz bloku "finally", `ApplicationException` nigdy nie jest wyświetlany poza blokiem using, jeśli `Dispose` () zakończy się niepowodzeniem. Jeśli kod poza programem musi wiedzieć o `ApplicationException` wystąpieniu problemu, konstrukcja "Using" może spowodować problemy, maskując ten wyjątek.

Na koniec przykład pokazuje, jak oczyścić prawidłowo, gdy wystąpią wyjątki w programie `DemonstrateCleanupWithExceptions` . Używa bloku try/catch do zgłaszania błędów i wywołań `Abort` . Zapoznaj się z przykładem [oczekiwanych wyjątków](expected-exceptions.md) , aby uzyskać więcej informacji na temat przechwytywania wyjątków z wywołań klientów.

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
> Instrukcja using i ServiceHost: wiele aplikacji do samodzielnego udostępniania jest nieco więcej niż Hostowanie usługi i ServiceHost. zamknięcie sporadycznie zgłasza wyjątek, dzięki czemu takie aplikacje mogą bezpiecznie używać instrukcji using z elementem ServiceHost. Należy jednak pamiętać, że ServiceHost. Close może zgłosić `CommunicationException` , więc jeśli aplikacja będzie kontynuować działanie po zamknięciu ServiceHost, należy unikać instrukcji using i postępować zgodnie ze wzorcem.

Po uruchomieniu przykładu odpowiedzi operacji i wyjątki są wyświetlane w oknie konsoli klienta.

Proces klienta uruchamia trzy scenariusze, z których każdy próbuje wywołać `Divide` . Pierwszy scenariusz ilustruje pominięcie kodu z powodu wyjątku od `Dispose` (). W drugim scenariuszu przedstawiono ważny wyjątek, który jest maskowany z powodu wyjątku od `Dispose` (). Trzeci scenariusz przedstawia poprawne czyszczenie.

Oczekiwane dane wyjściowe procesu klienta to:

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
