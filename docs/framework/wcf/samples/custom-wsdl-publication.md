---
title: Niestandardowa publikacja WSDL
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 8674d852be45119b247ec10bbc639922850d5a90
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928855"
---
# <a name="custom-wsdl-publication"></a>Niestandardowa publikacja WSDL
W tym przykładzie pokazano, jak:  
  
- Zaimplementuj <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> obiekt na atrybucie <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> niestandardowym, aby wyeksportować właściwości atrybutów jako adnotacje WSDL.  
  
- Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> , aby zaimportować niestandardowe adnotacje WSDL.  
  
- <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> Zaimplementuj <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> i w niestandardowym zachowaniu kontraktu oraz zachowaniem niestandardowej operacji, aby zapisać zaimportowane adnotacje jako komentarze w języku CodeDOM dla zaimportowanego kontraktu i operacji.  
  
- Użyj narzędzia, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> C# aby pobrać WSDL, a w celu zaimportowania WSDL przy użyciu niestandardowego importera WSDL, oraz do generowania kodu klienta Windows Communication Foundation (WCF) z adnotacjami WSDL jako komentarze///i "'" w i <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Visual Basic.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 Usługa w tym przykładzie jest oznaczona dwoma atrybutami niestandardowymi. Pierwszy, `WsdlDocumentationAttribute`,, akceptuje ciąg w konstruktorze i może być stosowany w celu zapewnienia interfejsu lub operacji kontraktu z ciągiem opisującym jego użycie. Sekunda, `WsdlParamOrReturnDocumentationAttribute`,, może być stosowana do zwracanych wartości lub parametrów w celu opisania tych wartości w operacji. Poniższy przykład przedstawia kontrakt `ICalculator`usługi, opisany przy użyciu tych atrybutów.  
  
