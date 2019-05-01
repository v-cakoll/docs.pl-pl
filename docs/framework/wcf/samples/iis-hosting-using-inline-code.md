---
title: Hostowanie usług IIS przy użyciu kodu wbudowanego
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 8e401d6ce73c036188d13f40c1293abd1f0de58c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781475"
---
# <a name="iis-hosting-using-inline-code"></a>Hostowanie usług IIS przy użyciu kodu wbudowanego

Ten przykład demonstruje sposób implementacji usługi hostowanej przez Internetowe usługi informacyjne (IIS), gdzie znajduje się kod usługi wiersz w pliku svc i jest kompilowany na żądanie. Kod usługi mogą być implementowane bezpośrednio w plikach kodu źródłowego, znajduje się w katalogu \App_Code aplikacji lub skompilowane do wdrożenia w \bin zestawu. W tym przykładzie nie przedstawiono tu tych metod.

> [!NOTE]
> Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

W przykładzie pokazano Typowa usługa, która implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Usługa jest hostowana w usługach IIS i kodu usługi jest całkowicie zawarty w pliku Service.svc. Usługa hosta — aktywowaniu i kompilowane na żądanie przez pierwszą wiadomością wysłaną do usługi. Nie konieczności wstępnej kompilacji nie istnieje. Implementuje usługi `ICalculator` Umowę zgodnie z definicją w poniższym kodzie:

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

```svc
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>
```

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

Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Po rozwiązaniu został utworzony, uruchom Setup.bat jest, aby skonfigurować aplikację ServiceModelSamples w [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Katalog ServiceModelSamples teraz powinny się wyświetlać jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji.

4. Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Na przykład o tym, jak utworzyć aplikację kliencką, która może wywołać tej usługi, zobacz [jak: Tworzenie klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).

## <a name="see-also"></a>Zobacz także

- [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
