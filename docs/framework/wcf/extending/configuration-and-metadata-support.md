---
title: Konfiguracja i obsługa metadanych
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 16c386f8479778c7d2f17fbdfdb95dee558baf52
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795839"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="d2f9c-102">Konfiguracja i obsługa metadanych</span><span class="sxs-lookup"><span data-stu-id="d2f9c-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="d2f9c-103">W tym temacie opisano sposób włączania obsługi konfiguracji i metadanych dla powiązań i elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="d2f9c-104">Przegląd konfiguracji i metadanych</span><span class="sxs-lookup"><span data-stu-id="d2f9c-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="d2f9c-105">W tym temacie omówiono następujące zadania, które są elementami opcjonalnymi 1, 2 i 4 na liście zadań [Tworzenie kanałów](developing-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="d2f9c-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="d2f9c-106">Włączanie obsługi pliku konfiguracji dla elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="d2f9c-107">Włączanie obsługi plików konfiguracyjnych dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="d2f9c-108">Eksportowanie potwierdzeń WSDL i zasad dla elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="d2f9c-109">Identyfikowanie potwierdzeń WSDL i zasad w celu wstawienia i skonfigurowania elementu powiązania lub powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="d2f9c-110">Aby uzyskać informacje na temat tworzenia powiązań zdefiniowanych przez użytkownika i elementów powiązania, zobacz temat [Tworzenie powiązań zdefiniowanych przez użytkownika](creating-user-defined-bindings.md) i [Tworzenie BindingElement](creating-a-bindingelement.md)odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="d2f9c-111">Dodawanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d2f9c-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="d2f9c-112">Aby włączyć obsługę plików konfiguracyjnych dla kanału, należy zaimplementować dwie sekcje <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>konfiguracji, umożliwiające obsługę konfiguracji elementów powiązania <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> oraz i <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, które umożliwiają obsługę konfiguracji dla powiązań.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="d2f9c-113">Łatwiejszym sposobem jest użycie narzędzia przykładowej [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) do wygenerowania kodu konfiguracji powiązań i elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="d2f9c-114">Rozszerzanie BindingElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="d2f9c-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="d2f9c-115">Następujący przykładowy kod jest pobierany z [transportu: Przykład](../samples/transport-udp.md) protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="d2f9c-116">Jest to, który uwidacznia `UdpTransportBindingElement` system konfiguracji. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> `UdpTransportElement`</span><span class="sxs-lookup"><span data-stu-id="d2f9c-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="d2f9c-117">Za pomocą kilku podstawowych zastąpień, przykład definiuje nazwę sekcji konfiguracji, typ elementu powiązania i sposób tworzenia elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="d2f9c-118">Następnie użytkownicy mogą zarejestrować sekcję rozszerzenia w pliku konfiguracji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="d2f9c-119">Do rozszerzenia można odwoływać się z niestandardowych powiązań, aby użyć protokołu UDP jako transportu.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="d2f9c-120">Dodawanie konfiguracji dla powiązania</span><span class="sxs-lookup"><span data-stu-id="d2f9c-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="d2f9c-121">Sekcja `SampleProfileUdpBindingCollectionElement` jest<xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> udostępniana`SampleProfileUdpBinding` systemowi konfiguracyjnemu.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="d2f9c-122">Zbiorcza implementacja jest delegowana do `SampleProfileUdpBindingConfigurationElement`elementu, który pochodzi od. <xref:System.ServiceModel.Configuration.StandardBindingElement></span><span class="sxs-lookup"><span data-stu-id="d2f9c-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="d2f9c-123">Zawiera właściwości, które odpowiadają właściwościom w `SampleProfileUdpBinding`, i `ConfigurationElement` funkcji, które mają być mapowane na podstawie powiązania. `SampleProfileUdpBindingConfigurationElement`</span><span class="sxs-lookup"><span data-stu-id="d2f9c-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="d2f9c-124">Na `OnApplyConfiguration` koniec Metoda zostanie zastąpiona `SampleProfileUdpBinding`w, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="d2f9c-125">Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, należy dodać następującą sekcję do odpowiedniego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="d2f9c-126">Można go następnie przywoływać z [ \<sekcji konfiguracji > System. ServiceModel](../../configure-apps/file-schema/wcf/system-servicemodel.md) .</span><span class="sxs-lookup"><span data-stu-id="d2f9c-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="d2f9c-127">Dodawanie obsługi metadanych dla elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="d2f9c-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="d2f9c-128">Aby zintegrować kanał z systemem metadanych, musi on obsługiwać Importowanie i eksportowanie zasad.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="d2f9c-129">Umożliwia to narzędziom, takim jak [Narzędzie do metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , generowanie klientów elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="d2f9c-130">Dodawanie obsługi WSDL</span><span class="sxs-lookup"><span data-stu-id="d2f9c-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="d2f9c-131">Element powiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji dotyczących adresowania w metadanych.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="d2f9c-132">W przypadku korzystania z powiązania SOAP element powiązania transportu powinien również eksportować prawidłowy identyfikator URI transportu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="d2f9c-133">Następujący przykładowy kod jest pobierany z [transportu: Przykład](../samples/transport-udp.md) protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="d2f9c-134">Eksport WSDL</span><span class="sxs-lookup"><span data-stu-id="d2f9c-134">WSDL Export</span></span>  
 <span data-ttu-id="d2f9c-135">Aby wyeksportować informacje dotyczące adresowania `UdpTransportBindingElement` , <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d2f9c-136"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda dodaje do portu WSDL prawidłowe informacje dotyczące adresowania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="d2f9c-137">`UdpTransportBindingElement` Implementacja<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> metody także eksportuje identyfikator URI transportu, gdy punkt końcowy używa powiązania SOAP:</span><span class="sxs-lookup"><span data-stu-id="d2f9c-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="d2f9c-138">Import WSDL</span><span class="sxs-lookup"><span data-stu-id="d2f9c-138">WSDL Import</span></span>  
 <span data-ttu-id="d2f9c-139">Aby zwiększyć system importowania WSDL do obsługi importowania adresów, Dodaj następującą konfigurację do pliku konfiguracji programu Svcutil. exe, jak pokazano w pliku Svcutil. exe. config:</span><span class="sxs-lookup"><span data-stu-id="d2f9c-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="d2f9c-140">Podczas uruchamiania programu Svcutil. exe dostępne są dwie opcje pobrania pliku Svcutil. exe w celu załadowania rozszerzeń WSDL:</span><span class="sxs-lookup"><span data-stu-id="d2f9c-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="d2f9c-141">Wskaż plik konfiguracyjny Svcutil. exe przy użyciu pliku/svcutilConfig:\<>.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="d2f9c-142">Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="d2f9c-143">`UdpBindingElementImporter` Typ<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d2f9c-144">`ImportEndpoint` Metoda importuje adres z portu WSDL:</span><span class="sxs-lookup"><span data-stu-id="d2f9c-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="d2f9c-145">Dodawanie obsługi zasad</span><span class="sxs-lookup"><span data-stu-id="d2f9c-145">Adding Policy Support</span></span>  
 <span data-ttu-id="d2f9c-146">Niestandardowy element powiązania może eksportować potwierdzenia zasad w powiązaniu WSDL dla punktu końcowego usługi, aby przedstawić możliwości tego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="d2f9c-147">Następujący przykładowy kod jest pobierany z [transportu: Przykład](../samples/transport-udp.md) protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="d2f9c-148">Eksport zasad</span><span class="sxs-lookup"><span data-stu-id="d2f9c-148">Policy Export</span></span>  
 <span data-ttu-id="d2f9c-149">Typ `UdpTransportBindingElement` implementuje<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> , aby dodać obsługę eksportowania zasad.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="d2f9c-150">W efekcie <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> obejmuje `UdpTransportBindingElement` generowanie zasad dla dowolnego powiązania, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="d2f9c-151">W <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>programie Dodaj potwierdzenie protokołu UDP i inne potwierdzenie, jeśli kanał jest w trybie multiemisji.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="d2f9c-152">Jest to spowodowane tym, że tryb multiemisji wpływa na sposób konstruowania stosu komunikacji i w związku z tym musi być koordynowany między stronami.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="d2f9c-153">Ponieważ niestandardowe elementy powiązania transportu są odpowiedzialne za obsługę adresowania <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> , implementacja `UdpTransportBindingElement` na serwerze musi również obsługiwać eksportowanie odpowiednich potwierdzeń zasad WS-Addressing w celu wskazania wersji WS-Addressing jest używany.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="d2f9c-154">Importowanie zasad</span><span class="sxs-lookup"><span data-stu-id="d2f9c-154">Policy Import</span></span>  
 <span data-ttu-id="d2f9c-155">Aby zwiększyć system importowania zasad, należy dodać następującą konfigurację do pliku konfiguracji programu Svcutil. exe, jak pokazano w pliku Svcutil. exe. config:</span><span class="sxs-lookup"><span data-stu-id="d2f9c-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="d2f9c-156">Następnie implementujemy <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> nasze zarejestrowanej klasy`UdpBindingElementImporter`().</span><span class="sxs-lookup"><span data-stu-id="d2f9c-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="d2f9c-157"><xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>Sprawdź potwierdzenia w odpowiedniej przestrzeni nazw i przetwórz je w celu wygenerowania transportu i sprawdzenia, czy jest to multiemisja.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="d2f9c-158">Ponadto Usuń potwierdzenia obsługiwane przez importera z listy potwierdzeń powiązań.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="d2f9c-159">Po uruchomieniu programu Svcutil. exe dostępne są dwie opcje integracji:</span><span class="sxs-lookup"><span data-stu-id="d2f9c-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="d2f9c-160">Wskaż plik konfiguracyjny Svcutil. exe przy użyciu pliku/svcutilConfig:\<>.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="d2f9c-161">Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="d2f9c-162">Dodawanie niestandardowego importera powiązań standardowych</span><span class="sxs-lookup"><span data-stu-id="d2f9c-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="d2f9c-163">Svcutil. exe i <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typ, domyślnie, rozpoznawanie i importowanie powiązań dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="d2f9c-164">W przeciwnym razie powiązanie zostanie zaimportowane jako <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="d2f9c-165">Aby umożliwić programowi Svcutil. exe <xref:System.ServiceModel.Description.WsdlImporter> i `SampleProfileUdpBinding` zaimportować `UdpBindingElementImporter` go również jako niestandardowego importera powiązań standardowych.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="d2f9c-166">Niestandardowy importer powiązań standardowych implementuje `ImportEndpoint` metodę <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> w interfejsie, aby sprawdzić <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienie zaimportowane z metadanych, aby sprawdzić, czy mogło zostać wygenerowane przez określone powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="d2f9c-167">Ogólnie rzecz biorąc, implementacja niestandardowego importera powiązań standardowych polega na sprawdzeniu właściwości zaimportowanych elementów powiązania, aby sprawdzić, czy zmieniono tylko właściwości, które mogły zostać ustawione przez powiązanie standardowe, a wszystkie inne właściwości są ich domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="d2f9c-168">Podstawową strategią wdrażania importera powiązań standardowych jest utworzenie wystąpienia standardowego powiązania, propagowanie właściwości z elementów powiązania do standardowego wystąpienia powiązania, które obsługuje powiązanie standardowe, oraz porównanie powiązania elementy ze standardowego powiązania z zaimportowanymi elementami powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2f9c-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
