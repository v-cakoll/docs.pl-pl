---
title: Niestandardowa publikacja WSDL
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: ae6d5fdf243d5000090e993bd3353c6180d0ccaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145062"
---
# <a name="custom-wsdl-publication"></a>Niestandardowa publikacja WSDL
W tym przykładzie pokazano, jak:  
  
- Zaimplementuj <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> atrybut niestandardowy <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> do eksportowania właściwości atrybutu jako adnotacji WSDL.  
  
- Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> w celu zaimportowania niestandardowych adnotacji WSDL.  
  
- Zaimplementuj <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> i <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> na zachowanie umowy niestandardowej i zachowanie operacji niestandardowej, odpowiednio, aby zapisać importowane adnotacje jako komentarze w CodeDom dla importowanego kontraktu i operacji.  
  
- <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Użyj, aby pobrać WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> do zaimportowania WSDL przy użyciu niestandardowego importera WSDL i <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> do generowania kodu klienta Windows Communication Foundation (WCF) z adnotacjami WSDL jako /// i ''' komentarze w języku C# i Visual Basic.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 Usługa w tym przykładzie jest oznaczona dwoma atrybutami niestandardowymi. Pierwszy, `WsdlDocumentationAttribute`, akceptuje ciąg w konstruktorze i mogą być stosowane w celu zapewnienia interfejsu umowy lub operacji z ciągiem, który opisuje jego użycie. Drugi , `WsdlParamOrReturnDocumentationAttribute`można zastosować do zwracanych wartości lub parametrów w celu opisania tych wartości w operacji. Poniższy przykład przedstawia umowę `ICalculator`serwisową, opisane przy użyciu tych atrybutów.  
  
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
  
 Implementuje `WsdlDocumentationAttribute` <xref:System.ServiceModel.Description.IContractBehavior> i <xref:System.ServiceModel.Description.IOperationBehavior>, więc wystąpienia atrybutu są <xref:System.ServiceModel.Description.ContractDescription> dodawane do odpowiednich lub <xref:System.ServiceModel.Description.OperationDescription> po otwarciu usługi. Atrybut implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension>również . Gdy <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> jest wywoływana, <xref:System.ServiceModel.Description.WsdlExporter> który jest używany do <xref:System.ServiceModel.Description.WsdlContractConversionContext> eksportowania metadanych i który zawiera obiekty opisu usługi są przekazywane jako parametry umożliwiające modyfikację eksportowanych metadanych.  
  
 W tym przykładzie, w zależności od <xref:System.ServiceModel.Description.ContractDescription> tego, czy obiekt kontekstu eksportu ma lub , <xref:System.ServiceModel.Description.OperationDescription>komentarz jest wyodrębniany z atrybutu przy użyciu właściwości text i jest dodawany do elementu adnotacji WSDL, jak pokazano w poniższym kodzie.  
  
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
        }
    }
}
```  
  
 Jeśli operacja jest eksportowana, próbka używa odbicia `WsdlParamOrReturnDocumentationAttribute` w celu uzyskania dowolnych wartości parametrów i wartości zwracanych i dodaje je do elementów adnotacji WSDL dla tej operacji w następujący sposób.  
  
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
  
 Następnie w próbce publikuje metadane w standardowy sposób, używając następującego pliku konfiguracyjnego.  
  
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
 W tym przykładzie nie jest używany plik Svcutil.exe. Umowa jest dostarczana w pliku generatedClient.cs, dzięki czemu po przykładzie pokazuje niestandardowe importU WSDL i generowania kodu, usługa może być wywoływana. Aby użyć następującego niestandardowego importera WSDL w tym przykładzie, można `/svcutilConfig` uruchomić program Svcutil.exe i określić opcję, nadając ścieżkę do pliku konfiguracji klienta używanego w tym przykładzie, który odwołuje się do `WsdlDocumentation.dll` biblioteki. Aby `WsdlDocumentationImporter`załadować , jednak Svuctil.exe musi być `WsdlDocumentation.dll` w stanie zlokalizować i załadować bibliotekę, co oznacza, że jest ona zarejestrowana w globalnej pamięci podręcznej zestawu, w ścieżce lub znajduje się w tym samym katalogu co Svcutil.exe. W przypadku próbki podstawowej, takiej jak ta, najłatwiejszą rzeczą do zrobienia jest skopiowanie pliku Svcutil.exe i pliku konfiguracyjnego klienta do tego samego katalogu, co `WsdlDocumentation.dll` ten katalog i uruchomienie go stamtąd.  
  
## <a name="the-custom-wsdl-importer"></a>Niestandardowy importer WSDL  
 <xref:System.ServiceModel.Description.IWsdlImportExtension> Obiekt `WsdlDocumentationImporter` niestandardowy implementuje <xref:System.ServiceModel.Description.IContractBehavior> również i <xref:System.ServiceModel.Description.IOperationBehavior> mają być dodawane <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> do <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> importowanych ServiceEndpoints i i do wywołania, aby zmodyfikować generowanie kodu podczas tworzenia kodu umowy lub operacji.  
  
 Po pierwsze <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> w metodzie próbki określa, czy adnotacja WSDL jest na poziomie umowy lub operacji i dodaje się jako zachowanie w odpowiednim zakresie, przekazując importowany tekst adnotacji do jego konstruktora.  
  
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
  
 Następnie po wygenerowaniu kodu system wywołuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> metody i, przekazując odpowiednie informacje kontekstowe. Przykład formatuje niestandardowe adnotacje WSDL i wstawia je jako komentarze do CodeDom.  
  
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
 Aplikacja kliencka ładuje niestandardowego importera WSDL, określając go w pliku konfiguracji aplikacji.  
  
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
  
 Po określeniu importera niestandardowego system metadanych WCF <xref:System.ServiceModel.Description.WsdlImporter> ładuje importera niestandardowego do dowolnego utworzonego w tym celu. W tym przykładzie użyto <xref:System.ServiceModel.Description.MetadataExchangeClient> do <xref:System.ServiceModel.Description.WsdlImporter> pobrania metadanych, poprawnie skonfigurowane do importowania metadanych przy użyciu importera niestandardowego próbka tworzy i <xref:System.ServiceModel.Description.ServiceContractGenerator> skompilować zmodyfikowane informacje umowy do kodu klienta języka Visual Basic i C#, który może służyć w programie Visual Studio do obsługi intellisense lub skompilowany w dokumentacji XML.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
