---
title: Konfiguracja i obsługa metadanych
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 74dab4528ae11b60fc930a826962b71595073a7f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587725"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="f1339-102">Konfiguracja i obsługa metadanych</span><span class="sxs-lookup"><span data-stu-id="f1339-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="f1339-103">W tym temacie opisano sposób włączania obsługi konfiguracji i metadanych dla powiązania i elementy powiązań.</span><span class="sxs-lookup"><span data-stu-id="f1339-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="f1339-104">Omówienie konfiguracji i metadanych</span><span class="sxs-lookup"><span data-stu-id="f1339-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="f1339-105">W tym temacie omówiono czynności, które są elementy opcjonalne, 1, 2 i 4 w [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md) listy zadań.</span><span class="sxs-lookup"><span data-stu-id="f1339-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="f1339-106">Włączanie obsługę element powiązania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1339-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="f1339-107">Włączanie obsługi plików konfiguracji dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1339-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="f1339-108">Eksportowanie WSDL i zasady potwierdzenia dla elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1339-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="f1339-109">Identyfikowanie potwierdzenia WSDL i zasady, aby wstawić i skonfiguruj powiązania lub element powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1339-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="f1339-110">Aby uzyskać informacji na temat tworzenia powiązań zdefiniowanych przez użytkownika i elementy powiązań, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) i [Tworzenie elementu BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f1339-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) and [Creating a BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="f1339-111">Dodanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f1339-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="f1339-112">Aby włączyć obsługę pliku konfiguracji dla kanału, musi implementować dwie sekcje konfiguracji <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, umożliwiająca obsługę konfiguracji dla elementów, wiązania i <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> i <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, umożliwiają one obsługę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1339-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="f1339-113">Łatwiejszy sposób, w tym celu jest użycie [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) przykładowe narzędzie do generowania kodu konfiguracji dla powiązania i elementy powiązań.</span><span class="sxs-lookup"><span data-stu-id="f1339-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="f1339-114">Rozszerzanie BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="f1339-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="f1339-115">Poniższy przykład kodu jest pobierana z [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="f1339-115">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="f1339-116">`UdpTransportElement` Jest <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> który uwidacznia `UdpTransportBindingElement` systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1339-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="f1339-117">Za pomocą kilku podstawowych zastąpień przykład definiuje nazwa sekcji konfiguracji, typem elementu powiązania i jak można utworzyć elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1339-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="f1339-118">Użytkownicy mogą następnie rejestrować w sekcji rozszerzeń w pliku konfiguracji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f1339-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f1339-119">Rozszerzenia mogą być przywoływane z powiązań niestandardowych, aby używać protokołu UDP transportu.</span><span class="sxs-lookup"><span data-stu-id="f1339-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="f1339-120">Dodawanie konfiguracji dla powiązania</span><span class="sxs-lookup"><span data-stu-id="f1339-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="f1339-121">Sekcja `SampleProfileUdpBindingCollectionElement` jest <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> który uwidacznia `SampleProfileUdpBinding` systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1339-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="f1339-122">Duża część wykonania jest delegowane do `SampleProfileUdpBindingConfigurationElement`, która jest pochodną <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f1339-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="f1339-123">`SampleProfileUdpBindingConfigurationElement` Ma właściwości, które odnoszą się do właściwości `SampleProfileUdpBinding`i funkcji do mapowania z `ConfigurationElement` powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1339-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="f1339-124">Na koniec `OnApplyConfiguration` metoda zostanie przesłonięta w `SampleProfileUdpBinding`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f1339-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp 
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="f1339-125">Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, dodaj następującą sekcję do pliku konfiguracyjnego istotne.</span><span class="sxs-lookup"><span data-stu-id="f1339-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="f1339-126">Następnie mogą być przywoływane z [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1339-126">It can then be referenced from the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="f1339-127">Dodanie obsługi metadanych elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="f1339-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="f1339-128">Aby zintegrować kanał w systemie metadanych, musi obsługiwać importu i eksportu zasad.</span><span class="sxs-lookup"><span data-stu-id="f1339-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="f1339-129">Dzięki temu narzędzi takich jak [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klientów elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1339-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="f1339-130">Dodawanie pomocy technicznej WSDL</span><span class="sxs-lookup"><span data-stu-id="f1339-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="f1339-131">Element powiązania transportu powiązanie jest odpowiedzialny za eksportowanie i importowanie informacji o adresach w metadanych.</span><span class="sxs-lookup"><span data-stu-id="f1339-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="f1339-132">Korzystając z powiązania protokołu SOAP, element powiązania transportu powinien również wyeksportować poprawne transportu identyfikatora URI w metadanych.</span><span class="sxs-lookup"><span data-stu-id="f1339-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="f1339-133">Poniższy przykład kodu jest pobierana z [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="f1339-133">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="f1339-134">WSDL Export</span><span class="sxs-lookup"><span data-stu-id="f1339-134">WSDL Export</span></span>  
 <span data-ttu-id="f1339-135">Aby wyeksportować informacje dotyczące adresowania, `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f1339-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="f1339-136"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda dodaje poprawnych informacji adresowania do portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="f1339-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="f1339-137">`UdpTransportBindingElement` Implementacji <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metoda również eksportuje transportu identyfikatora URI, gdy punkt końcowy korzysta z powiązania protokołu SOAP:</span><span class="sxs-lookup"><span data-stu-id="f1339-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="f1339-138">WSDL Import</span><span class="sxs-lookup"><span data-stu-id="f1339-138">WSDL Import</span></span>  
 <span data-ttu-id="f1339-139">Aby rozszerzyć system importu WSDL do obsługi importowanie adresów, dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="f1339-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f1339-140">Podczas uruchamiania Svcutil.exe, istnieją dwie opcje w celu uzyskania Svcutil.exe można załadować rozszerzenia importu WSDL:</span><span class="sxs-lookup"><span data-stu-id="f1339-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="f1339-141">Punkt Svcutil.exe do pliku konfiguracji, za pomocą /SvcutilConfig:\<pliku >.</span><span class="sxs-lookup"><span data-stu-id="f1339-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="f1339-142">Dodaj sekcję konfiguracji do Svcutil.exe.config, w tym samym katalogu co Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="f1339-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="f1339-143">`UdpBindingElementImporter` Typ implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f1339-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="f1339-144">`ImportEndpoint` Metoda importuje adres z portu WSDL:</span><span class="sxs-lookup"><span data-stu-id="f1339-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="f1339-145">Dodanie obsługi zasad</span><span class="sxs-lookup"><span data-stu-id="f1339-145">Adding Policy Support</span></span>  
 <span data-ttu-id="f1339-146">Element niestandardowego powiązania, można wyeksportować asercji zasad Powiązanie WSDL dla punktu końcowego usługi do wyrażenia możliwości tego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1339-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="f1339-147">Poniższy przykład kodu jest pobierana z [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="f1339-147">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="f1339-148">Eksportowanie zasad</span><span class="sxs-lookup"><span data-stu-id="f1339-148">Policy Export</span></span>  
 <span data-ttu-id="f1339-149">`UdpTransportBindingElement` Typ implementuje <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> się Dodaj pomoc techniczna dotycząca eksportowania zasad.</span><span class="sxs-lookup"><span data-stu-id="f1339-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="f1339-150">W rezultacie <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> obejmuje `UdpTransportBindingElement` podczas generowania zasady dla powiązania zawierający go.</span><span class="sxs-lookup"><span data-stu-id="f1339-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="f1339-151">W <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, Dodaj potwierdzenie dla protokołów UDP i innym potwierdzenie, jeśli kanał jest w trybie multiemisji.</span><span class="sxs-lookup"><span data-stu-id="f1339-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="f1339-152">Jest to spowodowane ma wpływ tryb multiemisji jak stos komunikacji jest tworzony i dlatego musi być koordynowane między obie strony.</span><span class="sxs-lookup"><span data-stu-id="f1339-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="f1339-153">Ponieważ elementy powiązania transportu niestandardowego jest odpowiedzialny za obsługę adresowania, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementacji na `UdpTransportBindingElement` muszą również obsługiwać eksportowania odpowiednie WS-Addressing asercji zasad do wskazania wersji WS-Addressing jest używane.</span><span class="sxs-lookup"><span data-stu-id="f1339-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="f1339-154">Importuj zasady</span><span class="sxs-lookup"><span data-stu-id="f1339-154">Policy Import</span></span>  
 <span data-ttu-id="f1339-155">Aby rozszerzyć system importu zasad, dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="f1339-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f1339-156">Następnie wdrożymy <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z naszych zarejestrowanych klasy (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="f1339-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="f1339-157">W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, sprawdź potwierdzenia w odpowiedniej przestrzeni nazw i przetworzyć te generowania transportu i sprawdzanie, czy jest multiemisji.</span><span class="sxs-lookup"><span data-stu-id="f1339-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="f1339-158">Ponadto należy usunąć potwierdzenia, które obsługuje importera z listy powiązania potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="f1339-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="f1339-159">Ponownie uruchamiając Svcutil.exe, dostępne są dwie opcje integracji:</span><span class="sxs-lookup"><span data-stu-id="f1339-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="f1339-160">Punkt Svcutil.exe do naszego pliku konfiguracji, za pomocą /SvcutilConfig:\<pliku >.</span><span class="sxs-lookup"><span data-stu-id="f1339-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="f1339-161">Dodaj sekcję konfiguracji do Svcutil.exe.config, w tym samym katalogu co Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="f1339-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="f1339-162">Dodawanie niestandardowych standardowego powiązanie importera</span><span class="sxs-lookup"><span data-stu-id="f1339-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="f1339-163">Svcutil.exe i <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typu, domyślnie, rozpoznaje i importować powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="f1339-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="f1339-164">W przeciwnym razie powiązanie pobiera importowane jako <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f1339-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="f1339-165">Aby włączyć Svcutil.exe i <xref:System.ServiceModel.Description.WsdlImporter> do zaimportowania `SampleProfileUdpBinding` `UdpBindingElementImporter` działa również jako importera niestandardowego powiązania standardowych.</span><span class="sxs-lookup"><span data-stu-id="f1339-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="f1339-166">Implementuje importera niestandardowego powiązania standardowa `ImportEndpoint` metody <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejsu do sprawdzenia <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienia zaimportowane z metadanych, aby zobaczyć, jeśli może ona zostać wygenerowane przez określone powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="f1339-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```csharp  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f1339-167">Ogólnie rzecz biorąc Implementowanie importera niestandardowego powiązania standardowa polega na sprawdzeniu właściwości elementów wiązania zaimportowanych, aby sprawdzić, czy tylko właściwości, które można ustawić przez powiązanie standardowe zostały zmienione, a wszystkie pozostałe właściwości są ich wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="f1339-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="f1339-168">Podstawowe strategii wykonywania importera Powiązanie standardowe jest utworzenie wystąpienia standard powiązania Propagacja powiązania właściwości z elementy powiązania wystąpienie Powiązanie standardowe, które obsługuje standardowe powiązania w celu porównania elementy wiązania standardowa elementami importowanych powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1339-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
