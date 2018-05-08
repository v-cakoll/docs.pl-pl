---
title: Wprowadzenie — przykład
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: dfba7062d4226f3644aa6c4cc0efcd7c5fb9eab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="getting-started-sample"></a>Wprowadzenie — przykład
Uruchamianie przykładowych pokazano, jak do zaimplementowania typowych usługi i typowego klienta za pomocą usługi Windows Communication Foundation (WCF). W tym przykładzie stanowi podstawę dla wszystkich innych przykładów podstawową technologię.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 Usługa zawiera opis operacji wykonywanych w kontrakcie usługi, który ujawnia on publicznie jak metadanych. Usługa zawiera również kod do wykonania operacji.  
  
 Klient zawiera definicję kontraktu usługi i klasy serwera proxy, aby uzyskać dostęp do usługi. Kod serwera proxy jest generowany na podstawie przy użyciu metadanych usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)], usługa jest obsługiwana w Windows Activation Service (WAS). Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], jest obsługiwany przez usługi Internet Information Services (IIS) i programu ASP.NET. Hosting w usługach IIS lub WAS umożliwia usłudze aktywowany automatycznie, gdy jest on dostępny po raz pierwszy.  
  
> [!NOTE]
>  Jeśli chcesz rozpocząć pracę z przykładowym obsługującego usługę w aplikacji konsoli usług IIS, zobacz [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.  
  
 Usługa i klient Określ szczegóły dotyczące dostępu w pliku ustawień konfiguracji, które zapewniają elastyczność w czasie wdrażania. Dotyczy to również definicji punktu końcowego, który określa address, binding i contract. Powiązanie określa szczegóły transportu i zabezpieczeń dla jak usługa ma być dostępny.  
  
 Usługa konfiguruje zachowania w czasie wykonywania Publikowanie metadanych.  
  
 Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia). Klient wysyła żądania do operacji matematycznych danego i odpowiedzi usługi z wynikiem. Implementuje usługi `ICalculator` kontraktu, który jest zdefiniowany w poniższym kodzie.  
  
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
  
 Implementacji usługi jest obliczana i zwraca odpowiednie wynik, jak pokazano w poniższym przykładzie kodzie.  
  
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
  
 Usługa przedstawia punktu końcowego w celu komunikowania się z usługą, zdefiniowane przy użyciu pliku konfiguracji (Web.config), jak pokazano w poniższym Przykładowa konfiguracja.  
  
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
  
 Usługa udostępnia punkt końcowy pod adresem podstawowa podał hosta usług IIS lub WAS. Powiązanie jest skonfigurowane z normą <xref:System.ServiceModel.WSHttpBinding>, co umożliwia komunikacji HTTP i standardowe protokoły usług sieci Web adresowanie i zabezpieczeń. Kontrakt jest `ICalculator` zaimplementowanych przez usługę.  
  
 Zgodnie z konfiguracją, usługi mogą być wyświetlane w http://localhost/servicemodelsamples/service.svc przez klienta na tym samym komputerze. W przypadku klientów dostępu zdalnego computersto usługi należy określić w pełni kwalifikowanej nazwy domeny zamiast nazwy localhost.  
  
 Domyślnie platformę nie ujawnia metadanych. W efekcie usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> i udostępnia punktu końcowego (MEX) wymiany metadanych w http://localhost/servicemodelsamples/service.svc/mex. Następująca konfiguracja pokazano to.  
  
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
  
 Klient komunikuje się za pomocą typu danego kontraktu przy użyciu klasy klienta, który jest generowany przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Ta wygenerowanego klienta znajduje się w pliku generatedClient.cs lub generatedClient.vb. Narzędzie to pobiera metadane dla danej usługi i generuje klienta do użycia przez aplikację klienta do komunikowania się przy użyciu typu danego kontraktu. Usługa hostowana musi być dostępny w celu generowania kodu klienta, ponieważ usługi służy do pobierania metadanych zaktualizowane.  
  
 Uruchom następujące polecenie w wierszu polecenia SDK w katalogu klienta można wygenerować typu serwera proxy:  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 Aby wygenerować klienta w Visual Basic, wpisz następujące polecenie w wierszu polecenia SDK:  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 Za pomocą wygenerowanego klienta, klient ma dostęp do danego punktu końcowego, konfigurując odpowiednie adres i powiązanie. Jak usługi Klient korzysta z pliku konfiguracji (App.config) do określenia punktu końcowego, z którą chce komunikacji. Konfiguracja punktu końcowego klienta składa się z adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu, jak pokazano w poniższym przykładzie.  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 Wdrożenie klienta tworzy klienta i korzysta z typu interfejsu do rozpoczęcia komunikacji z usługą, jak pokazano w poniższym przykładzie kodzie.  
  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Przykładowe wprowadzenie zawiera standardowy sposób, aby utworzyć usługę i klienta. Druga [podstawowe](../../../../docs/framework/wcf/samples/basic-sample.md) kompilacji w tym przykładzie, aby zademonstrować funkcje określonego produktu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Instrukcje: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
