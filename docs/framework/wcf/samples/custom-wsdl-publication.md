---
title: Niestandardowa publikacja WSDL
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 0d5ceecebc5f45d62bac7fd0aaa0f8515a469515
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045115"
---
# <a name="custom-wsdl-publication"></a><span data-ttu-id="5a1b1-102">Niestandardowa publikacja WSDL</span><span class="sxs-lookup"><span data-stu-id="5a1b1-102">Custom WSDL Publication</span></span>
<span data-ttu-id="5a1b1-103">W tym przykładzie pokazano, jak:</span><span class="sxs-lookup"><span data-stu-id="5a1b1-103">This sample demonstrates how to:</span></span>  
  
- <span data-ttu-id="5a1b1-104">Zaimplementuj <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> obiekt na atrybucie <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> niestandardowym, aby wyeksportować właściwości atrybutów jako adnotacje WSDL.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-104">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
- <span data-ttu-id="5a1b1-105">Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> , aby zaimportować niestandardowe adnotacje WSDL.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-105">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
- <span data-ttu-id="5a1b1-106"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> Zaimplementuj <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> i w niestandardowym zachowaniu kontraktu oraz zachowaniem niestandardowej operacji, aby zapisać zaimportowane adnotacje jako komentarze w języku CodeDOM dla zaimportowanego kontraktu i operacji.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-106">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
- <span data-ttu-id="5a1b1-107">Użyj narzędzia, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> C# aby pobrać WSDL, a w celu zaimportowania WSDL przy użyciu niestandardowego importera WSDL, oraz do generowania kodu klienta Windows Communication Foundation (WCF) z adnotacjami WSDL jako komentarze///i "'" w i <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-107">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate Windows Communication Foundation (WCF) client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a1b1-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="5a1b1-109">Usługa</span><span class="sxs-lookup"><span data-stu-id="5a1b1-109">Service</span></span>  
 <span data-ttu-id="5a1b1-110">Usługa w tym przykładzie jest oznaczona dwoma atrybutami niestandardowymi.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-110">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="5a1b1-111">Pierwszy, `WsdlDocumentationAttribute`,, akceptuje ciąg w konstruktorze i może być stosowany w celu zapewnienia interfejsu lub operacji kontraktu z ciągiem opisującym jego użycie.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-111">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="5a1b1-112">Sekunda, `WsdlParamOrReturnDocumentationAttribute`,, może być stosowana do zwracanych wartości lub parametrów w celu opisania tych wartości w operacji.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-112">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="5a1b1-113">Poniższy przykład przedstawia kontrakt `ICalculator`usługi, opisany przy użyciu tych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-113">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
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
  
 <span data-ttu-id="5a1b1-114">`WsdlDocumentationAttribute` Implementuje <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Description.OperationDescription> i, więc wystąpienia atrybutów są dodawane do odpowiadających lub gdy usługa jest otwarta. <xref:System.ServiceModel.Description.IOperationBehavior> <xref:System.ServiceModel.Description.IContractBehavior></span><span class="sxs-lookup"><span data-stu-id="5a1b1-114">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="5a1b1-115">Ten atrybut również implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-115">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="5a1b1-116">Gdy <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> jest wywoływana <xref:System.ServiceModel.Description.WsdlExporter> , to jest używana do <xref:System.ServiceModel.Description.WsdlContractConversionContext> eksportowania metadanych i zawierający obiekty opisu usługi są przenoszone jako parametry włączające modyfikację eksportowanych metadanych.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-116">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="5a1b1-117">W tym przykładzie, w zależności od tego, czy obiekt kontekstu eksportu ma <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Description.OperationDescription>lub a, komentarz jest wyodrębniany z atrybutu przy użyciu właściwości text i jest dodawany do elementu adnotacji WSDL, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-117">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="5a1b1-118">Jeśli operacja jest eksportowana, przykład używa odbicia w celu uzyskania `WsdlParamOrReturnDocumentationAttribute` wartości parametrów i zwracanych wartości i dodaje je do elementów adnotacji WSDL dla tej operacji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-118">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
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
  
 <span data-ttu-id="5a1b1-119">Następnie próbka publikuje metadane w standardowym sposobie przy użyciu następującego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-119">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
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
  
