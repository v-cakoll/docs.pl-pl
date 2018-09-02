---
title: Wprowadzenie — przykład
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: dda11511904d452a3a5101417f8ab8a33c00204f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469911"
---
# <a name="getting-started-sample"></a>Wprowadzenie — przykład
Wprowadzenie do przykładu demonstruje sposób implementacji typowych usług i typowego klienta za pomocą usługi Windows Communication Foundation (WCF). Te przykładowe dane stanowią podstawę dla wszystkich przykładów podstawową technologię.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 Usługa opisuje operacje, które wykonuje w kontrakcie usługi, który publicznie udostępnia się jako metadane. Usługa również zawiera kod implementujący działania.  
  
 Klient zawiera definicję kontraktu usługi i klasy serwera proxy do uzyskiwania dostępu do usługi. Kod serwera proxy jest generowany na podstawie przy użyciu metadanych usługi [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)], usługa jest hostowana w Windows Activation Service (WAS). Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], jest hostowana w usłudze Internet Information Services (IIS) i programu ASP.NET. Hosting w usługach IIS i WAS umożliwia usłudze aktywowany automatycznie, gdy jest on dostępny po raz pierwszy.  
  
> [!NOTE]
>  Jeśli chcesz użyć rozpocząć pracę przy użyciu przykładu hostującym usługę w aplikacji konsoli usług IIS, zobacz [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.  
  
 Usługi i klienta należy określić szczegóły dostępu w ustawieniach pliku konfiguracji, które zapewniają elastyczność w czasie wdrażania. W tym definicji punktu końcowego, który określa adres, powiązania i umowy. Powiązanie określa transportu i zabezpieczenia szczegółowe informacje o jak usługa ma być dostępny.  
  
 Usługa służy do konfigurowania zachowania w czasie wykonywania do publikowania metadanych.  
  
 Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia). Klient wysyła żądania do operacji matematycznych danego i odpowiedzi usługi z wynikiem. Implementuje usługi `ICalculator` kontraktu, który jest zdefiniowany w poniższym kodzie.  
  
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
  
 Wdrożenie usługi oblicza i zwraca odpowiedni wynik, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Usługa udostępnia punkt końcowy do komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji (Web.config), jak pokazano na poniższej przykładowej konfiguracji.  
  
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
  
 Usługa udostępnia punkt końcowy pod podstawowym adresem udostępniane przez hosta usług IIS i WAS. Powiązanie jest skonfigurowane przy użyciu standardowego <xref:System.ServiceModel.WSHttpBinding>, który zapewnia komunikacji HTTP i standardowych protokołów usług sieci Web do adresowania i zabezpieczeń. Kontrakt jest `ICalculator` implementowane przez usługę.  
  
 Zgodnie z konfiguracją, usługi mogą być wyświetlane w http://localhost/servicemodelsamples/service.svc przez klienta na tym samym komputerze. Dla klientów dostępu zdalnego computersto usługi należy określić w pełni kwalifikowanej nazwy domeny zamiast nazwy localhost.  
  
 Struktura nie ujawnia metadanych domyślnie. W efekcie usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> i udostępnia punkt końcowy programu exchange (MEX) metadanych w http://localhost/servicemodelsamples/service.svc/mex. Następującej konfiguracji pokazuje to.  
  
```xaml  
<system.serviceModel>  
  <services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- the mex endpoint is explosed at  
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
  
 Klient komunikuje się przy użyciu typu danego kontraktu za pomocą klasy klienta, który jest generowany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Ta wygenerowanego klienta znajduje się w pliku generatedClient.cs lub generatedClient.vb. To narzędzie służy do pobierania metadanych dla danej usługi i generuje klienta do użycia przez aplikację kliencką do komunikowania się za pomocą typu danego kontraktu. Usługa hostowana musi być dostępny w celu generowania kodu klienta, ponieważ usługi służy do pobierania zaktualizowanych metadanych.  
  
 Uruchom następujące polecenie w wierszu polecenia zestawu SDK w katalogu klienta można wygenerować typizowanego serwera proxy:  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 Aby wygenerować klienta w języku Visual Basic typu następujących poleceń w wierszu polecenia zestawu SDK:  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 Za pomocą wygenerowanego klienta, ten klient uzyskuje dostęp punkt końcowy danej usługi, należy skonfigurować odpowiedni adres i powiązanie. Jak usługa Klient korzysta z plikiem konfiguracyjnym (App.config) do określania punktu końcowego, z którym chce nawiązać połączenia. Konfiguracja punktu końcowego klienta składa się z adresem bezwzględnym dla punktu końcowego usługi, powiązanie i umowy, jak pokazano w poniższym przykładzie.  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 Wdrożenie klienta tworzy klienta i korzysta z kontrolą typów interfejsu na rozpoczęcie komunikowania się z usługą, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Wprowadzenie do przykładu przedstawia standardowy sposób, aby utworzyć usługę i klienta. Druga [podstawowe](../../../../docs/framework/wcf/samples/basic-sample.md) kompilacji w tym przykładzie, aby zademonstrować funkcje określonego produktu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Instrukcje: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
