---
title: Klient ASMX z usługą WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: ed3cceb7806e0f0b71b9290da001ba0659e28f3c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045188"
---
# <a name="asmx-client-with-a-wcf-service"></a>Klient ASMX z usługą WCF

W tym przykładzie pokazano, jak utworzyć usługę przy użyciu programu Windows Communication Foundation (WCF), a następnie uzyskać dostęp do usługi z poziomu klienta niepochodzącego z programu WCF, takiego jak Klient ASMX.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Ten przykład składa się z programu konsolowego klienta (exe) i biblioteki usług (. dll) hostowanej przez Internet Information Services (IIS). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (`Add`, `Subtract`, `Multiply`i `Divide`). Klient ASMX wykonuje synchroniczne żądania do operacji matematycznej i odpowiedzi usługi z wynikiem.

Usługa implementuje `ICalculator` kontrakt zgodnie z definicją w poniższym kodzie.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]
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

<xref:System.Runtime.Serialization.DataContractSerializer> I<xref:System.Xml.Serialization.XmlSerializer> Mapuj typy CLR na reprezentację XML. <xref:System.Runtime.Serialization.DataContractSerializer> Interpretuje niektóre reprezentacje XML inaczej niż XmlSerializer. Generatory proxy inne niż WCF, takie jak WSDL. exe, generują interfejs bardziej użyteczny, gdy jest używany element XmlSerializer. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Jest stosowany`ICalculator` do interfejsu, aby upewnić się, że XmlSerializer jest używany do mapowania typów CLR na XML. Implementacja usługi oblicza i zwraca odpowiedni wynik.

Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji (Web. config). Punkt końcowy składa się z adresu, powiązania i kontraktu. Usługa uwidacznia punkt końcowy pod adresem podstawowym dostarczonym przez hosta Internet Information Services (IIS). `binding` Atrybut jest ustawiany na BasicHttpBinding, który zapewnia komunikację HTTP przy użyciu protokołu SOAP 1,1, który jest zgodny z protokołem WS-I BasicProfile 1,1, jak pokazano w poniższej konfiguracji przykładowej.

```xml
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->
    <endpoint address=""
              binding="basicHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
</services>
```

Klient ASMX komunikuje się z usługą WCF przy użyciu serwera proxy z określonym typem, który jest generowany przez narzędzie Web Services Description Language (WSDL) (WSDL. exe). Typ serwera proxy jest zawarty w pliku generatedClient.cs. Narzędzie WSDL pobiera metadane dla określonej usługi i generuje serwer proxy z określonym typem, który będzie używany przez klienta do komunikacji. Domyślnie platforma nie ujawnia żadnych metadanych. Aby udostępnić metadane wymagane do wygenerowania serwera proxy, należy dodać [ \<> ServiceMetadata](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) i ustawić jego `httpGetEnabled` atrybut na `True` tak jak pokazano w poniższej konfiguracji.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <!-- Setting httpGetEnabled to True on the serviceMetadata
           behavior exposes the service's wsdl at <base address>?wsdl :
           http://localhost/servicemodelsamples/service.svc?wsdl -->
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

Uruchom następujące polecenie w wierszu polecenia w katalogu klienta, aby wygenerować serwer proxy z określonym typem.

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

Korzystając z wygenerowanego typu serwera proxy, klient może uzyskać dostęp do danego punktu końcowego usługi przez skonfigurowanie odpowiedniego adresu. Klient używa pliku konfiguracji (App. config), aby określić punkt końcowy do komunikacji.

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

Implementacja klienta Konstruuje wystąpienie serwera proxy o określonym typie, aby rozpocząć komunikację z usługą.

```csharp
// Create a client to the CalculatorService.
using (CalculatorService client = new CalculatorService())
{
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

}

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
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

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!NOTE]
> Aby uzyskać więcej informacji na temat przekazywania i zwracania złożonych typów danych, zobacz: [Powiązanie danych w kliencie Windows Forms](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [powiązanie danych w kliencie Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md)i [powiązanie danych w kliencie ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
