---
title: Konfigurowanie usług za pomocą plików konfiguracji
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: caf6e238ca286e5e712c0273e10502655fd7ff4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174800"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="82505-102">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="82505-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="82505-103">Konfigurowanie usługi Windows Communication Foundation (WCF) za pomocą pliku konfiguracji zapewnia elastyczność dostarczania danych o zachowaniu punktu końcowego i usługi w punkcie wdrożenia, a nie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="82505-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="82505-104">W tym temacie opisano podstawowe techniki dostępne.</span><span class="sxs-lookup"><span data-stu-id="82505-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="82505-105">Usługa WCF można konfigurować przy użyciu technologii konfiguracji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82505-105">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="82505-106">Najczęściej elementy XML są dodawane do pliku Web.config dla witryny internetowych usług informacyjnych (IIS), która obsługuje usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="82505-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="82505-107">Elementy umożliwiają zmianę szczegółów, takich jak adresy punktów końcowych (rzeczywiste adresy używane do komunikowania się z usługą) na podstawie komputera po komputerze.</span><span class="sxs-lookup"><span data-stu-id="82505-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="82505-108">Ponadto WCF zawiera kilka elementów dostarczonych przez system, które pozwalają szybko wybrać najbardziej podstawowe funkcje usługi.</span><span class="sxs-lookup"><span data-stu-id="82505-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="82505-109">Począwszy od programu .NET Framework 4, WCF jest wyposażony w nowy domyślny model konfiguracji, który upraszcza wymagania konfiguracyjne WCF.</span><span class="sxs-lookup"><span data-stu-id="82505-109">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="82505-110">Jeśli nie podasz żadnej konfiguracji WCF dla określonej usługi, środowisko wykonawcze automatycznie konfiguruje usługę z niektórymi standardowymi punktami końcowymi i domyślnym powiązaniem/zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="82505-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="82505-111">W praktyce pisanie konfiguracji jest główną częścią programowania aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="82505-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="82505-112">Aby uzyskać więcej informacji, zobacz [Konfigurowanie powiązań dla usług](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="82505-112">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="82505-113">Aby uzyskać listę najczęściej używanych elementów, zobacz [Powiązania dostarczone przez system](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="82505-113">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="82505-114">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [uproszczona konfiguracja usług WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="82505-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="82505-115">Podczas wdrażania scenariuszy obok siebie, w których są wdrażane dwie różne wersje usługi, konieczne jest określenie częściowych nazw zestawów, do których odwołuje się pliki konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="82505-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="82505-116">Dzieje się tak, ponieważ plik konfiguracji jest współużytkowane przez wszystkie wersje usługi i mogą być uruchomione w różnych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82505-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="82505-117">System.Configuration: Web.config i App.config</span><span class="sxs-lookup"><span data-stu-id="82505-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="82505-118">WCF używa systemu konfiguracji System.Configuration programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82505-118">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="82505-119">Podczas konfigurowania usługi w programie Visual Studio należy użyć pliku Web.config lub pliku App.config, aby określić ustawienia.</span><span class="sxs-lookup"><span data-stu-id="82505-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="82505-120">Wybór nazwy pliku konfiguracji zależy od środowiska hostingu wybranego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="82505-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="82505-121">Jeśli do obsługi usługi są używane usługi, użyj pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="82505-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="82505-122">Jeśli używasz innego środowiska hostingowego, użyj pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="82505-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="82505-123">W programie Visual Studio plik o nazwie App.config jest używany do tworzenia ostatecznego pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="82505-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="82505-124">Ostateczna nazwa faktycznie używana dla konfiguracji zależy od nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="82505-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="82505-125">Na przykład zestaw o nazwie "Cohowinery.exe" ma ostateczną nazwę pliku konfiguracji "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="82505-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="82505-126">Jednak wystarczy tylko zmodyfikować plik App.config.</span><span class="sxs-lookup"><span data-stu-id="82505-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="82505-127">Zmiany wprowadzone w tym pliku są automatycznie wprowadzane do ostatecznego pliku konfiguracji aplikacji w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="82505-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="82505-128">Korzystając z app.config, plik system konfiguracji scala plik App.config z zawartością pliku Machine.config po uruchomieniu aplikacji i zastosowaniu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="82505-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="82505-129">Mechanizm ten umożliwia zdefiniowanie ustawień dla całego komputera w pliku Machine.config.</span><span class="sxs-lookup"><span data-stu-id="82505-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="82505-130">Plik App.config może służyć do zastępowania ustawień pliku Machine.config; można również zablokować w ustawieniach pliku Machine.config, tak aby się przyzwyczaić.</span><span class="sxs-lookup"><span data-stu-id="82505-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="82505-131">W przypadku witryny Web.config system konfiguracji scala pliki Web.config we wszystkich katalogach prowadzących do katalogu aplikacji do konfiguracji, która zostanie zastosowana.</span><span class="sxs-lookup"><span data-stu-id="82505-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="82505-132">Aby uzyskać więcej informacji na temat konfiguracji i <xref:System.Configuration> priorytetów ustawień, zobacz tematy w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="82505-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="82505-133">Główne sekcje pliku konfiguracyjnego</span><span class="sxs-lookup"><span data-stu-id="82505-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="82505-134">Główne sekcje w pliku konfiguracyjnym zawierają następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="82505-134">The main sections in the configuration file include the following elements.</span></span>  
  
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
> <span data-ttu-id="82505-135">Powiązania i zachowania sekcje są opcjonalne i są uwzględniane tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="82505-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="82505-136">Usługi \<> Element</span><span class="sxs-lookup"><span data-stu-id="82505-136">The \<services> Element</span></span>  
 <span data-ttu-id="82505-137">Element `services` zawiera specyfikacje dla wszystkich usług hostów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82505-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="82505-138">Począwszy od uproszczonego modelu konfiguracji w programie .NET Framework 4, ta sekcja jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="82505-138">Starting with the simplified configuration model in .NET Framework 4, this section is optional.</span></span>  
  
 [<span data-ttu-id="82505-139">\<usługi></span><span class="sxs-lookup"><span data-stu-id="82505-139">\<services></span></span>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="82505-140">Usługa \<> Element</span><span class="sxs-lookup"><span data-stu-id="82505-140">The \<service> Element</span></span>  
 <span data-ttu-id="82505-141">Każda usługa ma następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="82505-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="82505-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="82505-142">`name`.</span></span> <span data-ttu-id="82505-143">Określa typ, który zapewnia implementację umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="82505-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="82505-144">Jest to w pełni kwalifikowana nazwa, która składa się z obszaru nazw, kropki, a następnie nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="82505-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="82505-145">Na przykład: `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="82505-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="82505-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="82505-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="82505-147">Określa nazwę jednego z `behavior` elementów znalezionych w elemencie. `behaviors`</span><span class="sxs-lookup"><span data-stu-id="82505-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="82505-148">Określone zachowanie reguluje akcje, takie jak czy usługa zezwala na personifikacji.</span><span class="sxs-lookup"><span data-stu-id="82505-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="82505-149">Jeśli jego wartość jest pusta nazwa lub nie `behaviorConfiguration` jest podana następnie domyślny zestaw zachowań usługi jest dodawany do usługi.</span><span class="sxs-lookup"><span data-stu-id="82505-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [<span data-ttu-id="82505-150">\<>serwisowe</span><span class="sxs-lookup"><span data-stu-id="82505-150">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="82505-151">Element \<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="82505-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="82505-152">Każdy punkt końcowy wymaga adresu, powiązania i umowy, które są reprezentowane przez następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="82505-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="82505-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="82505-153">`address`.</span></span> <span data-ttu-id="82505-154">Określa jednolity identyfikator zasobu usługi (URI), który może być adresem bezwzględnym lub adresem podanym względem adresu podstawowego usługi.</span><span class="sxs-lookup"><span data-stu-id="82505-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="82505-155">Jeśli ustawiono pusty ciąg, wskazuje, że punkt końcowy jest dostępny pod adresem <xref:System.ServiceModel.ServiceHost> podstawowym, który jest określony podczas tworzenia dla usługi.</span><span class="sxs-lookup"><span data-stu-id="82505-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="82505-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="82505-156">`binding`.</span></span> <span data-ttu-id="82505-157">Zazwyczaj określa powiązanie dostarczone przez <xref:System.ServiceModel.WSHttpBinding>system, takie jak , ale można również określić powiązanie zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="82505-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="82505-158">Określone powiązanie określa typ transportu, zabezpieczeń i kodowania używane i czy niezawodne sesje, transakcje lub przesyłania strumieniowego jest obsługiwany lub włączone.</span><span class="sxs-lookup"><span data-stu-id="82505-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="82505-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="82505-159">`bindingConfiguration`.</span></span> <span data-ttu-id="82505-160">Jeśli domyślne wartości powiązania muszą zostać zmodyfikowane, można to `binding` zrobić, `bindings` konfigurując odpowiedni element w elemencie.</span><span class="sxs-lookup"><span data-stu-id="82505-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="82505-161">Ten atrybut powinien mieć taką samą wartość jak `name` atrybut `binding` elementu, który jest używany do zmiany wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="82505-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="82505-162">Jeśli nazwa nie jest `bindingConfiguration` podana lub nie jest określony w powiązaniu, a następnie domyślne powiązanie typu powiązania jest używany w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="82505-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="82505-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="82505-163">`contract`.</span></span> <span data-ttu-id="82505-164">Określa interfejs definiujący kontrakt.</span><span class="sxs-lookup"><span data-stu-id="82505-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="82505-165">Jest to interfejs zaimplementowany w typie środowiska wykonawczego `name` języka wspólnego `service` (CLR) określonym przez atrybut elementu.</span><span class="sxs-lookup"><span data-stu-id="82505-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [<span data-ttu-id="82505-166">\<>punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="82505-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="82505-167">Wiązania \<> Element</span><span class="sxs-lookup"><span data-stu-id="82505-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="82505-168">Element `bindings` zawiera specyfikacje dla wszystkich powiązań, które mogą być używane przez dowolny punkt końcowy zdefiniowany w dowolnej usłudze.</span><span class="sxs-lookup"><span data-stu-id="82505-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="82505-169">\<wiązania></span><span class="sxs-lookup"><span data-stu-id="82505-169">\<bindings></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="82505-170">Element \<wiążący></span><span class="sxs-lookup"><span data-stu-id="82505-170">The \<binding> Element</span></span>  
 <span data-ttu-id="82505-171">Elementy `binding` zawarte w `bindings` elemencie mogą być jednym z powiązań dostarczonych przez system (patrz [Powiązania dostarczone przez system)](system-provided-bindings.md)lub powiązaniem niestandardowym (patrz [Powiązania niestandardowe).](./extending/custom-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="82505-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="82505-172">Element `binding` ma `name` atrybut, który koreluje powiązanie z punktem końcowym określonym w `bindingConfiguration` atrybucie `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="82505-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="82505-173">Jeśli nie nazwa jest określona, a następnie, że powiązanie odpowiada domyślnie tego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="82505-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="82505-174">Aby uzyskać więcej informacji na temat konfigurowania usług i klientów, zobacz [Konfigurowanie usług WCF](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="82505-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="82505-175">\<wiążące></span><span class="sxs-lookup"><span data-stu-id="82505-175">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="82505-176">Zachowania \<> Element</span><span class="sxs-lookup"><span data-stu-id="82505-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="82505-177">Jest to element kontenera dla `behavior` elementów, które definiują zachowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="82505-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="82505-178">\<zachowania></span><span class="sxs-lookup"><span data-stu-id="82505-178">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="82505-179">Zachowanie \<> element</span><span class="sxs-lookup"><span data-stu-id="82505-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="82505-180">Każdy `behavior` element jest identyfikowany przez `name` atrybut i zapewnia zachowanie dostarczone przez `throttling` system, takie jak <> lub zachowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="82505-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="82505-181">Jeśli nie podano nazwy, element tego zachowania odpowiada domyślnemu zachowaniu usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="82505-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="82505-182">\<>zachowania</span><span class="sxs-lookup"><span data-stu-id="82505-182">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="82505-183">Jak używać konfiguracji wiązania i zachowania</span><span class="sxs-lookup"><span data-stu-id="82505-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="82505-184">WCF ułatwia udostępnianie konfiguracji między punktami końcowymi przy użyciu systemu odniesienia w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="82505-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="82505-185">Zamiast bezpośrednio przypisywać wartości konfiguracji do punktu końcowego, wartości konfiguracji `bindingConfiguration` związane `<binding>` z powiązaniem są grupowane w elementy w sekcji.</span><span class="sxs-lookup"><span data-stu-id="82505-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="82505-186">Konfiguracja powiązania jest nazwaną grupą ustawień dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="82505-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="82505-187">Punkty końcowe mogą `bindingConfiguration` następnie odwoływać się do nazwy według.</span><span class="sxs-lookup"><span data-stu-id="82505-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
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
  
 <span data-ttu-id="82505-188">Element `name` `bindingConfiguration` jest ustawiony w `<binding>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="82505-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="82505-189">Musi `name` to być unikatowy ciąg w zakresie typu powiązania — w tym przypadku [<podstawowahttpbinowanie\>](../configure-apps/file-schema/wcf/basichttpbinding.md)lub pusta wartość, aby odwołać się do wiązania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="82505-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="82505-190">Punkt końcowy łączy się z `bindingConfiguration` konfiguracją, ustawiając atrybut do tego ciągu.</span><span class="sxs-lookup"><span data-stu-id="82505-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="82505-191">A `behaviorConfiguration` jest implementowana w ten sam sposób, jak pokazano w poniższej próbce.</span><span class="sxs-lookup"><span data-stu-id="82505-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="82505-192">Należy zauważyć, że domyślny zestaw zachowań usługi są dodawane do usługi.</span><span class="sxs-lookup"><span data-stu-id="82505-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="82505-193">System ten umożliwia punktom końcowym udostępnianie typowych konfiguracji bez ponownego definiowania ustawień.</span><span class="sxs-lookup"><span data-stu-id="82505-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="82505-194">Jeśli wymagany jest zakres dla całego komputera, utwórz konfigurację powiązania lub zachowania w pliku Machine.config. Ustawienia konfiguracji są dostępne we wszystkich plikach App.config.</span><span class="sxs-lookup"><span data-stu-id="82505-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="82505-195">[Narzędzie Edytor konfiguracji (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) ułatwia tworzenie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="82505-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="82505-196">Scalanie zachowań</span><span class="sxs-lookup"><span data-stu-id="82505-196">Behavior Merge</span></span>  
 <span data-ttu-id="82505-197">Funkcja scalania zachowań ułatwia zarządzanie zachowaniami, gdy chcesz, aby zestaw typowych zachowań był używany konsekwentnie.</span><span class="sxs-lookup"><span data-stu-id="82505-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="82505-198">Ta funkcja umożliwia określenie zachowań na różnych poziomach hierarchii konfiguracji i mają usługi dziedziczą zachowania z wielu poziomów hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="82505-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="82505-199">Aby zilustrować, jak to działa, założono, że masz następujący układ katalogu wirtualnego w usługach IIS:</span><span class="sxs-lookup"><span data-stu-id="82505-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="82505-200">A `~\Web.config` plik ma następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="82505-200">And your `~\Web.config` file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="82505-201">I masz podrzędny Web.config znajduje się na ~\Dziecko\Web.config z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="82505-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="82505-202">Usługa znajdująca się pod adresem ~\Child\Service.svc będzie zachowywać się tak, jakby miało zarówno zachowania serviceDebug, jak i serviceMetadata.</span><span class="sxs-lookup"><span data-stu-id="82505-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="82505-203">Usługa znajdująca się w ~\Service.svc będzie miała tylko zachowanie serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="82505-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="82505-204">Co się dzieje, że dwie kolekcje zachowania o tej samej nazwie (w tym przypadku pusty ciąg) są scalane.</span><span class="sxs-lookup"><span data-stu-id="82505-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="82505-205">Można również wyczyścić zachowania kolekcji przy użyciu znacznika \<> i usunąć poszczególne \<zachowania z kolekcji przy użyciu tagu> remove.</span><span class="sxs-lookup"><span data-stu-id="82505-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="82505-206">Na przykład następujące dwie wyniki konfiguracji w usłudze podrzędnej posiadające tylko zachowanie serviceMetadata:</span><span class="sxs-lookup"><span data-stu-id="82505-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="82505-207">Scalanie zachowań odbywa się dla bezimiennych kolekcji zachowań, jak pokazano powyżej i nazwane kolekcje zachowań, jak również.</span><span class="sxs-lookup"><span data-stu-id="82505-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="82505-208">Scalanie zachowania działa w środowisku hostingowym usług IIS, w którym pliki Web.config łączą się hierarchicznie z głównym plikiem Web.config i plikiem machine.config. Ale działa również w środowisku aplikacji, gdzie machine.config można scalić z plikiem App.config.</span><span class="sxs-lookup"><span data-stu-id="82505-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="82505-209">Scalanie zachowań dotyczy zarówno zachowań punktu końcowego, jak i zachowań usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="82505-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="82505-210">Jeśli kolekcja zachowania podrzędnego zawiera zachowanie, które jest już obecne w kolekcji zachowania nadrzędnego, zachowanie podrzędne zastępuje nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="82505-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="82505-211">Więc jeśli kolekcja zachowania `<serviceMetadata httpGetEnabled="False" />` nadrzędnego miał `<serviceMetadata httpGetEnabled="True" />`i kolekcji zachowania podrzędnego miał, zachowanie podrzędne będzie zastąpić zachowanie nadrzędne w kolekcji zachowania i httpGetEnabled będzie "true".</span><span class="sxs-lookup"><span data-stu-id="82505-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82505-212">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82505-212">See also</span></span>

- [<span data-ttu-id="82505-213">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="82505-213">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="82505-214">Konfigurowanie usług WCF</span><span class="sxs-lookup"><span data-stu-id="82505-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="82505-215">\<>serwisowe</span><span class="sxs-lookup"><span data-stu-id="82505-215">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="82505-216">\<wiążące></span><span class="sxs-lookup"><span data-stu-id="82505-216">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)
