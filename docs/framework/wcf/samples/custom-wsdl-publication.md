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
# <a name="custom-wsdl-publication"></a><span data-ttu-id="a9c56-102">Niestandardowa publikacja WSDL</span><span class="sxs-lookup"><span data-stu-id="a9c56-102">Custom WSDL Publication</span></span>
<span data-ttu-id="a9c56-103">Niniejszy przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="a9c56-103">This sample demonstrates how to:</span></span>  
  
- <span data-ttu-id="a9c56-104">Implementowanie <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> na niestandardowy <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atrybutu, aby wyeksportować właściwości atrybutu jako adnotacje WSDL.</span><span class="sxs-lookup"><span data-stu-id="a9c56-104">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
- <span data-ttu-id="a9c56-105">Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> można zaimportować niestandardowych adnotacje WSDL.</span><span class="sxs-lookup"><span data-stu-id="a9c56-105">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
- <span data-ttu-id="a9c56-106">Implementowanie <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> i <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> na niestandardowy umowę zachowanie i zachowanie niestandardowe operacji, odpowiednio, zapis adnotacji importowany jako komentarze w CodeDom dla importowanych kontraktu i operacji.</span><span class="sxs-lookup"><span data-stu-id="a9c56-106">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
- <span data-ttu-id="a9c56-107">Użyj <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> można pobrać pliku WSDL, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> można zaimportować pliku WSDL, przy użyciu niestandardowych importerów WSDL i <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> do generowania kodu klienta usługi Windows Communication Foundation (WCF) z adnotacjami WSDL jako / / / i ''' komentarzy w języku C# i Visual Podstawowe.</span><span class="sxs-lookup"><span data-stu-id="a9c56-107">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate Windows Communication Foundation (WCF) client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9c56-108">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a9c56-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="a9c56-109">Usługa</span><span class="sxs-lookup"><span data-stu-id="a9c56-109">Service</span></span>  
 <span data-ttu-id="a9c56-110">Usługi w tym przykładzie jest oznaczona za pomocą dwóch atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a9c56-110">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="a9c56-111">Pierwsza strona, `WsdlDocumentationAttribute`akceptuje ciąg w Konstruktorze i mogą być stosowane do interfejsu kontraktu lub operację, podając ciąg, który opisuje jego użycia.</span><span class="sxs-lookup"><span data-stu-id="a9c56-111">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="a9c56-112">Druga Strona, `WsdlParamOrReturnDocumentationAttribute`, mogą być stosowane do zwracania wartości lub parametry do opisania tych wartości w operacji.</span><span class="sxs-lookup"><span data-stu-id="a9c56-112">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="a9c56-113">W poniższym przykładzie pokazano umowę serwisową `ICalculator`, które zostały opisane, przy użyciu tych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a9c56-113">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
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
  
 <span data-ttu-id="a9c56-114">`WsdlDocumentationAttribute` Implementuje <xref:System.ServiceModel.Description.IContractBehavior> i <xref:System.ServiceModel.Description.IOperationBehavior>, więc instancje wieloatrybutowe są dodawane do odpowiednich <xref:System.ServiceModel.Description.ContractDescription> lub <xref:System.ServiceModel.Description.OperationDescription> po otwarciu usługi.</span><span class="sxs-lookup"><span data-stu-id="a9c56-114">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="a9c56-115">Ten atrybut implementuje również <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span><span class="sxs-lookup"><span data-stu-id="a9c56-115">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="a9c56-116">Gdy <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> jest wywoływana, <xref:System.ServiceModel.Description.WsdlExporter> służący do wyeksportowania metadanych i <xref:System.ServiceModel.Description.WsdlContractConversionContext> zawierający opis usługi, które obiekty są przekazywane w jako parametry umożliwiające modyfikowanie metadane wyeksportowane.</span><span class="sxs-lookup"><span data-stu-id="a9c56-116">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="a9c56-117">W tym przykładzie, w zależności od tego, czy obiekt kontekstu eksportu ma <xref:System.ServiceModel.Description.ContractDescription> lub <xref:System.ServiceModel.Description.OperationDescription>, komentarz są wyodrębniane z atrybutu za pomocą właściwości text i zostanie dodany do elementu adnotacji WSDL, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a9c56-117">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="a9c56-118">Jeśli operacja jest eksportowany, próbki używa odbicia, aby uzyskać dowolne `WsdlParamOrReturnDocumentationAttribute` wartości dla parametrów i zwracanych wartości i dodaje je do elementów adnotacji WSDL dla tej operacji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a9c56-118">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
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
  
 <span data-ttu-id="a9c56-119">Przykład następnie publikuje metadane w sposób standardowy, przy użyciu następującego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a9c56-119">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
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
  
## <a name="svcutil-client"></a><span data-ttu-id="a9c56-120">Klient narzędzia svcutil</span><span class="sxs-lookup"><span data-stu-id="a9c56-120">Svcutil client</span></span>  
 <span data-ttu-id="a9c56-121">W tym przykładzie nie używa Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="a9c56-121">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="a9c56-122">Kontrakt jest podana w generatedClient.cs pliku, więc po próbki demonstrujące niestandardowe importu WSDL i generowania kodu, usługa może być wywołana.</span><span class="sxs-lookup"><span data-stu-id="a9c56-122">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="a9c56-123">Aby użyć następujących niestandardowe importera WSDL w tym przykładzie, można uruchomić Svcutil.exe i określ `/svcutilConfig` opcji, podając ścieżkę do pliku konfiguracji klienta, które są używane w tym przykładzie, który odwołuje się `WsdlDocumentation.dll` biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a9c56-123">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="a9c56-124">Aby załadować `WsdlDocumentationImporter`, jednak Svuctil.exe musi być w stanie do lokalizowania i ładowania `WsdlDocumentation.dll` biblioteki, co oznacza, że wartość jest zarejestrowany w globalnej pamięci podręcznej, a w ścieżce, lub znajduje się w tym samym katalogu co Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="a9c56-124">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="a9c56-125">Podstawowy przykład takich, najłatwiejszym jest skopiowanie Svcutil.exe i pliku konfiguracji klienta, w tym samym katalogu co `WsdlDocumentation.dll` i uruchom go z tego miejsca.</span><span class="sxs-lookup"><span data-stu-id="a9c56-125">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="a9c56-126">Importer niestandardowych plików WSDL</span><span class="sxs-lookup"><span data-stu-id="a9c56-126">The Custom WSDL Importer</span></span>  
 <span data-ttu-id="a9c56-127">Niestandardowy <xref:System.ServiceModel.Description.IWsdlImportExtension> obiektu `WsdlDocumentationImporter` implementuje również <xref:System.ServiceModel.Description.IContractBehavior> i <xref:System.ServiceModel.Description.IOperationBehavior> mają zostać dodane do importowanych ServiceEndpoints i <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> i <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> wywoływanej do modyfikowania generowania kodu po umowy lub operacji Trwa tworzenie kodu.</span><span class="sxs-lookup"><span data-stu-id="a9c56-127">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="a9c56-128">Pierwszy w <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metody przykład określa, czy adnotacja WSDL znajduje się na poziomie umowy lub operacji i dodaje się jako zachowanie w zakresie odpowiednie, przekazując tekst adnotacji zaimportowane do jej konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a9c56-128">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
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
  
 <span data-ttu-id="a9c56-129">Następnie, gdy kod jest generowany, system wywołuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> i <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> metod przekazywania informacji odpowiedniego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a9c56-129">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="a9c56-130">Próbka formatów niestandardowych adnotacje WSDL i wstawia je jako komentarze do CodeDom.</span><span class="sxs-lookup"><span data-stu-id="a9c56-130">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
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
  
## <a name="the-client-application"></a><span data-ttu-id="a9c56-131">Aplikacja kliencka</span><span class="sxs-lookup"><span data-stu-id="a9c56-131">The Client Application</span></span>  
 <span data-ttu-id="a9c56-132">Aplikacja kliencka ładuje niestandardowe importerów WSDL, określając je w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9c56-132">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
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
  
 <span data-ttu-id="a9c56-133">Gdy określono niestandardowe importera WCF metadanych załadowanie importera niestandardowych w każdym <xref:System.ServiceModel.Description.WsdlImporter> utworzone w tym celu.</span><span class="sxs-lookup"><span data-stu-id="a9c56-133">Once the custom importer has been specified, the WCF metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="a9c56-134">W tym przykładzie użyto <xref:System.ServiceModel.Description.MetadataExchangeClient> można pobrać metadanych, <xref:System.ServiceModel.Description.WsdlImporter> prawidłowo skonfigurowane, aby zaimportować metadane za pomocą niestandardowych importera Przykładowa aplikacja tworzy, a <xref:System.ServiceModel.Description.ServiceContractGenerator> skompilować informacje na temat modyfikacji umowy na obu Visual Basic i C# kod klienta, który mogą być używane w programie Visual Studio do obsługi technologii Intellisense lub skompilowane do dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="a9c56-134">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a9c56-135">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="a9c56-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a9c56-136">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9c56-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a9c56-137">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9c56-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a9c56-138">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9c56-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9c56-139">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a9c56-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a9c56-140">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a9c56-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a9c56-141">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="a9c56-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9c56-142">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a9c56-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
