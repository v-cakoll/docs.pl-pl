---
title: Klient ASMX z usługą WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: 5a0262361eac35ac45c3861deee13133011754ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="asmx-client-with-a-wcf-service"></a>Klient ASMX z usługą WCF
W tym przykładzie pokazano, jak utworzyć usługę za pomocą usługi Windows Communication Foundation (WCF) i uzyskuje dostęp do usługi z innej[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, takich jak klient ASMX.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), obsługiwane przez Internet Information Services (IIS). Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (`Add`, `Subtract`, `Multiply`, i `Divide`). Klient ASMX zgłasza żądań synchronicznych operacji matematycznych i odpowiedzi usługi z wynikiem.  
  
 Implementuje usługi `ICalculator` kontraktu zgodnie z definicją w poniższym kodzie.  
  
```  
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
  
 <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> mapowania typów CLR reprezentację XML. <xref:System.Runtime.Serialization.DataContractSerializer> Inaczej niż XmlSerializer interpretuje niektóre reprezentacji XML. Z systemem innym niż[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generatory serwera proxy, takich jak Wsdl.exe, generowanie bardziej użyteczne interfejsu, gdy jest używany element XmlSerializer. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Jest stosowany do `ICalculator` interfejsu, aby upewnić się, że XmlSerializer służy do mapowania typów CLR XML. Implementacji usługi jest obliczana i zwraca odpowiedni wynik.  
  
 Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji (Web.config). Punkt końcowy składa się z adresu, powiązania i kontrakt. Usługa udostępnia punkt końcowy w bazowym adresie dostarczone przez hosta usługi Internet Information Services (IIS). `binding` Atrybut ma ustawioną basicHttpBinding udostępniający komunikacji HTTP przy użyciu protokołu SOAP 1.1, który jest zgodny ze WS-I BasicProfile 1.1, jak pokazano w poniższych Przykładowa konfiguracja.  
  
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
  
 Klient ASMX komunikuje się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi przy użyciu typu serwera proxy, który jest generowany przez narzędzie Web Services Description Language (WSDL) (Wsdl.exe). Typu serwera proxy znajduje się w pliku generatedClient.cs. Narzędzie WSDL pobiera metadane dla określonej usługi i generuje typu serwera proxy do użytku przez klienta do komunikacji. Domyślnie platformę nie ujawnia żadnych metadanych. Do udostępnienia metadanych wymaganych do utworzenia serwera proxy, należy dodać [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) i ustawić jej `httpGetEnabled` atrybutu `True` jak pokazano w poniższej konfiguracji.  
  
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
  
 Uruchom następujące polecenie w wierszu polecenia w katalogu klienta można wygenerować typu serwera proxy.  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 Za pomocą wygenerowanego typu serwera proxy, klient ma dostęp do danego punktu końcowego konfigurując odpowiednie adresy. Klient korzysta z pliku konfiguracji (App.config) do określenia punktu końcowego do komunikowania się z.  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 Implementacja klienta tworzy wystąpienie klasy typizowanego serwera proxy do rozpoczęcia komunikacji z usługą.  
  
```  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Aby uzyskać więcej informacji o przekazywanie i zwracający dane złożone Zobacz typy: [powiązania danych w kliencie formularzy systemu Windows](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [powiązania danych w kliencie systemu Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), i [danych Powiązanie w kliencie programu ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a>Zobacz też
