---
title: '&lt;serviceMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4e88c6e5f03cef83e640fbca7434d10f82653f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicemetadatagt"></a><span data-ttu-id="99ac8-102">&lt;serviceMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="99ac8-102">&lt;serviceMetadata&gt;</span></span>
<span data-ttu-id="99ac8-103">Określa publikację usługi metadanych i skojarzonych informacji.</span><span class="sxs-lookup"><span data-stu-id="99ac8-103">Specifies the publication of service metadata and associated information.</span></span>  
  
<span data-ttu-id="99ac8-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="99ac8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="99ac8-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="99ac8-105">\<behaviors></span></span>  
<span data-ttu-id="99ac8-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="99ac8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="99ac8-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="99ac8-107">\<behavior></span></span>  
<span data-ttu-id="99ac8-108">\<serviceMetadata ></span><span class="sxs-lookup"><span data-stu-id="99ac8-108">\<serviceMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99ac8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="99ac8-109">Syntax</span></span>  
  
```xml
<serviceMetadata externalMetadataLocation="String"  
                 httpGetBinding="String" 
                 httpGetBindingConfiguration="String"  
                 httpGetEnabled="Boolean" 
                 httpGetUrl="String" 
                 httpsGetBinding="String" 
                 httpsGetBindingConfiguration="String"  
                 httpsGetEnabled="Boolean"   
                 httpsGetUrl="String"  
                 policyVersion="Policy12/Policy15" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99ac8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="99ac8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="99ac8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="99ac8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99ac8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="99ac8-112">Attributes</span></span>  
  
|<span data-ttu-id="99ac8-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="99ac8-113">Attribute</span></span>|<span data-ttu-id="99ac8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="99ac8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99ac8-115">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="99ac8-115">externalMetadataLocation</span></span>|<span data-ttu-id="99ac8-116">Identyfikator Uri zawiera lokalizację pliku WSDL, który jest zwracany do użytkownika w odpowiedzi na żądania WSDL oraz MEX zamiast automatycznie generowanego WSDL.</span><span class="sxs-lookup"><span data-stu-id="99ac8-116">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="99ac8-117">Ten atrybut nie jest ustawiona, wartość domyślna WSDL jest zwracany w trakcie.</span><span class="sxs-lookup"><span data-stu-id="99ac8-117">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="99ac8-118">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="99ac8-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="99ac8-119">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="99ac8-119">httpGetBinding</span></span>|<span data-ttu-id="99ac8-120">Ciąg określający typ powiązania, który będzie używany do pobierania metadanych za pośrednictwem HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="99ac8-120">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="99ac8-121">To ustawienie jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="99ac8-121">This setting is optional.</span></span> <span data-ttu-id="99ac8-122">Jeśli nie zostanie określony, będą używane domyślne powiązania.</span><span class="sxs-lookup"><span data-stu-id="99ac8-122">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="99ac8-123">Tylko powiązania z elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="99ac8-123">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="99ac8-124">Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwość powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="99ac8-124">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="99ac8-125">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="99ac8-125">httpGetBindingConfiguration</span></span>|<span data-ttu-id="99ac8-126">Ciąg ustawiający nazwę powiązania, które jest określone w `httpGetBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="99ac8-126">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="99ac8-127">Taką samą nazwę, muszą być zdefiniowane w `<bindings>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="99ac8-127">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="99ac8-128">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="99ac8-128">httpGetEnabled</span></span>|<span data-ttu-id="99ac8-129">Wartość logiczna określająca, czy publikować metadane usługi dla pobierania za pomocą żądania HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="99ac8-129">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="99ac8-130">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="99ac8-130">The default is `false`.</span></span><br /><br /> <span data-ttu-id="99ac8-131">Jeśli nie określono atrybut httpGetUrl, adres, w którym publikowane są metadane jest adres usługi oraz "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="99ac8-131">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="99ac8-132">Na przykład jeśli adres usługi "adresem http://localhost: 8080/CalculatorService", adres metadanych HTTP/Get jest "adresem http://localhost: 8080/CalculatorService? wsdl".</span><span class="sxs-lookup"><span data-stu-id="99ac8-132">For example, if the service address is "http://localhost:8080/CalculatorService", the HTTP/Get metadata address is "http://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="99ac8-133">Jeśli ta właściwość jest `false`, lub adres usługi nie jest oparty na HTTP lub HTTPS, "? wsdl" zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="99ac8-133">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="99ac8-134">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="99ac8-134">httpGetUrl</span></span>|<span data-ttu-id="99ac8-135">Identyfikator Uri, który określa adres, w którym publikowane są metadane dla pobierania za pomocą żądania HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="99ac8-135">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="99ac8-136">Jeśli względny identyfikator Uri jest określony, będzie traktowane jako względem adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="99ac8-136">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="99ac8-137">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="99ac8-137">httpsGetBinding</span></span>|<span data-ttu-id="99ac8-138">Ciąg określający typ powiązania, które będą używane do pobierania metadanych za pośrednictwem HTTPS GET.</span><span class="sxs-lookup"><span data-stu-id="99ac8-138">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="99ac8-139">To ustawienie jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="99ac8-139">This setting is optional.</span></span> <span data-ttu-id="99ac8-140">Jeśli nie zostanie określony, będą używane domyślne powiązania.</span><span class="sxs-lookup"><span data-stu-id="99ac8-140">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="99ac8-141">Tylko powiązania z elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="99ac8-141">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="99ac8-142">Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwość powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="99ac8-142">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="99ac8-143">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="99ac8-143">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="99ac8-144">Ciąg ustawiający nazwę powiązania, które jest określone w `httpsGetBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="99ac8-144">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="99ac8-145">Taką samą nazwę, muszą być zdefiniowane w `<bindings>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="99ac8-145">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="99ac8-146">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="99ac8-146">httpsGetEnabled</span></span>|<span data-ttu-id="99ac8-147">Wartość logiczna określająca, czy publikować metadane usługi dla pobierania za pomocą żądania HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="99ac8-147">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="99ac8-148">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="99ac8-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="99ac8-149">Jeśli nie określono atrybut httpsGetUrl, adres, w którym publikowane są metadane jest adres usługi oraz "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="99ac8-149">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="99ac8-150">Na przykład jeśli adres usługi "https://localhost:8080/CalculatorService", adres metadanych HTTP/Get jest "https://localhost:8080/CalculatorService? wsdl".</span><span class="sxs-lookup"><span data-stu-id="99ac8-150">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="99ac8-151">Jeśli ta właściwość jest `false`, lub adres usługi nie jest oparty na HTTP lub HTTPS, "? wsdl" zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="99ac8-151">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="99ac8-152">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="99ac8-152">httpsGetUrl</span></span>|<span data-ttu-id="99ac8-153">Identyfikator Uri, który określa adres, w którym publikowane są metadane dla pobierania za pomocą żądania HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="99ac8-153">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="99ac8-154">PolicyVersion</span><span class="sxs-lookup"><span data-stu-id="99ac8-154">policyVersion</span></span>|<span data-ttu-id="99ac8-155">Ciąg, który określa wersję specyfikacji WS-Policy używane.</span><span class="sxs-lookup"><span data-stu-id="99ac8-155">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="99ac8-156">Ten atrybut jest typu <xref:System.ServiceModel.Description.PolicyVersion>.</span><span class="sxs-lookup"><span data-stu-id="99ac8-156">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99ac8-157">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="99ac8-157">Child Elements</span></span>  
 <span data-ttu-id="99ac8-158">Brak</span><span class="sxs-lookup"><span data-stu-id="99ac8-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99ac8-159">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="99ac8-159">Parent Elements</span></span>  
  
|<span data-ttu-id="99ac8-160">Element</span><span class="sxs-lookup"><span data-stu-id="99ac8-160">Element</span></span>|<span data-ttu-id="99ac8-161">Opis</span><span class="sxs-lookup"><span data-stu-id="99ac8-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99ac8-162">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="99ac8-162">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="99ac8-163">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="99ac8-163">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99ac8-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99ac8-164">Remarks</span></span>  
 <span data-ttu-id="99ac8-165">Ten element konfiguracji służy do kontrolowania funkcji publikowania metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="99ac8-165">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="99ac8-166">Aby zapobiec przypadkowe ujawnienie metadanych usługi potencjalnie poufnych, konfigurację domyślną dla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług wyłącza Publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="99ac8-166">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="99ac8-167">To zachowanie jest domyślnie bezpieczne, ale również zaimportować narzędzia (na przykład Svcutil.exe) oznacza, że metadane nie można użyć do generowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie podczas publikowania metadanych usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="99ac8-167">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="99ac8-168">Za pomocą tego elementu konfiguracji, można włączyć to zachowanie podczas publikowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="99ac8-168">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="99ac8-169">Aby uzyskać szczegółowy przykład konfiguracji tego zachowania, zobacz [zachowanie podczas publikowania metadanych](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="99ac8-169">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="99ac8-170">Opcjonalny `httpGetBinding` i `httpsGetBinding` atrybutów umożliwiają konfigurowanie powiązania używane do pobierania metadanych za pośrednictwem HTTP GET (lub HTTPS GET).</span><span class="sxs-lookup"><span data-stu-id="99ac8-170">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="99ac8-171">Jeśli nie są one określone, powiązania domyślnego (`HttpTransportBindingElement`, w przypadku protokołu HTTP i `HttpsTransportBindingElement`, w przypadku protokołu HTTPS) są używane do pobierania metadanych zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="99ac8-171">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="99ac8-172">Zwróć uwagę, że nie można użyć tych atrybutów z wbudowanych powiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="99ac8-172">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="99ac8-173">Tylko powiązania z elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="99ac8-173">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="99ac8-174">Ponadto <xref:System.ServiceModel.Channels.MessageVersion> właściwość powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="99ac8-174">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="99ac8-175">Aby zmniejszyć ryzyko usługi złośliwych użytkowników, jest możliwe do zabezpieczenia przy użyciu protokołu SSL za pośrednictwem protokołu HTTP (HTTPS) mechanizm transferu.</span><span class="sxs-lookup"><span data-stu-id="99ac8-175">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="99ac8-176">Aby to zrobić, należy najpierw powiązać odpowiedniego certyfikatu X.509 określonego portu na komputerze, na którym uruchomiono usługę.</span><span class="sxs-lookup"><span data-stu-id="99ac8-176">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="99ac8-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Po drugie, Dodaj ten element w konfiguracji usługi i ustaw `httpsGetEnabled` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="99ac8-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="99ac8-178">Wreszcie, ustaw `httpsGetUrl` atrybutu na adres URL punktu końcowego metadanych usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="99ac8-178">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml
<behaviors>  
  <serviceBehaviors>  
    <behavior name="NewBehavior">  
      <serviceMetadata httpsGetEnabled="true"   
                       httpsGetUrl="https://myComputerName/myEndpoint" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="example"></a><span data-ttu-id="99ac8-179">Przykład</span><span class="sxs-lookup"><span data-stu-id="99ac8-179">Example</span></span>  
 <span data-ttu-id="99ac8-180">Poniższy przykład skonfigurować usługę do udostępnienia metadanych za pomocą \<serviceMetadata > elementu.</span><span class="sxs-lookup"><span data-stu-id="99ac8-180">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="99ac8-181">Konfiguruje również punkt końcowy do udostępnienia `IMetadataExchange` kontrakt, co implementacji protokołu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="99ac8-181">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="99ac8-182">W przykładzie użyto `mexHttpBinding`, który jest powiązanie standardowe udogodnienie jest odpowiednikiem `wsHttpBinding` tryb zabezpieczeń ustawiono na `None`.</span><span class="sxs-lookup"><span data-stu-id="99ac8-182">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="99ac8-183">Względny adres "mex" jest używany w punkcie końcowym, w przypadku których nazwy zostały rozstrzygnięte na podstawowej usługi adres powoduje http://localhost/servicemodelsamples/service.svc/mex adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="99ac8-183">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService" 
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex   
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <!-- The serviceMetadata behavior publishes metadata through   
               the IMetadataExchange contract. When this behavior is   
               present, you can expose this contract through an endpoint   
               as shown above. Setting httpGetEnabled to true publishes   
               the service's WSDL at the <baseaddress>?wsdl  
               eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99ac8-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99ac8-184">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="99ac8-185">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="99ac8-185">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="99ac8-186">Zachowanie publikowania metadanych</span><span class="sxs-lookup"><span data-stu-id="99ac8-186">Metadata Publishing Behavior</span></span>](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
