---
title: Hostowanie usług IIS przy użyciu kodu wbudowanego
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 47d056e35b92654c8e47647c7273c5d69b37bd97
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594650"
---
# <a name="iis-hosting-using-inline-code"></a>Hostowanie usług IIS przy użyciu kodu wbudowanego

Ten przykład ilustruje sposób implementacji usługi hostowanej przez Internet Information Services (IIS), gdzie kod usługi jest zawarty w pliku svc i jest kompilowany na żądanie. Kod usługi można również zaimplementować bezpośrednio w plikach kodu źródłowego znajdujących się w katalogu \ App_Code aplikacji lub kompilować do zestawu wdrożonego w \Bin. Ten przykład nie pokazuje tych technik.

> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

W przykładzie pokazano typową usługę, która implementuje kontrakt definiujący wzorzec komunikacji z odpowiedzią na żądanie. Usługa jest hostowana w usługach IIS, a kod usługi jest całkowicie zawarty w pliku Service. svc. Usługa jest uruchomiona na hoście i skompilowana na żądanie przez pierwszą wiadomość wysłaną do usługi. Nie ma potrzeby wstępnej kompilacji. Usługa implementuje `ICalculator` kontrakt zgodnie z definicją w następującym kodzie:

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

Implementacja usługi oblicza i zwraca odpowiedni wynik.

`<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>`

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Po skompilowaniu rozwiązania Uruchom polecenie Setup. bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS 7,0. Katalog ServiceModelSamples powinien teraz pojawić się jako aplikacja usług IIS 7,0.

4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md). Aby zapoznać się z przykładem dotyczącym tworzenia aplikacji klienckiej, która może wywołać tę usługę, zobacz [How to: Create an Client](../how-to-create-a-wcf-client.md).

## <a name="see-also"></a>Zobacz też

- [Przykłady hostingu i trwałości usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