```csharp  
// Define a service contract.      
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,   
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,   
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 `WsdlDocumentationAttribute` Implementuje <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Description.OperationDescription> i, więc wystąpienia atrybutów są dodawane do odpowiadających lub gdy usługa jest otwarta. <xref:System.ServiceModel.Description.IOperationBehavior> <xref:System.ServiceModel.Description.IContractBehavior> Ten atrybut również implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension>. Gdy <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> jest wywoływana <xref:System.ServiceModel.Description.WsdlExporter> , to jest używana do <xref:System.ServiceModel.Description.WsdlContractConversionContext> eksportowania metadanych i zawierający obiekty opisu usługi są przenoszone jako parametry włączające modyfikację eksportowanych metadanych.  
  
 W tym przykładzie, w zależności od tego, czy obiekt kontekstu eksportu ma <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Description.OperationDescription>lub a, komentarz jest wyodrębniany z atrybutu przy użyciu właściwości text i jest dodawany do elementu adnotacji WSDL, jak pokazano w poniższym kodzie.  
  
```csharp  
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (contractDescription != null)  
    {  
        // Inside this block it is the contract-level comment attribute.  
        // This.Text returns the string for the contract attribute.  
        // Set the doc element; if this isn't done first, there is no XmlElement in the   
        // DocumentElement property.  
        context.WsdlPortType.Documentation = string.Empty;  
        // Contract comments.  
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;  
        XmlElement summaryElement = owner.CreateElement("summary");  
        summaryElement.InnerText = this.Text;  
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);  
    }  
    else  
    {  
        Operation operation = context.GetOperation(operationDescription);  
        if (operation != null)  
        {  
            // We are dealing strictly with the operation here.  
            // This.Text returns the string for the operation-level attributes.  
            // Set the doc element; if this isn't done first, there is no XmlElement in the   
            // DocumentElement property.  
            operation.Documentation = String.Empty;  
  
            // Operation C# triple comments.  
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;  
            XmlElement newSummaryElement = owner.CreateElement("summary");  
            newSummaryElement.InnerText = this.Text;  
            operation.DocumentationElement.AppendChild(newSummaryElement);  
```  
  
 Jeśli operacja jest eksportowana, przykład używa odbicia w celu uzyskania `WsdlParamOrReturnDocumentationAttribute` wartości parametrów i zwracanych wartości i dodaje je do elementów adnotacji WSDL dla tej operacji w następujący sposób.  
  
```csharp  
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 Następnie próbka publikuje metadane w standardowym sposobie przy użyciu następującego pliku konfiguracji.  
  
```xml  
<services>  
  <service   
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a>Klient Svcutil  
 Ten przykład nie używa programu Svcutil. exe. Umowa jest dostępna w pliku generatedClient.cs, dzięki czemu po przykładzie zademonstrowano niestandardowy import WSDL i generowanie kodu, usługa może być wywoływana. Aby użyć następującego niestandardowego importera WSDL na potrzeby tego przykładu, można uruchomić program Svcutil. exe i `/svcutilConfig` określić opcję, podając ścieżkę do pliku konfiguracji klienta użytego w tym przykładzie, który odwołuje `WsdlDocumentation.dll` się do biblioteki. Aby załadować `WsdlDocumentationImporter`plik, program Svuctil. exe musi mieć możliwość zlokalizowania i `WsdlDocumentation.dll` załadowania biblioteki, co oznacza, że jest ona zarejestrowana w globalnej pamięci podręcznej zestawów, w ścieżce lub znajduje się w tym samym katalogu, co Svcutil. exe. W przypadku podstawowego przykładu, najłatwiejszym rozwiązaniem jest skopiowanie Svcutil. exe i pliku konfiguracji klienta do tego samego katalogu, co `WsdlDocumentation.dll` spowoduje jego uruchomienie.  
  
## <a name="the-custom-wsdl-importer"></a>Niestandardowy importer WSDL  
 Obiekt <xref:System.ServiceModel.Description.IWsdlImportExtension> <xref:System.ServiceModel.Description.IContractBehavior> <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> niestandardowy zostanie również zaimplementowany <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> i <xref:System.ServiceModel.Description.IOperationBehavior> dodany do zaimportowanych punktów końcowych i i zostanie wywołany w celu zmodyfikowania generowania kodu podczas kontraktu lub operacji `WsdlDocumentationImporter` Trwa tworzenie kodu.  
  
 Po pierwsze, w <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metodzie, przykład określa, czy adnotacja WSDL znajduje się na poziomie kontraktu lub operacji, i dodaje się do niego w odpowiednim zakresie, przekazując zaimportowany tekst adnotacji do jego konstruktora.  
  
```csharp  
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 Po wygenerowaniu kodu system wywołuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metody i <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> , przekazując odpowiednie informacje kontekstu. Przykład formatuje niestandardowe adnotacje WSDL i wstawia je jako komentarze do CodeDom.  
  
```csharp  
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a>Aplikacja kliencka  
 Aplikacja kliencka ładuje niestandardowego importera WSDL przez określenie go w pliku konfiguracyjnym aplikacji.  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"   
  binding="wsHttpBinding"   
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 Po określeniu importera niestandardowego system metadanych programu WCF ładuje niestandardowego importera do dowolnego <xref:System.ServiceModel.Description.WsdlImporter> utworzonego w tym celu. Ten przykład korzysta z <xref:System.ServiceModel.Description.MetadataExchangeClient> programu w celu pobrania metadanych <xref:System.ServiceModel.Description.WsdlImporter> , odpowiednio skonfigurowanych do importowania metadanych przy użyciu importera niestandardowego tworzonego przez <xref:System.ServiceModel.Description.ServiceContractGenerator> przykład, a następnie do skompilowania zmodyfikowanych informacji o kontrakcie w obu Visual Basic kod C# klienta, który może być używany w programie Visual Studio do obsługi technologii IntelliSense lub kompilowany do dokumentacji XML.  
  
```csharp  
/// From WSDL Documentation:  
///   
/// <summary>The ICalculator contract performs basic calculation   
/// services.</summary>   
///   
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Add operation adds two numbers and returns the   
    /// result.</summary><returns>The result of adding the two arguments   
    /// together.</returns><param name="n1">The first value to add.</param><param   
    /// name="n2">The second value to add.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Subtract operation subtracts the second argument from the   
    /// first.</summary><returns>The result of the second argument subtracted from the   
    /// first.</returns><param name="n1">The value from which the second is   
    /// subtracted.</param><param name="n2">The value that is subtracted from the   
    /// first.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The   
    /// result of multiplying the first and second arguments.</returns><param   
    /// name="n1">The first value to multiply.</param><param name="n2">The second value   
    /// to multiply.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Divide operation returns the value of the first argument divided   
    /// by the second argument.</summary><returns>The result of dividing the first   
    /// argument by the second.</returns><param name="n1">The numerator.</param><param   
    /// name="n2">The denominator.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
