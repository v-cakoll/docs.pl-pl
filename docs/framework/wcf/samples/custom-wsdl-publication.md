---
title: Niestandardowa publikacja WSDL
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 6b83f225c7c410c3f7dc86f39978b5fef32ae3f5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650166"
---
# <a name="custom-wsdl-publication"></a>Niestandardowa publikacja WSDL
Niniejszy przykład pokazuje, jak:  
  
- Implementowanie <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> na niestandardowy <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atrybutu, aby wyeksportować właściwości atrybutu jako adnotacje WSDL.  
  
- Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> można zaimportować niestandardowych adnotacje WSDL.  
  
- Implementowanie <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> i <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> na niestandardowy umowę zachowanie i zachowanie niestandardowe operacji, odpowiednio, zapis adnotacji importowany jako komentarze w CodeDom dla importowanych kontraktu i operacji.  
  
- Użyj <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> można pobrać pliku WSDL, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> można zaimportować pliku WSDL, przy użyciu niestandardowych importerów WSDL i <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> do generowania kodu klienta usługi Windows Communication Foundation (WCF) z adnotacjami WSDL jako / / / i ''' komentarzy w języku C# i Visual Podstawowe.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 Usługi w tym przykładzie jest oznaczona za pomocą dwóch atrybutów niestandardowych. Pierwsza strona, `WsdlDocumentationAttribute`akceptuje ciąg w Konstruktorze i mogą być stosowane do interfejsu kontraktu lub operację, podając ciąg, który opisuje jego użycia. Druga Strona, `WsdlParamOrReturnDocumentationAttribute`, mogą być stosowane do zwracania wartości lub parametry do opisania tych wartości w operacji. W poniższym przykładzie pokazano umowę serwisową `ICalculator`, które zostały opisane, przy użyciu tych atrybutów.  
  
```  
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
  
 `WsdlDocumentationAttribute` Implementuje <xref:System.ServiceModel.Description.IContractBehavior> i <xref:System.ServiceModel.Description.IOperationBehavior>, więc instancje wieloatrybutowe są dodawane do odpowiednich <xref:System.ServiceModel.Description.ContractDescription> lub <xref:System.ServiceModel.Description.OperationDescription> po otwarciu usługi. Ten atrybut implementuje również <xref:System.ServiceModel.Description.IWsdlExportExtension>. Gdy <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> jest wywoływana, <xref:System.ServiceModel.Description.WsdlExporter> służący do wyeksportowania metadanych i <xref:System.ServiceModel.Description.WsdlContractConversionContext> zawierający opis usługi, które obiekty są przekazywane w jako parametry umożliwiające modyfikowanie metadane wyeksportowane.  
  
 W tym przykładzie, w zależności od tego, czy obiekt kontekstu eksportu ma <xref:System.ServiceModel.Description.ContractDescription> lub <xref:System.ServiceModel.Description.OperationDescription>, komentarz są wyodrębniane z atrybutu za pomocą właściwości text i zostanie dodany do elementu adnotacji WSDL, jak pokazano w poniższym kodzie.  
  
```  
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
  
 Jeśli operacja jest eksportowany, próbki używa odbicia, aby uzyskać dowolne `WsdlParamOrReturnDocumentationAttribute` wartości dla parametrów i zwracanych wartości i dodaje je do elementów adnotacji WSDL dla tej operacji w następujący sposób.  
  
```  
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
  
 Przykład następnie publikuje metadane w sposób standardowy, przy użyciu następującego pliku konfiguracji.  
  
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
  
## <a name="svcutil-client"></a>Klient narzędzia svcutil  
 W tym przykładzie nie używa Svcutil.exe. Kontrakt jest podana w generatedClient.cs pliku, więc po próbki demonstrujące niestandardowe importu WSDL i generowania kodu, usługa może być wywołana. Aby użyć następujących niestandardowe importera WSDL w tym przykładzie, można uruchomić Svcutil.exe i określ `/svcutilConfig` opcji, podając ścieżkę do pliku konfiguracji klienta, które są używane w tym przykładzie, który odwołuje się `WsdlDocumentation.dll` biblioteki. Aby załadować `WsdlDocumentationImporter`, jednak Svuctil.exe musi być w stanie do lokalizowania i ładowania `WsdlDocumentation.dll` biblioteki, co oznacza, że wartość jest zarejestrowany w globalnej pamięci podręcznej, a w ścieżce, lub znajduje się w tym samym katalogu co Svcutil.exe. Podstawowy przykład takich, najłatwiejszym jest skopiowanie Svcutil.exe i pliku konfiguracji klienta, w tym samym katalogu co `WsdlDocumentation.dll` i uruchom go z tego miejsca.  
  
## <a name="the-custom-wsdl-importer"></a>Importer niestandardowych plików WSDL  
 Niestandardowy <xref:System.ServiceModel.Description.IWsdlImportExtension> obiektu `WsdlDocumentationImporter` implementuje również <xref:System.ServiceModel.Description.IContractBehavior> i <xref:System.ServiceModel.Description.IOperationBehavior> mają zostać dodane do importowanych ServiceEndpoints i <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> i <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> wywoływanej do modyfikowania generowania kodu po umowy lub operacji Trwa tworzenie kodu.  
  
 Pierwszy w <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metody przykład określa, czy adnotacja WSDL znajduje się na poziomie umowy lub operacji i dodaje się jako zachowanie w zakresie odpowiednie, przekazując tekst adnotacji zaimportowane do jej konstruktora.  
  
```  
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
  
 Następnie, gdy kod jest generowany, system wywołuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> i <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> metod przekazywania informacji odpowiedniego kontekstu. Próbka formatów niestandardowych adnotacje WSDL i wstawia je jako komentarze do CodeDom.  
  
```  
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
 Aplikacja kliencka ładuje niestandardowe importerów WSDL, określając je w pliku konfiguracyjnym aplikacji.  
  
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
  
 Gdy określono niestandardowe importera WCF metadanych załadowanie importera niestandardowych w każdym <xref:System.ServiceModel.Description.WsdlImporter> utworzone w tym celu. W tym przykładzie użyto <xref:System.ServiceModel.Description.MetadataExchangeClient> można pobrać metadanych, <xref:System.ServiceModel.Description.WsdlImporter> prawidłowo skonfigurowane, aby zaimportować metadane za pomocą niestandardowych importera Przykładowa aplikacja tworzy, a <xref:System.ServiceModel.Description.ServiceContractGenerator> skompilować informacje na temat modyfikacji umowy na obu Visual Basic i C# kod klienta, który mogą być używane w programie Visual Studio do obsługi technologii Intellisense lub skompilowane do dokumentacji XML.  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
