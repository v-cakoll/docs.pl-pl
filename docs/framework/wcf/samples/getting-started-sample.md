---
title: Wprowadzenie — przykład
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: fc4a7e9acb15f77140732638b2982dd4a9dae9ce
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575189"
---
# <a name="getting-started-sample"></a>Wprowadzenie — przykład

Przykład Wprowadzenie ilustruje sposób implementacji typowej usługi i typowego klienta przy użyciu Windows Communication Foundation (WCF). Ten przykład jest podstawą dla wszystkich innych podstawowych przykładów technologii.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

Usługa opisuje operacje wykonywane w ramach kontraktu usługi, które ujawnia publicznie jako metadane. Usługa zawiera również kod umożliwiający zaimplementowanie operacji.

Klient zawiera definicję kontraktu usługi i klasy proxy w celu uzyskania dostępu do usługi. Kod serwera proxy jest generowany na podstawie metadanych usługi przy użyciu [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).

W systemie Windows Vista usługa jest hostowana w usłudze aktywacji systemu Windows (WAS). W systemach Windows XP i Windows Server 2003 jest on hostowany przez Internet Information Services (IIS) i ASP.NET. Hostowanie usługi w usługach IIS lub zezwala na automatyczne Aktywowanie usługi przy pierwszym dostępie.

> [!NOTE]
> Jeśli wolisz rozpocząć pracę z przykładem, który hostuje usługę w aplikacji konsolowej zamiast usług IIS, [Zobacz przykład samoobsługi.](self-host.md)

Usługa i klient określają szczegóły dostępu w ustawieniach pliku konfiguracji, co zapewnia elastyczność w czasie wdrażania. Obejmuje to definicję punktu końcowego, który określa adres, powiązanie i kontrakt. Powiązanie określa szczegóły dotyczące transportu i zabezpieczeń dotyczące sposobu uzyskiwania dostępu do usługi.

Usługa konfiguruje zachowanie w czasie wykonywania w celu opublikowania jego metadanych.

Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie). Klient wysyła żądania do danej operacji matematycznej i zwraca odpowiedzi usługi z wynikiem. Usługa implementuje `ICalculator` kontrakt zdefiniowany w poniższym kodzie.

```vb
' Define a service contract.
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>
     Public Interface ICalculator
        <OperationContract()>
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
```

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

Implementacja usługi oblicza i zwraca odpowiedni wynik, jak pokazano w poniższym przykładowym kodzie.

```vb
' Service class which implements the service contract.
Public Class CalculatorService
Implements ICalculator
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
Return n1 + n2
End Function

Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
Return n1 - n2
End Function

Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
Return n1 * n2
End Function

Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
Return n1 / n2
End Function
End Class
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

Usługa udostępnia punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji (Web. config), jak pokazano w poniższej konfiguracji przykładowej.

```xaml
<services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
        <!-- ICalculator is exposed at the base address provided by
         host: http://localhost/servicemodelsamples/service.svc.  -->
       <endpoint address=""
              binding="wsHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
       ...
    </service>
</services>
```

Usługa uwidacznia punkt końcowy pod adresem podstawowym dostarczonym przez usługi IIS lub hosta. Powiązanie jest skonfigurowane przy użyciu standardu <xref:System.ServiceModel.WSHttpBinding> , który zapewnia komunikację HTTP i standardowe protokoły usług sieci Web do adresowania i zabezpieczenia. Kontrakt jest `ICalculator` implementowany przez usługę.

Zgodnie z konfiguracją usługa może być dostępna `http://localhost/servicemodelsamples/service.svc` przez klienta programu na tym samym komputerze. Aby klienci na komputerach zdalnych mogli uzyskać dostęp do usługi, należy określić w pełni kwalifikowaną nazwę domeny zamiast hosta lokalnego.

Struktura nie ujawnia domyślnie metadanych. W związku z tym usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> i uwidacznia punkt końcowy wymiany metadanych (Mex) pod adresem `http://localhost/servicemodelsamples/service.svc/mex` . Poniżej przedstawiono konfigurację.

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
       http://localhost/servicemodelsamples/service.svc/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>

  <!--For debugging purposes set the includeExceptionDetailInFaults
   attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True"/>
        <serviceDebug includeExceptionDetailInFaults="False" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

Klient komunikuje się przy użyciu danego typu kontraktu przy użyciu klasy klienta, która jest generowana przez [Narzędzie narzędzia metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Ten wygenerowany klient jest zawarty w pliku generatedClient.cs lub generatedClient. vb. To narzędzie pobiera metadane dla danej usługi i generuje klienta do użytku przez aplikację kliencką w celu komunikowania się przy użyciu danego typu kontraktu. Usługa hostowana musi być dostępna do wygenerowania kodu klienta, ponieważ usługa jest używana do pobierania zaktualizowanych metadanych.

 Uruchom następujące polecenie w wierszu polecenia zestawu SDK w katalogu klienta, aby wygenerować serwer proxy z określonym typem:

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

Aby wygenerować klienta w Visual Basic wpisz następujące polecenie w wierszu polecenia zestawu SDK:

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

Korzystając z wygenerowanego klienta, klient może uzyskać dostęp do danego punktu końcowego usługi przez skonfigurowanie odpowiedniego adresu i powiązania. Podobnie jak w przypadku usługi, klient używa pliku konfiguracji (App. config) do określenia punktu końcowego, z którym chce się skomunikować. Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu, jak pokazano w poniższym przykładzie.

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

Implementacja klienta tworzy wystąpienie klienta i używa określonego interfejsu do rozpoczęcia komunikacji z usługą, jak pokazano w poniższym przykładowym kodzie.

```vb
' Create a client
Dim client As New CalculatorClient()

' Call the Add service operation.
            Dim value1 = 100.0R
            Dim value2 = 15.99R
            Dim result = client.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

' Call the Subtract service operation.
value1 = 145.00R
value2 = 76.54R
result = client.Subtract(value1, value2)
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

' Call the Multiply service operation.
value1 = 9.00R
value2 = 81.25R
result = client.Multiply(value1, value2)
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

' Call the Divide service operation.
value1 = 22.00R
value2 = 7.00R
result = client.Divide(value1, value2)
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

'Closing the client gracefully closes the connection and cleans up resources
```

```csharp
// Create a client.
CalculatorClient client = new CalculatorClient();

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

// Call the Subtract service operation.
value1 = 145.00D;
value2 = 76.54D;
result = client.Subtract(value1, value2);
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

// Call the Multiply service operation.
value1 = 9.00D;
value2 = 81.25D;
result = client.Multiply(value1, value2);
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

// Call the Divide service operation.
value1 = 22.00D;
value2 = 7.00D;
result = client.Divide(value1, value2);
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

//Closing the client releases all communication resources.
client.Close();
```

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

Wprowadzenie przykład pokazuje standardowy sposób tworzenia usługi i klienta. Druga [podstawowa](basic-sample.md) Kompilacja tego przykładu w celu przedstawienia określonych funkcji produktu.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [Instrukcje: hostowanie usługi WCF w programie IIS](../feature-details/how-to-host-a-wcf-service-in-iis.md)
