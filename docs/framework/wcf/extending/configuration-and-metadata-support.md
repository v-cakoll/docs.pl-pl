---
title: Konfiguracja i obsługa metadanych
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 0ec8c3286037e7adbe6f5efb73e846a30b9d48d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185664"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="8c7bf-102">Konfiguracja i obsługa metadanych</span><span class="sxs-lookup"><span data-stu-id="8c7bf-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="8c7bf-103">W tym temacie opisano sposób włączania obsługi konfiguracji i metadanych dla powiązań i elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="8c7bf-104">Omówienie konfiguracji i metadanych</span><span class="sxs-lookup"><span data-stu-id="8c7bf-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="8c7bf-105">W tym temacie omówiono następujące zadania, które są opcjonalnymi elementami 1, 2 i 4 na liście zadań [Kanały programowe.](developing-channels.md)</span><span class="sxs-lookup"><span data-stu-id="8c7bf-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="8c7bf-106">Włączanie obsługi pliku konfiguracji dla elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="8c7bf-107">Włączanie obsługi plików konfiguracji dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="8c7bf-108">Eksportowanie WSDL i potwierdzeń zasad dla elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="8c7bf-109">Identyfikowanie WSDL i potwierdzeń zasad, aby wstawić i skonfigurować element wiązania lub powiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="8c7bf-110">Aby uzyskać informacje dotyczące tworzenia powiązań zdefiniowanych przez użytkownika i elementów wiązania, zobacz [Tworzenie powiązań zdefiniowanych przez użytkownika](creating-user-defined-bindings.md) i tworzenie [bindingelement](creating-a-bindingelement.md), odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="8c7bf-111">Dodawanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8c7bf-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="8c7bf-112">Aby włączyć obsługę plików konfiguracji dla kanału, należy <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>zaimplementować dwie sekcje <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> konfiguracji, który umożliwia obsługę konfiguracji dla elementów wiązania i i <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, które umożliwiają obsługę konfiguracji dla powiązań.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="8c7bf-113">Łatwiejszym sposobem jest użycie przykładowego narzędzia [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) do generowania kodu konfiguracji dla powiązań i elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="8c7bf-114">Rozszerzanie bindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="8c7bf-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="8c7bf-115">Poniższy przykładowy kod jest pobierany z transport: przykład [UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="8c7bf-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="8c7bf-116">Jest `UdpTransportElement` <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> to, który `UdpTransportBindingElement` udostępnia do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="8c7bf-117">Z kilku podstawowych zastąpienia, przykład definiuje nazwę sekcji konfiguracji, typ elementu wiązania i jak utworzyć element wiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="8c7bf-118">Użytkownicy mogą następnie zarejestrować sekcję rozszerzenia w pliku konfiguracyjnym w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="8c7bf-119">Rozszerzenie można odwoływać się od niestandardowych powiązań do korzystania z protokołu UDP jako transportu.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="8c7bf-120">Dodawanie konfiguracji dla powiązania</span><span class="sxs-lookup"><span data-stu-id="8c7bf-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="8c7bf-121">Sekcja `SampleProfileUdpBindingCollectionElement` <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> jest, która `SampleProfileUdpBinding` udostępnia do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="8c7bf-122">Większość implementacji jest delegowana `SampleProfileUdpBindingConfigurationElement`do , który <xref:System.ServiceModel.Configuration.StandardBindingElement>pochodzi z .</span><span class="sxs-lookup"><span data-stu-id="8c7bf-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="8c7bf-123">Ma `SampleProfileUdpBindingConfigurationElement` właściwości, które odpowiadają właściwości `SampleProfileUdpBinding`na , i funkcje do mapowania z `ConfigurationElement` powiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="8c7bf-124">Na koniec `OnApplyConfiguration` metoda jest zastępowana `SampleProfileUdpBinding`w , jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                var expectedType = typeof(SampleProfileUdpBinding).AssemblyQualifiedName;
                var typePassedIn = binding.GetType().AssemblyQualifiedName;
                throw new ArgumentException($"Invalid type for binding. Expected type: {expectedType}. Type passed in: {typePassedIn}.");  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="8c7bf-125">Aby zarejestrować ten program obsługi w systemie konfiguracji, dodaj następującą sekcję do odpowiedniego pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="8c7bf-126">Następnie można się do niego odwoływać z [ \<sekcji system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="8c7bf-127">Dodawanie obsługi metadanych dla elementu wiązania</span><span class="sxs-lookup"><span data-stu-id="8c7bf-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="8c7bf-128">Aby zintegrować kanał z systemem metadanych, musi obsługiwać zarówno importowanie, jak i eksport zasad.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="8c7bf-129">Dzięki temu narzędzia, takie jak [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klientów elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="8c7bf-130">Dodawanie obsługi WSDL</span><span class="sxs-lookup"><span data-stu-id="8c7bf-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="8c7bf-131">Element wiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji adresowych w metadanych.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="8c7bf-132">Podczas korzystania z powiązania SOAP element wiązania transportu należy również wyeksportować poprawny identyfikator URI transportu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="8c7bf-133">Poniższy przykładowy kod jest pobierany z transport: przykład [UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="8c7bf-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="8c7bf-134">Eksport WSDL</span><span class="sxs-lookup"><span data-stu-id="8c7bf-134">WSDL Export</span></span>  
 <span data-ttu-id="8c7bf-135">Aby wyeksportować `UdpTransportBindingElement` informacje <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> adresowe, implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="8c7bf-136">Metoda <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> dodaje poprawne informacje adresowe do portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="8c7bf-137">Implementacja `UdpTransportBindingElement` <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody eksportuje również transportowy identyfikator URI, gdy punkt końcowy używa powiązania SOAP:</span><span class="sxs-lookup"><span data-stu-id="8c7bf-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="8c7bf-138">WSDL Import</span><span class="sxs-lookup"><span data-stu-id="8c7bf-138">WSDL Import</span></span>  
 <span data-ttu-id="8c7bf-139">Aby rozszerzyć system importowania WSDL na obsługę importowania adresów, dodaj następującą konfigurację do pliku konfiguracyjnego programu Svcutil.exe, jak pokazano w pliku Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="8c7bf-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="8c7bf-140">Podczas uruchamiania programu Svcutil.exe dostępne są dwie opcje ładowania rozszerzenia importu WSDL przez program Svcutil.exe:</span><span class="sxs-lookup"><span data-stu-id="8c7bf-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="8c7bf-141">Punkt Svcutil.exe do pliku konfiguracyjnego przy użyciu\<pliku /SvcutilConfig:>.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="8c7bf-142">Dodaj sekcję konfiguracji do pliku Svcutil.exe.config w tym samym katalogu co program Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="8c7bf-143">Typ `UdpBindingElementImporter` implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejs.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="8c7bf-144">Metoda `ImportEndpoint` importuje adres z portu WSDL:</span><span class="sxs-lookup"><span data-stu-id="8c7bf-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="8c7bf-145">Dodawanie obsługi zasad</span><span class="sxs-lookup"><span data-stu-id="8c7bf-145">Adding Policy Support</span></span>  
 <span data-ttu-id="8c7bf-146">Element wiązania niestandardowego można eksportować potwierdzeń zasad w powiązanie WSDL dla punktu końcowego usługi do wyrażania możliwości tego elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="8c7bf-147">Poniższy przykładowy kod jest pobierany z transport: przykład [UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="8c7bf-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="8c7bf-148">Eksport zasad</span><span class="sxs-lookup"><span data-stu-id="8c7bf-148">Policy Export</span></span>  
 <span data-ttu-id="8c7bf-149">Typ `UdpTransportBindingElement` implementuje, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> aby dodać obsługę zasad eksportowania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="8c7bf-150">W rezultacie <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> obejmuje `UdpTransportBindingElement` w generowaniu zasad dla dowolnego powiązania, które go zawiera.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="8c7bf-151">W <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, dodaj asercja dla UDP i innego potwierdzenia, jeśli kanał jest w trybie multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="8c7bf-152">Jest tak, ponieważ tryb multiemisji wpływa na sposób konstruowania stosu komunikacji, a zatem musi być skoordynowane między obiema stronami.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="8c7bf-153">Ponieważ niestandardowe elementy wiązania transportu są <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> odpowiedzialne za `UdpTransportBindingElement` obsługę adresowania, implementacja na musi również obsługiwać eksportowanie odpowiednich potwierdzeń zasad adresowania WS, aby wskazać wersję używanego adresowania WS.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="8c7bf-154">Import zasad</span><span class="sxs-lookup"><span data-stu-id="8c7bf-154">Policy Import</span></span>  
 <span data-ttu-id="8c7bf-155">Aby rozszerzyć system importu zasad, dodaj następującą konfigurację do pliku konfiguracyjnego programu Svcutil.exe, jak pokazano w pliku Svcutil.exe.config:</span><span class="sxs-lookup"><span data-stu-id="8c7bf-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="8c7bf-156">Następnie wdrażamy <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z naszej`UdpBindingElementImporter`zarejestrowanej klasy ( ).</span><span class="sxs-lookup"><span data-stu-id="8c7bf-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="8c7bf-157">W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, zbadać potwierdzenia w odpowiednim obszarze nazw i przetwarzać te do generowania transportu i sprawdzanie, czy jest multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="8c7bf-158">Ponadto należy usunąć twierdzenia, które importer obsługuje z listy potwierdzeń wiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="8c7bf-159">Ponownie, podczas uruchamiania programu Svcutil.exe dostępne są dwie opcje integracji:</span><span class="sxs-lookup"><span data-stu-id="8c7bf-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="8c7bf-160">Punkt Svcutil.exe do naszego pliku konfiguracyjnego za\<pomocą pliku /SvcutilConfig:>.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="8c7bf-161">Dodaj sekcję konfiguracji do pliku Svcutil.exe.config w tym samym katalogu co program Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="8c7bf-162">Dodawanie niestandardowego importera wiązania standardowego</span><span class="sxs-lookup"><span data-stu-id="8c7bf-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="8c7bf-163">Program Svcutil.exe <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> i typ domyślnie rozpoznają i zaimportują powiązania dostarczone przez system.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="8c7bf-164">W przeciwnym razie powiązanie <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> zostanie zaimportowane jako wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="8c7bf-165">Aby włączyć Svcutil.exe <xref:System.ServiceModel.Description.WsdlImporter> i `SampleProfileUdpBinding` importować `UdpBindingElementImporter` również działa jako importer wiązania standard niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="8c7bf-166">Importer wiązania niestandardowego standard `ImportEndpoint` implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> metodę w <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> interfejsie, aby sprawdzić wystąpienie importowane z metadanych, aby sprawdzić, czy mogło zostać wygenerowane przez określone powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="8c7bf-167">Ogólnie rzecz biorąc implementowanie importera wiązania niestandardowego standard polega na sprawdzeniu właściwości importowanych elementów wiązania, aby sprawdzić, czy tylko właściwości, które mogły zostać ustawione przez standardowe powiązanie zostały zmienione i wszystkie inne właściwości są ich wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="8c7bf-168">Podstawową strategią wdrażania standardowego importera wiązania jest utworzenie wystąpienia standardowego powiązania, propagowanie właściwości z elementów wiązania do standardowego wystąpienia wiązania, które obsługuje standardowe powiązanie, oraz porównywanie powiązania elementy ze standardowego powiązania z importowanymi elementami wiązania.</span><span class="sxs-lookup"><span data-stu-id="8c7bf-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
