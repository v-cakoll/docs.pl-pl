---
title: Konfigurowanie usług za pomocą plików konfiguracji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62a8774ab2843d0b1f0a19ad04fc0a76abb7cac5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="c2b50-102">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c2b50-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="c2b50-103">Konfigurowanie [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi przy użyciu pliku konfiguracji zapewnia elastyczność udostępniania punktu końcowego i Usługa danych zachowanie w punkcie wdrożenia, a nie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="c2b50-103">Configuring a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="c2b50-104">W tym temacie przedstawiono podstawowe metody dostępne.</span><span class="sxs-lookup"><span data-stu-id="c2b50-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="c2b50-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługa jest można skonfigurować przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="c2b50-106">Najczęściej, elementy XML są dodawane do pliku Web.config dla witryny Internet Information Services (IIS), który jest hostem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="c2b50-107">Elementy umożliwiają zmianę szczegółowe informacje, takie jak adresy punktów końcowych (rzeczywiste adresy używane do komunikacji z usługą) na komputerze przez komputer.</span><span class="sxs-lookup"><span data-stu-id="c2b50-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="c2b50-108">Ponadto [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zawiera kilka elementów dostarczane przez system, które umożliwiają szybkie wybranie najbardziej podstawowych funkcji usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-108">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="c2b50-109">Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] jest dostarczany z nowy model konfiguracji domyślne, które upraszcza [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] wymagania dotyczące konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="c2b50-110">Jeśli nie podano żadnego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfiguracji dla określonej usługi, środowisko uruchomieniowe automatycznie konfiguruje usługi z niektórymi standardowych punktów końcowych i zachowanie wiązania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="c2b50-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="c2b50-111">W praktyce, zapisywanie konfiguracji to główne programowania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-111">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
 <span data-ttu-id="c2b50-112">Aby uzyskać więcej informacji, zobacz [konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c2b50-112">For more information, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="c2b50-113">Dla listy z najbardziej często używanych elementów, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="c2b50-113">For a list of of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="c2b50-114">Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c2b50-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2b50-115">Podczas wdrażania scenariuszy dla siebie wdrożonym dwie różne wersje usługi, jest niezbędne do określenia częściowych nazw zestawów, do których odwołuje się w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="c2b50-116">Jest tak, ponieważ plik konfiguracji jest współużytkowana przez wszystkie wersje usługi i mogą być wykonywane w różnych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2b50-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="c2b50-117">System.Configuration: Plik Web.config i App.config</span><span class="sxs-lookup"><span data-stu-id="c2b50-117">System.Configuration: Web.config and App.config</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="c2b50-118"> używa systemu konfiguracji System.Configuration [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2b50-118"> uses the System.Configuration configuration system of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="c2b50-119">Podczas konfigurowania usługi w programie Visual Studio, użyj pliku Web.config lub pliku App.config, aby określić ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c2b50-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="c2b50-120">Wybór nazwy pliku konfiguracji jest określana przez środowisko macierzyste, wybranych dla usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="c2b50-121">Jeśli używane są usługi IIS do obsługi usługi, należy użyć pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="c2b50-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="c2b50-122">Jeśli używane są inne środowiska macierzystego, należy użyć pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="c2b50-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="c2b50-123">W programie Visual Studio plik o nazwie App.config służy do tworzenia pliku konfiguracji końcowej.</span><span class="sxs-lookup"><span data-stu-id="c2b50-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="c2b50-124">Nazwa końcowej faktycznie używana dla konfiguracji zależy od nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="c2b50-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="c2b50-125">Na przykład zestaw o nazwie "Cohowinery.exe" ma nazwę konfiguracji końcowej "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="c2b50-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="c2b50-126">Jednak tylko musisz zmodyfikować plik App.config.</span><span class="sxs-lookup"><span data-stu-id="c2b50-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="c2b50-127">Zmiany wprowadzone w tym pliku zostaną zastosowane do pliku konfiguracji aplikacji końcowego automatycznie w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="c2b50-128">Korzystając z pliku App.config, pliku system konfiguracji scala pliku App.config z zawartością pliku Machine.config podczas uruchamiania aplikacji i konfiguracja zostanie zastosowana.</span><span class="sxs-lookup"><span data-stu-id="c2b50-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="c2b50-129">Mechanizm ten umożliwia ustawień komputera, które zostały określone w pliku Machine.config.</span><span class="sxs-lookup"><span data-stu-id="c2b50-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="c2b50-130">Plik App.config może służyć do zastąpienia ustawień pliku Machine.config. można również zablokować w ustawieniach w pliku Machine.config, aby mogły uzyskać używane.</span><span class="sxs-lookup"><span data-stu-id="c2b50-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="c2b50-131">W przypadku pliku Web.config system konfiguracji scala plików Web.config we wszystkich katalogach prowadzących do katalogu aplikacji do konfiguracji, który zostanie zastosowany.</span><span class="sxs-lookup"><span data-stu-id="c2b50-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="c2b50-132">Aby uzyskać więcej informacji o konfiguracji i priorytety ustawienia, zobacz Tematy w <xref:System.Configuration> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c2b50-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="c2b50-133">Główna sekcji w pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c2b50-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="c2b50-134">Głównych sekcji w pliku konfiguracji obejmują następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="c2b50-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!—- Define the service endpoints. This section is optional in the new  
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
>  <span data-ttu-id="c2b50-135">Powiązania i zachowania sekcje są opcjonalne i są tylko jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="c2b50-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="c2b50-136">\<Usługi > — Element</span><span class="sxs-lookup"><span data-stu-id="c2b50-136">The \<services> Element</span></span>  
 <span data-ttu-id="c2b50-137">`services` Element zawiera wymagania dotyczące wszystkich usług hostów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="c2b50-138">Począwszy od modelu uproszczona konfiguracja w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ta sekcja jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c2b50-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="c2b50-139">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="c2b50-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="c2b50-140">\<Usługi > — Element</span><span class="sxs-lookup"><span data-stu-id="c2b50-140">The \<service> Element</span></span>  
 <span data-ttu-id="c2b50-141">Każda usługa ma następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="c2b50-141">Each service has these attributes:</span></span>  
  
-   <span data-ttu-id="c2b50-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="c2b50-142">`name`.</span></span> <span data-ttu-id="c2b50-143">Określa typ, który zawiera implementację kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="c2b50-144">Jest to pełna nazwa, która składa się z przestrzeni nazw, okres, a następnie nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="c2b50-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="c2b50-145">Na przykład `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="c2b50-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
-   <span data-ttu-id="c2b50-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="c2b50-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="c2b50-147">Określa nazwę jednego z `behavior` elementy znalezione w `behaviors` elementu.</span><span class="sxs-lookup"><span data-stu-id="c2b50-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="c2b50-148">Zachowanie określonego reguluje akcje, takie jak określa, czy usługa umożliwia personifikacji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="c2b50-149">Jeśli wartość jest pusta nazwa lub nie `behaviorConfiguration` podano domyślny zestaw zachowań usługi jest dodawana do usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
-   [<span data-ttu-id="c2b50-150">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="c2b50-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="c2b50-151">\<Punktu końcowego > — Element</span><span class="sxs-lookup"><span data-stu-id="c2b50-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="c2b50-152">Każdy punkt końcowy wymaga adresu, powiązania i kontraktu, które są reprezentowane przez następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="c2b50-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
-   <span data-ttu-id="c2b50-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="c2b50-153">`address`.</span></span> <span data-ttu-id="c2b50-154">Określa usługi identyfikator URI (Uniform Resource), może to adres bezwzględny lub taki, który znajduje się względem adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="c2b50-155">Jeśli wartość pustego ciągu, informuje, że punkt końcowy jest dostępny na adres podstawowy, który został określony podczas tworzenia <xref:System.ServiceModel.ServiceHost> dla usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
-   <span data-ttu-id="c2b50-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="c2b50-156">`binding`.</span></span> <span data-ttu-id="c2b50-157">Zazwyczaj określa powiązania dostarczane przez system, takich jak <xref:System.ServiceModel.WSHttpBinding>, ale można również określić powiązania zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c2b50-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="c2b50-158">Określone powiązanie Określa typ transportu, zabezpieczeń i kodowanie używane i niezawodne sesje, transakcje lub przesyłania strumieniowego obsługiwane czy jest włączone.</span><span class="sxs-lookup"><span data-stu-id="c2b50-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
-   <span data-ttu-id="c2b50-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="c2b50-159">`bindingConfiguration`.</span></span> <span data-ttu-id="c2b50-160">Jeśli wartości domyślne powiązania muszą zostać zmodyfikowane, można to zrobić przez skonfigurowanie odpowiednie `binding` element `bindings` elementu.</span><span class="sxs-lookup"><span data-stu-id="c2b50-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="c2b50-161">Ten atrybut powinien mieć taką samą wartość jak `name` atrybutu `binding` element, który służy do zmiany ustawień domyślnych.</span><span class="sxs-lookup"><span data-stu-id="c2b50-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="c2b50-162">Jeśli nazwa nie jest określony, lub nie `bindingConfiguration` określono powiązanie, powiązanie domyślny typ powiązania zostanie użyta w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="c2b50-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
-   <span data-ttu-id="c2b50-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="c2b50-163">`contract`.</span></span> <span data-ttu-id="c2b50-164">Określa interfejs, który definiuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c2b50-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="c2b50-165">To jest zaimplementowana w wspólny typ środowiska uruchomieniowego (języka wspólnego CLR) język określony przez interfejs `name` atrybutu `service` elementu.</span><span class="sxs-lookup"><span data-stu-id="c2b50-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
-   [<span data-ttu-id="c2b50-166">\<punkt końcowy > odwołanie do elementu</span><span class="sxs-lookup"><span data-stu-id="c2b50-166">\<endpoint> element reference</span></span>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="c2b50-167">\<Powiązania > — Element</span><span class="sxs-lookup"><span data-stu-id="c2b50-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="c2b50-168">`bindings` Element zawiera specyfikacje dla wszystkich powiązań, które mogą być używane przez dowolnego punktu końcowego zdefiniowana w dowolnej usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="c2b50-169">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c2b50-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="c2b50-170">\<Powiązania > — Element</span><span class="sxs-lookup"><span data-stu-id="c2b50-170">The \<binding> Element</span></span>  
 <span data-ttu-id="c2b50-171">`binding` Elementów zawartych w `bindings` element może być jedną z powiązania dostarczane przez system (zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md)) lub niestandardowego powiązania (zobacz [niestandardowego powiązania](../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="c2b50-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="c2b50-172">`binding` Element ma `name` atrybutu odpowiadająca powiązania z punktem końcowym określone w `bindingConfiguration` atrybutu `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="c2b50-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="c2b50-173">Jeśli nazwa nie zostanie określona, a następnie tego powiązania odpowiada wartość domyślna tego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="c2b50-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
 <span data-ttu-id="c2b50-174">Aby uzyskać więcej informacji na temat konfigurowania usług i klientów, zobacz [Konfigurowanie aplikacji systemu Windows Communication Foundation](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="c2b50-174">For more information about configuring services and clients, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
 [<span data-ttu-id="c2b50-175">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c2b50-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="c2b50-176">\<Zachowania > — Element</span><span class="sxs-lookup"><span data-stu-id="c2b50-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="c2b50-177">To jest elementem kontenera `behavior` elementów, które definiują zachowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="c2b50-178">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="c2b50-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="c2b50-179">\<Zachowanie > — Element</span><span class="sxs-lookup"><span data-stu-id="c2b50-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="c2b50-180">Każdy `behavior` element jest identyfikowany przez `name` atrybutu i zawiera albo dostarczane przez system zachowanie, takich jak <`throttling`>, lub zachowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="c2b50-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="c2b50-181">Jeśli nazwa nie jest określony element tego zachowania odpowiada domyślnego zachowania usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c2b50-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="c2b50-182">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="c2b50-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="c2b50-183">Jak używać powiązania i konfiguracje zachowanie</span><span class="sxs-lookup"><span data-stu-id="c2b50-183">How to Use Binding and Behavior Configurations</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="c2b50-184"> można łatwo udostępniać konfiguracje między punktami końcowymi za pomocą systemu odniesienia w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-184"> makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="c2b50-185">Zamiast bezpośrednio przypisywać wartości konfiguracji punktu końcowego, wartości konfiguracji odnoszące się do powiązania są pogrupowane w `bindingConfiguration` elementów w `<binding>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="c2b50-186">Konfiguracja powiązania jest nazwaną grupę ustawień w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="c2b50-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="c2b50-187">Następnie można odwoływać się punkty końcowe `bindingConfiguration` według nazwy.</span><span class="sxs-lookup"><span data-stu-id="c2b50-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!—- Default binding for basicHttpBinding -->  
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
  
 <span data-ttu-id="c2b50-188">`name` z `bindingConfiguration` jest ustawiany w `<binding>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c2b50-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="c2b50-189">`name` Musi być unikatowy ciąg w zakresie typ powiązania — w takim przypadku [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), lub wartość pusta w odwołaniu do powiązania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="c2b50-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="c2b50-190">Punkt końcowy łącza do konfiguracji przez ustawienie `bindingConfiguration` atrybutu na ciąg.</span><span class="sxs-lookup"><span data-stu-id="c2b50-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="c2b50-191">A `behaviorConfiguration` zaimplementowano tak samo, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c2b50-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="c2b50-192">Należy pamiętać, że zestaw domyślnego zachowania usługi są dodawane do usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="c2b50-193">Ten system umożliwia punktów końcowych udostępnić typowe konfiguracje bez ponowne definiowanie ustawień.</span><span class="sxs-lookup"><span data-stu-id="c2b50-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="c2b50-194">Jeśli zakres komputera jest wymagane, należy utworzyć powiązanie lub zachowania konfiguracji w pliku Machine.config. Ustawienia konfiguracji są dostępne we wszystkich plikach App.config.</span><span class="sxs-lookup"><span data-stu-id="c2b50-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="c2b50-195">[Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) ułatwia tworzenie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="c2b50-196">Zachowanie scalania</span><span class="sxs-lookup"><span data-stu-id="c2b50-196">Behavior Merge</span></span>  
 <span data-ttu-id="c2b50-197">Zachowanie funkcji scalania ułatwia zarządzanie zachowania, gdy ma zestaw zachowań wspólnych zawsze korzystać.</span><span class="sxs-lookup"><span data-stu-id="c2b50-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="c2b50-198">Ta funkcja pozwala na określenie zachowania na różnych poziomach hierarchii konfiguracji i ma dziedziczyć z różnych poziomów hierarchii konfiguracji zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="c2b50-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="c2b50-199">Aby zilustrować jak to działa założono, że następujące układu katalogu wirtualnego w usługach IIS:</span><span class="sxs-lookup"><span data-stu-id="c2b50-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 <span data-ttu-id="c2b50-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span><span class="sxs-lookup"><span data-stu-id="c2b50-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span></span>  
  
 <span data-ttu-id="c2b50-201">I plik ~\Web.config ma następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="c2b50-201">And your ~\Web.config file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="c2b50-202">I ma element podrzędny, które Web.config znajdującym się w ~\Child\Web.config z następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="c2b50-202">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="c2b50-203">Usługi znajdującej się na ~\Child\Service.svc będą zachowywać się tak, jakby ma zarówno serviceDebug, jak i serviceMetadata zachowania.</span><span class="sxs-lookup"><span data-stu-id="c2b50-203">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="c2b50-204">Usługi znajdującej się na ~\Service.svc będzie miał tylko zachowanie serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="c2b50-204">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="c2b50-205">Co się stanie, jest scalania kolekcje dwóch zachowanie o takiej samej nazwie (w tym przypadku ciągiem pustym).</span><span class="sxs-lookup"><span data-stu-id="c2b50-205">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="c2b50-206">Można także wyczyścić kolekcji zachowań przy użyciu \<Wyczyść > tagu i usunąć zachowania poszczególnych elementów z kolekcji przy użyciu \<Usuń > tagu.</span><span class="sxs-lookup"><span data-stu-id="c2b50-206">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="c2b50-207">Na przykład następujące dwa wyniki konfiguracji w podrzędnym usługi o tylko zachowanie serviceMetadata:</span><span class="sxs-lookup"><span data-stu-id="c2b50-207">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="c2b50-208">Scalanie zachowanie jest wykonywane dla kolekcji zachowań bez, zgodnie z powyższym i nosi nazwę również kolekcji zachowań.</span><span class="sxs-lookup"><span data-stu-id="c2b50-208">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="c2b50-209">Zachowanie scalania działa w usługach IIS, środowisko, w którym scalania plików Web.config hierarchicznie z głównego pliku Web.config i machine.config hostingu. Jednak działa w środowisku aplikacji, w którym machine.config może łączyć się z pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="c2b50-209">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="c2b50-210">Zachowanie scalania stosuje się do zachowania punktu końcowego i usługa zachowania w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c2b50-210">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="c2b50-211">Jeśli podrzędnej kolekcji zachowanie zawiera zachowania, które jest już obecny w kolekcji zachowań nadrzędnej, zachowanie podrzędnego zastępuje element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="c2b50-211">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="c2b50-212">Dlatego w przypadku kolekcji zachowań nadrzędny ma `<serviceMetadata httpGetEnabled="False" />` i została podrzędnej kolekcji zachowanie `<serviceMetadata httpGetEnabled="True" />`, działanie podrzędne spowoduje zastąpienie zachowania nadrzędnego w kolekcji zachowań i httpGetEnabled byłoby "true".</span><span class="sxs-lookup"><span data-stu-id="c2b50-212">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b50-213">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2b50-213">See Also</span></span>  
 [<span data-ttu-id="c2b50-214">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c2b50-214">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="c2b50-215">Konfigurowanie systemu Windows Communication Foundation aplikacji</span><span class="sxs-lookup"><span data-stu-id="c2b50-215">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="c2b50-216">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="c2b50-216">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [<span data-ttu-id="c2b50-217">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c2b50-217">\<binding></span></span>](../../../docs/framework/misc/binding.md)