## <a name="svcutil-client"></a><span data-ttu-id="5a1b1-120">Klient Svcutil</span><span class="sxs-lookup"><span data-stu-id="5a1b1-120">Svcutil client</span></span>  
 <span data-ttu-id="5a1b1-121">Ten przykład nie używa programu Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-121">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="5a1b1-122">Umowa jest dostępna w pliku generatedClient.cs, dzięki czemu po przykładzie zademonstrowano niestandardowy import WSDL i generowanie kodu, usługa może być wywoływana.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-122">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="5a1b1-123">Aby użyć następującego niestandardowego importera WSDL na potrzeby tego przykładu, można uruchomić program Svcutil. exe i `/svcutilConfig` określić opcję, podając ścieżkę do pliku konfiguracji klienta użytego w tym przykładzie, który odwołuje `WsdlDocumentation.dll` się do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-123">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="5a1b1-124">Aby załadować `WsdlDocumentationImporter`plik, program Svuctil. exe musi mieć możliwość zlokalizowania i `WsdlDocumentation.dll` załadowania biblioteki, co oznacza, że jest ona zarejestrowana w globalnej pamięci podręcznej zestawów, w ścieżce lub znajduje się w tym samym katalogu, co Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-124">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="5a1b1-125">W przypadku podstawowego przykładu, najłatwiejszym rozwiązaniem jest skopiowanie Svcutil. exe i pliku konfiguracji klienta do tego samego katalogu, co `WsdlDocumentation.dll` spowoduje jego uruchomienie.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-125">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="5a1b1-126">Niestandardowy importer WSDL</span><span class="sxs-lookup"><span data-stu-id="5a1b1-126">The Custom WSDL Importer</span></span>  
 <span data-ttu-id="5a1b1-127">Obiekt <xref:System.ServiceModel.Description.IWsdlImportExtension> <xref:System.ServiceModel.Description.IContractBehavior> <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> niestandardowy zostanie również zaimplementowany <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> i <xref:System.ServiceModel.Description.IOperationBehavior> dodany do zaimportowanych punktów końcowych i i zostanie wywołany w celu zmodyfikowania generowania kodu podczas kontraktu lub operacji `WsdlDocumentationImporter` Trwa tworzenie kodu.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-127">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="5a1b1-128">Po pierwsze, w <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metodzie, przykład określa, czy adnotacja WSDL znajduje się na poziomie kontraktu lub operacji, i dodaje się do niego w odpowiednim zakresie, przekazując zaimportowany tekst adnotacji do jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-128">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
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
  
 <span data-ttu-id="5a1b1-129">Po wygenerowaniu kodu system wywołuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metody i <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> , przekazując odpowiednie informacje kontekstu.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-129">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="5a1b1-130">Przykład formatuje niestandardowe adnotacje WSDL i wstawia je jako komentarze do CodeDom.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-130">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
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
  
## <a name="the-client-application"></a><span data-ttu-id="5a1b1-131">Aplikacja kliencka</span><span class="sxs-lookup"><span data-stu-id="5a1b1-131">The Client Application</span></span>  
 <span data-ttu-id="5a1b1-132">Aplikacja kliencka ładuje niestandardowego importera WSDL przez określenie go w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-132">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
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
  
 <span data-ttu-id="5a1b1-133">Po określeniu importera niestandardowego system metadanych programu WCF ładuje niestandardowego importera do dowolnego <xref:System.ServiceModel.Description.WsdlImporter> utworzonego w tym celu.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-133">Once the custom importer has been specified, the WCF metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="5a1b1-134">Ten przykład korzysta z <xref:System.ServiceModel.Description.MetadataExchangeClient> programu w celu pobrania metadanych <xref:System.ServiceModel.Description.WsdlImporter> , odpowiednio skonfigurowanych do importowania metadanych przy użyciu importera niestandardowego tworzonego przez <xref:System.ServiceModel.Description.ServiceContractGenerator> przykład, a następnie do skompilowania zmodyfikowanych informacji o kontrakcie w obu Visual Basic kod C# klienta, który może być używany w programie Visual Studio do obsługi technologii IntelliSense lub kompilowany do dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-134">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a1b1-135">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="5a1b1-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5a1b1-136">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a1b1-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5a1b1-137">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a1b1-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5a1b1-138">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a1b1-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5a1b1-139">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5a1b1-140">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="5a1b1-140">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5a1b1-141">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a1b1-142">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5a1b1-142">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
