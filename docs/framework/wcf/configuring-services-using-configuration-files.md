---
title: Konfigurowanie usług za pomocą plików konfiguracji
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 9a8db0670fff604cc9db8279ab1566e6e3fd3c8d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320675"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="6b616-102">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6b616-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="6b616-103">Skonfigurowanie usługi Windows Communication Foundation (WCF) z plikiem konfiguracji zapewnia elastyczność udostępniania punktów końcowych i danych zachowania usługi w punkcie wdrożenia, a nie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="6b616-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="6b616-104">W tym temacie opisano dostępne podstawowe techniki.</span><span class="sxs-lookup"><span data-stu-id="6b616-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="6b616-105">Usługę WCF można skonfigurować za pomocą technologii konfiguracji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b616-105">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="6b616-106">Najczęściej elementy XML są dodawane do pliku Web. config dla witryny Internet Information Services (IIS), która hostuje usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="6b616-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="6b616-107">Elementy umożliwiają zmianę szczegółów, takich jak adresy punktów końcowych (rzeczywiste adresy używane do komunikowania się z usługą) na poszczególnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="6b616-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="6b616-108">Ponadto program WCF zawiera kilka elementów dostępnych w systemie, które umożliwiają szybkie wybieranie najbardziej podstawowych funkcji usługi.</span><span class="sxs-lookup"><span data-stu-id="6b616-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="6b616-109">Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF jest dostarczany z nowym domyślnym modelem konfiguracji, który upraszcza wymagania dotyczące konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="6b616-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="6b616-110">Jeśli nie podasz żadnej konfiguracji WCF dla określonej usługi, środowisko uruchomieniowe automatycznie skonfiguruje usługę przy użyciu standardowych punktów końcowych oraz domyślnego powiązania/zachowania.</span><span class="sxs-lookup"><span data-stu-id="6b616-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="6b616-111">W tym przypadku Zapisywanie konfiguracji jest główną częścią programowania aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="6b616-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="6b616-112">Aby uzyskać więcej informacji, zobacz [Konfigurowanie powiązań dla usług](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6b616-112">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="6b616-113">Aby uzyskać listę najczęściej używanych elementów, zobacz [powiązania dostarczone przez system](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="6b616-113">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="6b616-114">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6b616-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b616-115">W przypadku wdrażania w wielu różnych wersjach usługi, należy określić częściowe nazwy zestawów, do których istnieją odwołania w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6b616-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="6b616-116">Wynika to z faktu, że plik konfiguracji jest współużytkowany przez wszystkie wersje usługi i może być uruchomiony w różnych wersjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b616-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="6b616-117">System. Configuration: Web. config i App. config</span><span class="sxs-lookup"><span data-stu-id="6b616-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="6b616-118">Usługa WCF używa systemu konfiguracji system. Configuration .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b616-118">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="6b616-119">Podczas konfigurowania usługi w programie Visual Studio należy określić ustawienia za pomocą pliku Web. config lub pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="6b616-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="6b616-120">Wybór nazwy pliku konfiguracji jest określany przez środowisko hostingu wybrane dla usługi.</span><span class="sxs-lookup"><span data-stu-id="6b616-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="6b616-121">Jeśli używasz usług IIS do hostowania usługi, użyj pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="6b616-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="6b616-122">Jeśli używasz innego środowiska hostingu, użyj pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="6b616-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="6b616-123">W programie Visual Studio plik o nazwie App. config jest używany do tworzenia końcowego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6b616-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="6b616-124">Końcowa nazwa aktualnie używana na potrzeby konfiguracji zależy od nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="6b616-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="6b616-125">Na przykład zestaw o nazwie "cohowinery. exe" ma ostateczną nazwę pliku konfiguracji "cohowinery. exe. config".</span><span class="sxs-lookup"><span data-stu-id="6b616-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="6b616-126">Jednak wystarczy zmodyfikować plik App. config.</span><span class="sxs-lookup"><span data-stu-id="6b616-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="6b616-127">Zmiany wprowadzone w tym pliku są automatycznie wprowadzane do ostatecznego pliku konfiguracji aplikacji w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6b616-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="6b616-128">W przypadku korzystania z pliku App. config system konfiguracji Scala plik App. config z zawartością pliku Machine. config, gdy aplikacja zostanie uruchomiona, a konfiguracja zostanie zastosowana.</span><span class="sxs-lookup"><span data-stu-id="6b616-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="6b616-129">Ten mechanizm umożliwia zdefiniowanie ustawień całego komputera w pliku Machine. config.</span><span class="sxs-lookup"><span data-stu-id="6b616-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="6b616-130">Plik App. config może służyć do zastępowania ustawień pliku Machine. config; Możesz również zablokować ustawienia w pliku Machine. config, tak aby były używane.</span><span class="sxs-lookup"><span data-stu-id="6b616-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="6b616-131">W pliku Web. config system konfiguracji scala pliki Web. config we wszystkich katalogach, które pomogą do katalogu aplikacji, do konfiguracji, która zostanie zastosowana.</span><span class="sxs-lookup"><span data-stu-id="6b616-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="6b616-132">Aby uzyskać więcej informacji na temat konfiguracji i priorytetów ustawień, zobacz tematy w przestrzeni nazw <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="6b616-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="6b616-133">Główne sekcje pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6b616-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="6b616-134">Główne sekcje w pliku konfiguracji obejmują następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="6b616-134">The main sections in the configuration file include the following elements.</span></span>  
  
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
> <span data-ttu-id="6b616-135">Sekcje powiązania i zachowania są opcjonalne i są uwzględniane tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="6b616-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="6b616-136">@No__t-0services > elementu</span><span class="sxs-lookup"><span data-stu-id="6b616-136">The \<services> Element</span></span>  
 <span data-ttu-id="6b616-137">Element `services` zawiera specyfikacje dla wszystkich usług, które są obsługiwane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="6b616-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="6b616-138">Począwszy od uproszczonego modelu konfiguracji w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ta sekcja jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="6b616-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="6b616-139">@no__t — 1services ></span><span class="sxs-lookup"><span data-stu-id="6b616-139">\<services></span></span>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="6b616-140">@No__t-0Service > elementu</span><span class="sxs-lookup"><span data-stu-id="6b616-140">The \<service> Element</span></span>  
 <span data-ttu-id="6b616-141">Każda usługa ma następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="6b616-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="6b616-142">`name`.,</span><span class="sxs-lookup"><span data-stu-id="6b616-142">`name`.</span></span> <span data-ttu-id="6b616-143">Określa typ, który zapewnia implementację kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="6b616-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="6b616-144">Jest to w pełni kwalifikowana nazwa, która składa się z przestrzeni nazw, kropki, a następnie nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="6b616-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="6b616-145">Na przykład `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="6b616-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="6b616-146">`behaviorConfiguration`.,</span><span class="sxs-lookup"><span data-stu-id="6b616-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="6b616-147">Określa nazwę jednego z elementów `behavior` znalezionych w elemencie `behaviors`.</span><span class="sxs-lookup"><span data-stu-id="6b616-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="6b616-148">Określone zachowanie zarządza akcjami, takimi jak czy usługa zezwala na personifikację.</span><span class="sxs-lookup"><span data-stu-id="6b616-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="6b616-149">Jeśli wartość jest pustą nazwą lub nie `behaviorConfiguration`, zostanie dodany domyślny zestaw zachowań usługi do usługi.</span><span class="sxs-lookup"><span data-stu-id="6b616-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [<span data-ttu-id="6b616-150">@no__t — 1service ></span><span class="sxs-lookup"><span data-stu-id="6b616-150">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="6b616-151">@No__t-0endpoint > elementu</span><span class="sxs-lookup"><span data-stu-id="6b616-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="6b616-152">Każdy punkt końcowy wymaga adresu, powiązania i kontraktu, które są reprezentowane przez następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="6b616-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="6b616-153">`address`.,</span><span class="sxs-lookup"><span data-stu-id="6b616-153">`address`.</span></span> <span data-ttu-id="6b616-154">Określa Uniform Resource Identifier usługi (URI), który może być adresem bezwzględnym lub taki, który jest określony względem adresu podstawowego usługi.</span><span class="sxs-lookup"><span data-stu-id="6b616-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="6b616-155">W przypadku wybrania pustego ciągu wskazuje, że punkt końcowy jest dostępny pod adresem podstawowym określonym podczas tworzenia <xref:System.ServiceModel.ServiceHost> dla usługi.</span><span class="sxs-lookup"><span data-stu-id="6b616-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="6b616-156">`binding`.,</span><span class="sxs-lookup"><span data-stu-id="6b616-156">`binding`.</span></span> <span data-ttu-id="6b616-157">Zwykle określa powiązanie dostarczone z systemem, takie jak <xref:System.ServiceModel.WSHttpBinding>, ale może również określać powiązanie zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6b616-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="6b616-158">Określone powiązanie określa typ transportu, używanego zabezpieczenia i kodowanie oraz to, czy niezawodne sesje, transakcje lub przesyłanie strumieniowe są obsługiwane lub włączone.</span><span class="sxs-lookup"><span data-stu-id="6b616-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="6b616-159">`bindingConfiguration`.,</span><span class="sxs-lookup"><span data-stu-id="6b616-159">`bindingConfiguration`.</span></span> <span data-ttu-id="6b616-160">Jeśli wartości domyślne powiązania muszą być modyfikowane, można to zrobić przez skonfigurowanie odpowiedniego elementu `binding` w elemencie `bindings`.</span><span class="sxs-lookup"><span data-stu-id="6b616-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="6b616-161">Ten atrybut powinien mieć taką samą wartość jak atrybut `name` elementu `binding`, który jest używany do zmiany wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="6b616-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="6b616-162">Jeśli nie podano nazwy lub w powiązaniu nie określono `bindingConfiguration`, to domyślne powiązanie typu powiązania jest używane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="6b616-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="6b616-163">`contract`.,</span><span class="sxs-lookup"><span data-stu-id="6b616-163">`contract`.</span></span> <span data-ttu-id="6b616-164">Określa interfejs, który definiuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="6b616-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="6b616-165">Jest to interfejs zaimplementowany w typie środowiska uruchomieniowego języka wspólnego (CLR) określony przez atrybut `name` elementu `service`.</span><span class="sxs-lookup"><span data-stu-id="6b616-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [<span data-ttu-id="6b616-166">@no__t — 1endpoint ></span><span class="sxs-lookup"><span data-stu-id="6b616-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="6b616-167">@No__t-0bindings > elementu</span><span class="sxs-lookup"><span data-stu-id="6b616-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="6b616-168">Element `bindings` zawiera specyfikacje dla wszystkich powiązań, które mogą być używane przez dowolny punkt końcowy zdefiniowany w dowolnej usłudze.</span><span class="sxs-lookup"><span data-stu-id="6b616-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="6b616-169">@no__t — 1bindings ></span><span class="sxs-lookup"><span data-stu-id="6b616-169">\<bindings></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="6b616-170">@No__t-0binding > elementu</span><span class="sxs-lookup"><span data-stu-id="6b616-170">The \<binding> Element</span></span>  
 <span data-ttu-id="6b616-171">Elementy `binding` zawarte w elemencie `bindings` mogą być jednym z powiązań dostarczonych przez system (patrz [powiązania dostarczone z systemem](system-provided-bindings.md)) lub powiązaniem niestandardowym (zobacz [powiązania niestandardowe](./extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="6b616-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="6b616-172">Element `binding` ma atrybut `name`, który skorelowanie powiązania z punktem końcowym określonym w atrybucie `bindingConfiguration` elementu `endpoint`.</span><span class="sxs-lookup"><span data-stu-id="6b616-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="6b616-173">Jeśli nazwa nie zostanie określona, to powiązanie odnosi się do wartości domyślnej tego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="6b616-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="6b616-174">Aby uzyskać więcej informacji na temat konfigurowania usług i klientów, zobacz [Konfigurowanie usług WCF](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="6b616-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="6b616-175">@no__t — 1binding ></span><span class="sxs-lookup"><span data-stu-id="6b616-175">\<binding></span></span>](../misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="6b616-176">@No__t-0behaviors > elementu</span><span class="sxs-lookup"><span data-stu-id="6b616-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="6b616-177">Jest to element kontenera dla elementów `behavior`, które definiują zachowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="6b616-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="6b616-178">@no__t — 1behaviors ></span><span class="sxs-lookup"><span data-stu-id="6b616-178">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="6b616-179">@No__t-0behavior > elementu</span><span class="sxs-lookup"><span data-stu-id="6b616-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="6b616-180">Każdy element `behavior` jest identyfikowany przez atrybut `name` i zapewnia zachowanie dostarczone przez system, takie jak < `throttling` > lub niestandardowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="6b616-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="6b616-181">Jeśli nazwa nie zostanie określona, ten element zachowania odnosi się do domyślnego zachowania usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6b616-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="6b616-182">@no__t — 1behavior ></span><span class="sxs-lookup"><span data-stu-id="6b616-182">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="6b616-183">Jak używać konfiguracji powiązań i zachowań</span><span class="sxs-lookup"><span data-stu-id="6b616-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="6b616-184">Program WCF ułatwia udostępnianie konfiguracji między punktami końcowymi przy użyciu systemu odniesienia w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6b616-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="6b616-185">Zamiast bezpośredniego przypisywania wartości konfiguracyjnych do punktu końcowego wartości konfiguracyjne powiązane z powiązaniem są pogrupowane w `bindingConfiguration` elementów w sekcji `<binding>`.</span><span class="sxs-lookup"><span data-stu-id="6b616-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="6b616-186">Konfiguracja powiązania to nazwana grupa ustawień dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="6b616-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="6b616-187">Punkty końcowe mogą następnie odwoływać się do `bindingConfiguration` według nazwy.</span><span class="sxs-lookup"><span data-stu-id="6b616-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
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
  
 <span data-ttu-id="6b616-188">@No__t-0 `bindingConfiguration` jest ustawiony w elemencie `<binding>`.</span><span class="sxs-lookup"><span data-stu-id="6b616-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="6b616-189">@No__t-0 musi być unikatowym ciągiem w zakresie typu powiązania — w tym przypadku [< BasicHttpBinding @ no__t-2](../configure-apps/file-schema/wcf/basichttpbinding.md)lub pustą wartość, aby odwołać się do powiązania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="6b616-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="6b616-190">Punkt końcowy łączy się z konfiguracją przez ustawienie atrybutu `bindingConfiguration` na ten ciąg.</span><span class="sxs-lookup"><span data-stu-id="6b616-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="6b616-191">@No__t-0 jest zaimplementowana w taki sam sposób, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6b616-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="6b616-192">Należy zauważyć, że domyślny zestaw zachowań usługi jest dodawany do usługi.</span><span class="sxs-lookup"><span data-stu-id="6b616-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="6b616-193">Ten system umożliwia używanie punktów końcowych do udostępniania wspólnych konfiguracji bez ponownego definiowania ustawień.</span><span class="sxs-lookup"><span data-stu-id="6b616-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="6b616-194">Jeśli wymagany jest zakres całego komputera, należy utworzyć konfigurację powiązania lub zachowania w pliku Machine. config. Ustawienia konfiguracji są dostępne we wszystkich plikach App. config.</span><span class="sxs-lookup"><span data-stu-id="6b616-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="6b616-195">[Narzędzie edytora konfiguracji (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md) ułatwia tworzenie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6b616-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="6b616-196">Scalanie zachowań</span><span class="sxs-lookup"><span data-stu-id="6b616-196">Behavior Merge</span></span>  
 <span data-ttu-id="6b616-197">Funkcja scalania zachowań ułatwia zarządzanie zachowaniami, gdy istnieje potrzeba spójnego stosowania zestawu typowych zachowań.</span><span class="sxs-lookup"><span data-stu-id="6b616-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="6b616-198">Ta funkcja umożliwia określenie zachowań na różnych poziomach w hierarchii konfiguracji, a usługi dziedziczą zachowania z wielu poziomów hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6b616-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="6b616-199">Aby zilustrować, jak to działa, Załóżmy, że w usługach IIS znajduje się następujący układ katalogu wirtualnego:</span><span class="sxs-lookup"><span data-stu-id="6b616-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="6b616-200">A plik `~\Web.config` ma następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="6b616-200">And your `~\Web.config` file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="6b616-201">Istnieje natomiast plik Web. config znajdujący się w lokalizacji ~ \Child\Web.config z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="6b616-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="6b616-202">Usługa znajdująca się w lokalizacji ~ \Child\Service.svc będzie zachowywać się tak, jakby miała zarówno zachowanie serviceDebug, jak i ServiceMetadata.</span><span class="sxs-lookup"><span data-stu-id="6b616-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="6b616-203">Usługa zlokalizowana w lokalizacji ~ \Service.svc będzie miała tylko zachowanie serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="6b616-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="6b616-204">Dzieje się tak, aby dwie kolekcje zachowań o tej samej nazwie (w tym przypadku pusty ciąg) zostały scalone.</span><span class="sxs-lookup"><span data-stu-id="6b616-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="6b616-205">Możesz również wyczyścić kolekcje zachowań przy użyciu tagu \<clear > i usunąć pojedyncze zachowania z kolekcji przy użyciu tagu \<remove >.</span><span class="sxs-lookup"><span data-stu-id="6b616-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="6b616-206">Na przykład następujące dwie wyniki konfiguracji w usłudze podrzędnej mają tylko zachowanie usługi ServiceMetadata:</span><span class="sxs-lookup"><span data-stu-id="6b616-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="6b616-207">Scalanie zachowań odbywa się dla kolekcji zachowań pustego, jak pokazano powyżej i nazwanych kolekcji zachowań.</span><span class="sxs-lookup"><span data-stu-id="6b616-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="6b616-208">Scalanie zachowań działa w środowisku hostingu usług IIS, w którym pliki Web. config są scalane hierarchicznie z głównym plikiem Web. config i Machine. config. Działa również w środowisku aplikacji, gdzie Machine. config można scalić z plikiem app. config.</span><span class="sxs-lookup"><span data-stu-id="6b616-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="6b616-209">Scalanie zachowań dotyczy zarówno zachowań punktu końcowego, jak i zachowań usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6b616-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="6b616-210">Jeśli kolekcja zachowań podrzędnych zawiera zachowanie, które jest już obecne w kolekcji zachowań nadrzędnych, zachowanie podrzędne zastępuje element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="6b616-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="6b616-211">Dlatego jeśli nadrzędna kolekcja zachowań miała `<serviceMetadata httpGetEnabled="False" />`, a kolekcja zachowań podrzędnych miała `<serviceMetadata httpGetEnabled="True" />`, zachowanie potomne przesłoni zachowanie nadrzędne w kolekcji zachowań, a httpGetEnabled będzie "true".</span><span class="sxs-lookup"><span data-stu-id="6b616-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b616-212">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b616-212">See also</span></span>

- [<span data-ttu-id="6b616-213">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="6b616-213">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="6b616-214">Konfigurowanie usług WCF</span><span class="sxs-lookup"><span data-stu-id="6b616-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="6b616-215">@no__t — 1service ></span><span class="sxs-lookup"><span data-stu-id="6b616-215">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="6b616-216">@no__t — 1binding ></span><span class="sxs-lookup"><span data-stu-id="6b616-216">\<binding></span></span>](../misc/binding.md)
