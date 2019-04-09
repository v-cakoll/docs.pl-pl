---
title: Konfigurowanie usług za pomocą plików konfiguracji
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 144d2b6732ea319ba920317601eff2ebd7b58322
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132577"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="532cb-102">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="532cb-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="532cb-103">Konfigurowanie usługi Windows Communication Foundation (WCF) z plikiem konfiguracyjnym zapewnia elastyczność związanych z udostępnianiem punktu końcowego i danych zachowanie usługi na miejscu wdrożenia, a nie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="532cb-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="532cb-104">W tym temacie opisano dostępne metody podstawowej.</span><span class="sxs-lookup"><span data-stu-id="532cb-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="532cb-105">Usługa WCF jest konfigurowane za pomocą [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="532cb-105">A WCF service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="532cb-106">Najczęściej XML elementy są dodawane do pliku Web.config dla witryny usług Internet Information Services (IIS), który hostuje usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="532cb-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="532cb-107">Elementy umożliwiają zmianę szczegóły, takie jak adresy punktów końcowych (rzeczywista adresy, używane do komunikacji z usługą) na podstawie maszyny według komputera.</span><span class="sxs-lookup"><span data-stu-id="532cb-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="532cb-108">Ponadto WCF zawiera kilku elementów dostarczanych przez system, które pozwalają szybko wybrać najbardziej podstawowe funkcje dla usługi.</span><span class="sxs-lookup"><span data-stu-id="532cb-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="532cb-109">Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF, który jest dostarczany z nowy model konfiguracji domyślnej, który upraszcza wymagania dotyczące konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="532cb-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="532cb-110">Jeśli nie podano żadnej konfiguracji programu WCF dla określonej usługi, środowisko wykonawcze automatycznie konfiguruje usługi przy użyciu niektóre standardowe punkty końcowe i zachowanie wiązania domyślne.</span><span class="sxs-lookup"><span data-stu-id="532cb-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="532cb-111">W praktyce Zapisywanie konfiguracji jest poważnym należą do programowania aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="532cb-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="532cb-112">Aby uzyskać więcej informacji, zobacz [konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="532cb-112">For more information, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="532cb-113">Lista najczęściej często używanych elementów, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="532cb-113">For a list of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="532cb-114">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="532cb-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="532cb-115">Podczas wdrażania scenariuszy obok siebie, w których są wdrażane dwa różne wersje usługi, należy określić częściowych nazw zestawów, do których odwołuje się w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="532cb-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="532cb-116">Jest to spowodowane plik konfiguracji jest współużytkowany przez wszystkie wersje usługi i mogą być wykonywane w ramach różnych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="532cb-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="532cb-117">System.Configuration: Plik Web.config i pliku App.config</span><span class="sxs-lookup"><span data-stu-id="532cb-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="532cb-118">WCF używa systemu konfiguracji System.Configuration [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="532cb-118">WCF uses the System.Configuration configuration system of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="532cb-119">Podczas konfigurowania usługi w programie Visual Studio, należy użyć pliku Web.config lub pliku App.config do określania ustawień.</span><span class="sxs-lookup"><span data-stu-id="532cb-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="532cb-120">Wybór nazwy pliku konfiguracji jest określany przez środowisko hostingu, wybrany dla usługi.</span><span class="sxs-lookup"><span data-stu-id="532cb-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="532cb-121">Jeśli używasz usług IIS do hostowania usługi, należy użyć pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="532cb-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="532cb-122">Jeśli używasz innego środowiska hostingu użycie pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="532cb-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="532cb-123">W programie Visual Studio plik o nazwie pliku App.config służy do tworzenia pliku konfiguracji końcowej.</span><span class="sxs-lookup"><span data-stu-id="532cb-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="532cb-124">Nazwa końcowego rzeczywiście używane dla konfiguracji zależy od nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="532cb-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="532cb-125">Na przykład zestaw o nazwie "Cohowinery.exe" ma nazwę pliku konfiguracji końcowej "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="532cb-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="532cb-126">Jednak tylko należy zmodyfikować plik App.config.</span><span class="sxs-lookup"><span data-stu-id="532cb-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="532cb-127">Zmiany wprowadzone w tym pliku zostaną zastosowane automatycznie do pliku konfiguracyjnym ostateczny aplikacji w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="532cb-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="532cb-128">Korzystając z pliku App.config, pliku system konfiguracji scala pliku App.config przy użyciu zawartości pliku Machine.config podczas uruchamiania aplikacji i konfiguracja jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="532cb-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="532cb-129">Ten mechanizm pozwala ustawień komputera, które zostały określone w pliku Machine.config.</span><span class="sxs-lookup"><span data-stu-id="532cb-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="532cb-130">Plik App.config może służyć do zastąpienia ustawień w pliku Machine.config. Możesz również blokować w ustawieniach w pliku Machine.config, aby mogły uzyskać używane.</span><span class="sxs-lookup"><span data-stu-id="532cb-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="532cb-131">W przypadku pliku Web.config system konfiguracji scala plików Web.config we wszystkich katalogach prowadzących do katalogu aplikacji do konfiguracji, który zostanie zastosowany.</span><span class="sxs-lookup"><span data-stu-id="532cb-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="532cb-132">Aby uzyskać więcej informacji o konfiguracji i priorytety ustawienie, zobacz Tematy w <xref:System.Configuration> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="532cb-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="532cb-133">Głównych sekcji w pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="532cb-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="532cb-134">Głównych sekcji w pliku konfiguracji obejmują następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="532cb-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="532cb-135">Powiązania i zachowania sekcje są opcjonalne i można je tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="532cb-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="532cb-136">\<Usługi > — Element</span><span class="sxs-lookup"><span data-stu-id="532cb-136">The \<services> Element</span></span>  
 <span data-ttu-id="532cb-137">`services` Element zawiera specyfikacje dotyczące wszystkich usług hostów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="532cb-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="532cb-138">Począwszy od modelu uproszczona konfiguracja w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ta sekcja jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="532cb-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="532cb-139">\<services></span><span class="sxs-lookup"><span data-stu-id="532cb-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="532cb-140">\<Usługi > — Element</span><span class="sxs-lookup"><span data-stu-id="532cb-140">The \<service> Element</span></span>  
 <span data-ttu-id="532cb-141">Każda usługa ma następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="532cb-141">Each service has these attributes:</span></span>  
  
-   `name`<span data-ttu-id="532cb-142">.</span><span class="sxs-lookup"><span data-stu-id="532cb-142">.</span></span> <span data-ttu-id="532cb-143">Określa typ, który dostarcza implementację kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="532cb-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="532cb-144">Jest to w pełni kwalifikowanej nazwy, która składa się z przestrzeni nazw, kropkę oraz nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="532cb-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="532cb-145">Na przykład `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="532cb-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
-   `behaviorConfiguration`<span data-ttu-id="532cb-146">.</span><span class="sxs-lookup"><span data-stu-id="532cb-146">.</span></span> <span data-ttu-id="532cb-147">Określa nazwę jednej z `behavior` elementy znalezione w `behaviors` elementu.</span><span class="sxs-lookup"><span data-stu-id="532cb-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="532cb-148">Określonego zachowania Określa akcje, takie jak czy umożliwia personifikacji.</span><span class="sxs-lookup"><span data-stu-id="532cb-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="532cb-149">Gdy jego wartość jest pusta nazwa lub nie `behaviorConfiguration` znajduje się na wybranie domyślnego zestawu zachowania usług jest dodawana do usługi.</span><span class="sxs-lookup"><span data-stu-id="532cb-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
-   [<span data-ttu-id="532cb-150">\<service></span><span class="sxs-lookup"><span data-stu-id="532cb-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="532cb-151">\<Punktu końcowego > Element</span><span class="sxs-lookup"><span data-stu-id="532cb-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="532cb-152">Każdy punkt końcowy wymaga adresu, powiązanie i umowy, które są reprezentowane przez następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="532cb-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
-   `address`<span data-ttu-id="532cb-153">.</span><span class="sxs-lookup"><span data-stu-id="532cb-153">.</span></span> <span data-ttu-id="532cb-154">Określa usługę identyfikator (URI), który może być adresem bezwzględnym lub taki, który otrzymuje względem podstawowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="532cb-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="532cb-155">Jeśli ustawiony na pusty ciąg, informuje, że punkt końcowy jest dostępny pod podstawowym adresem, który jest określony podczas tworzenia <xref:System.ServiceModel.ServiceHost> dla usługi.</span><span class="sxs-lookup"><span data-stu-id="532cb-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
-   `binding`<span data-ttu-id="532cb-156">.</span><span class="sxs-lookup"><span data-stu-id="532cb-156">.</span></span> <span data-ttu-id="532cb-157">Zazwyczaj określa powiązania dostarczane przez system, takich jak <xref:System.ServiceModel.WSHttpBinding>, ale można również określić powiązanie zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="532cb-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="532cb-158">Określone powiązanie Określa typ transportu, zabezpieczeń i kodowanie używane i sesje niezawodne, transakcji lub przesyłania strumieniowego obsługiwany czy jest włączone.</span><span class="sxs-lookup"><span data-stu-id="532cb-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
-   `bindingConfiguration`<span data-ttu-id="532cb-159">.</span><span class="sxs-lookup"><span data-stu-id="532cb-159">.</span></span> <span data-ttu-id="532cb-160">Jeśli wartości domyślne powiązania, muszą zostać zmodyfikowane, można to zrobić, konfigurując odpowiednie `binding` element `bindings` elementu.</span><span class="sxs-lookup"><span data-stu-id="532cb-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="532cb-161">Ten atrybut powinien być podawany taką samą wartość jak `name` atrybutu `binding` element, który służy do zmiany ustawień domyślnych.</span><span class="sxs-lookup"><span data-stu-id="532cb-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="532cb-162">Jeśli nazwa nie jest określony, lub nie `bindingConfiguration` określono powiązanie, a następnie powiązanie domyślny typ powiązania jest używany w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="532cb-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
-   `contract`<span data-ttu-id="532cb-163">.</span><span class="sxs-lookup"><span data-stu-id="532cb-163">.</span></span> <span data-ttu-id="532cb-164">Określa interfejs, który definiuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="532cb-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="532cb-165">Jest to interfejs zaimplementowane w typ języka wspólnego środowiska uruchomieniowego (języka wspólnego CLR) określonej przez `name` atrybutu `service` elementu.</span><span class="sxs-lookup"><span data-stu-id="532cb-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
-   [<span data-ttu-id="532cb-166">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="532cb-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="532cb-167">\<Powiązania > Element</span><span class="sxs-lookup"><span data-stu-id="532cb-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="532cb-168">`bindings` Element zawiera specyfikacje dotyczące wszystkich powiązań, które mogą być używane przez dowolnego punktu końcowego zdefiniowana w każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="532cb-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="532cb-169">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="532cb-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="532cb-170">\<Powiązania > Element</span><span class="sxs-lookup"><span data-stu-id="532cb-170">The \<binding> Element</span></span>  
 <span data-ttu-id="532cb-171">`binding` Elementów zawartych w słowniku `bindings` element może być dowolny powiązania dostarczane przez system (zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md)) lub niestandardowego powiązania (zobacz [powiązań niestandardowych](../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="532cb-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="532cb-172">`binding` Element ma `name` atrybut, który jest odwrotnie skorelowana powiązanie z punktu końcowego określonego w `bindingConfiguration` atrybutu `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="532cb-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="532cb-173">Jeśli nazwa nie zostanie określona, a następnie to powiązanie odnosi się do domyślnego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="532cb-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="532cb-174">Aby uzyskać więcej informacji na temat konfigurowania usług i klientów, zobacz [usług WCF Konfigurowanie](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="532cb-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="532cb-175">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="532cb-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="532cb-176">\<Zachowania > Element</span><span class="sxs-lookup"><span data-stu-id="532cb-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="532cb-177">Jest to element kontenera dla `behavior` elementy, które definiują zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="532cb-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="532cb-178">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="532cb-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="532cb-179">\<Zachowanie > Element</span><span class="sxs-lookup"><span data-stu-id="532cb-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="532cb-180">Każdy `behavior` element jest identyfikowany przez `name` atrybutu i zawiera albo dostarczane przez system zachowania, takich jak <`throttling`>, lub niestandardowe zachowania.</span><span class="sxs-lookup"><span data-stu-id="532cb-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="532cb-181">Jeśli nazwa nie jest określony element tego zachowania odnosi się do domyślnego zachowania usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="532cb-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="532cb-182">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="532cb-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="532cb-183">Jak używać powiązania i konfiguracji zachowanie</span><span class="sxs-lookup"><span data-stu-id="532cb-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="532cb-184">Usługi WCF można łatwo udostępniać konfiguracje między punktami końcowymi za pomocą systemu odniesienia w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="532cb-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="532cb-185">Zamiast bezpośrednio przypisywać wartości konfiguracji w punkcie końcowym, konfiguracji odnoszące się do powiązania wartości są grupowane w `bindingConfiguration` elementów w `<binding>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="532cb-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="532cb-186">Konfiguracja powiązania jest nazwaną grupę ustawień w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="532cb-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="532cb-187">Następnie tworzyć odwołania do punktów końcowych `bindingConfiguration` według nazwy.</span><span class="sxs-lookup"><span data-stu-id="532cb-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="532cb-188">`name` z `bindingConfiguration` jest ustawiana w `<binding>` elementu.</span><span class="sxs-lookup"><span data-stu-id="532cb-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="532cb-189">`name` Musi być unikatowy ciąg w zakresie typ powiązania — w tym przypadku [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), lub wartość pustą, aby odwołać się do powiązania domyślne.</span><span class="sxs-lookup"><span data-stu-id="532cb-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="532cb-190">Łączy punkt końcowy z konfiguracją, ustawiając `bindingConfiguration` atrybutu do tego ciągu.</span><span class="sxs-lookup"><span data-stu-id="532cb-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="532cb-191">A `behaviorConfiguration` zaimplementowano ten sam sposób, jak pokazano w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="532cb-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="532cb-192">Należy pamiętać, że domyślny zestaw zachowania usług są dodawane do usługi.</span><span class="sxs-lookup"><span data-stu-id="532cb-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="532cb-193">Ten system umożliwia punktów końcowych udostępnić typowych konfiguracji bez ponownego definiowania ustawień.</span><span class="sxs-lookup"><span data-stu-id="532cb-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="532cb-194">Jeśli zakres komputera jest wymagany, należy utworzyć powiązanie lub zachowanie konfiguracji w pliku Machine.config. Ustawienia konfiguracji są dostępne we wszystkich plikach w pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="532cb-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="532cb-195">[Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) można łatwo tworzyć konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="532cb-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="532cb-196">Zachowanie scalania</span><span class="sxs-lookup"><span data-stu-id="532cb-196">Behavior Merge</span></span>  
 <span data-ttu-id="532cb-197">Funkcja scalania zachowanie ułatwia zarządzanie zachowania, gdy chcesz, aby zestaw wspólny zbiór wykonywanych czynności zawsze korzystać.</span><span class="sxs-lookup"><span data-stu-id="532cb-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="532cb-198">Ta funkcja pozwala określić zachowania na różnych poziomach hierarchii konfiguracji i usług, które dziedziczą zachowań na różnych poziomach hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="532cb-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="532cb-199">Aby zilustrować, jak ta działa przyjęto założenie, że masz następujące układu katalogu wirtualnego w usługach IIS:</span><span class="sxs-lookup"><span data-stu-id="532cb-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="532cb-200">I `~\Web.config` plik ma następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="532cb-200">And your `~\Web.config` file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="532cb-201">I ma element podrzędny, który plik Web.config znajduje się w ~\Child\Web.config z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="532cb-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="532cb-202">Usługa znajdujący się w ~\Child\Service.svc będzie działać tak, jakby ma zachowania serviceDebug i serviceMetadata w pliku.</span><span class="sxs-lookup"><span data-stu-id="532cb-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="532cb-203">Usługa znajdujący się w ~\Service.svc będzie miał tylko zachowanie serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="532cb-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="532cb-204">Co się stanie, jest scalania dwóch zachowanie kolekcji o tej samej nazwie (w tym przypadku ciąg pusty).</span><span class="sxs-lookup"><span data-stu-id="532cb-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="532cb-205">Można także wyczyścić zachowanie kolekcji za pomocą \<Wyczyść > tag i usunąć zachowania poszczególnych elementów z kolekcji przy użyciu \<Usuń > tag.</span><span class="sxs-lookup"><span data-stu-id="532cb-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="532cb-206">Na przykład następujące dwa wyniki konfiguracji w podrzędnym usługi mających tylko zachowanie serviceMetadata w pliku:</span><span class="sxs-lookup"><span data-stu-id="532cb-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="532cb-207">Zachowanie scalania jest wykonywane dla pustego zachowania kolekcji, jak pokazano powyżej i nosi nazwę kolekcji zachowań, jak również.</span><span class="sxs-lookup"><span data-stu-id="532cb-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="532cb-208">Zachowanie scalania działa w usługach IIS, środowisko, w których scalania plików Web.config hierarchicznie z głównego pliku Web.config i machine.config hostingu. Jednak ta funkcja działa w środowisku aplikacji, gdzie machine.config można scalać z pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="532cb-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="532cb-209">Scalanie zachowanie dotyczy zarówno zachowań punktu końcowego, jak i zachowania usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="532cb-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="532cb-210">Jeśli kolekcja zachowanie podrzędnych zawiera zachowania, które znajduje się już w zbiorze zachowanie nadrzędnym, zachowanie podrzędnego zastępuje element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="532cb-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="532cb-211">Tak, jeśli próba zawierała kolekcji nadrzędnej zachowanie `<serviceMetadata httpGetEnabled="False" />` i zachowanie kolekcji podrzędnej `<serviceMetadata httpGetEnabled="True" />`zachowanie podrzędnych przesłonić zachowanie nadrzędnego w kolekcji zachowanie i httpGetEnabled będzie "true".</span><span class="sxs-lookup"><span data-stu-id="532cb-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="532cb-212">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="532cb-212">See also</span></span>

- [<span data-ttu-id="532cb-213">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="532cb-213">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="532cb-214">Konfigurowanie usług WCF</span><span class="sxs-lookup"><span data-stu-id="532cb-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="532cb-215">\<service></span><span class="sxs-lookup"><span data-stu-id="532cb-215">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="532cb-216">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="532cb-216">\<binding></span></span>](../../../docs/framework/misc/binding.md)
