---
title: "&lt;disablefusionupdatesfromadmanager —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d3a1214b4aecf56c9a6440e31459573a5922676
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a><span data-ttu-id="6b6f4-102">&lt;disablefusionupdatesfromadmanager —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="6b6f4-102">&lt;disableFusionUpdatesFromADManager&gt; Element</span></span>
<span data-ttu-id="6b6f4-103">Określa, czy zachowanie domyślne, czyli aby umożliwić host czasu wykonywania w celu zastąpienia ustawień konfiguracji dla domeny aplikacji jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="6b6f4-104">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="6b6f4-104">\<configuration> Element</span></span>  
<span data-ttu-id="6b6f4-105">\<środowisko uruchomieniowe > — Element</span><span class="sxs-lookup"><span data-stu-id="6b6f4-105">\<runtime> Element</span></span>  
<span data-ttu-id="6b6f4-106">\<disablefusionupdatesfromadmanager — ></span><span class="sxs-lookup"><span data-stu-id="6b6f4-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b6f4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b6f4-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b6f4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6b6f4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6b6f4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b6f4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6b6f4-110">Attributes</span></span>  
  
|<span data-ttu-id="6b6f4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6b6f4-111">Attribute</span></span>|<span data-ttu-id="6b6f4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6b6f4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b6f4-113">włączone</span><span class="sxs-lookup"><span data-stu-id="6b6f4-113">enabled</span></span>|<span data-ttu-id="6b6f4-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="6b6f4-115">Określa, czy domyślne możliwość zastąpienia ustawień Fusion jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6b6f4-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="6b6f4-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="6b6f4-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="6b6f4-117">Value</span></span>|<span data-ttu-id="6b6f4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="6b6f4-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b6f4-119">0</span><span class="sxs-lookup"><span data-stu-id="6b6f4-119">0</span></span>|<span data-ttu-id="6b6f4-120">Nie wyłączaj możliwości zastępują ustawienia Fusion.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="6b6f4-121">Jest to zachowanie domyślne, począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b6f4-121">This is the default behavior, starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
|<span data-ttu-id="6b6f4-122">1</span><span class="sxs-lookup"><span data-stu-id="6b6f4-122">1</span></span>|<span data-ttu-id="6b6f4-123">Wyłącz możliwości zastępują ustawienia Fusion.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="6b6f4-124">Spowoduje to przywrócenie zachowania wcześniejszych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b6f4-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6b6f4-125">Child Elements</span></span>  
 <span data-ttu-id="6b6f4-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b6f4-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6b6f4-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6b6f4-128">Element</span><span class="sxs-lookup"><span data-stu-id="6b6f4-128">Element</span></span>|<span data-ttu-id="6b6f4-129">Opis</span><span class="sxs-lookup"><span data-stu-id="6b6f4-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6b6f4-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6b6f4-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b6f4-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b6f4-132">Remarks</span></span>  
 <span data-ttu-id="6b6f4-133">Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], domyślne zachowanie jest umożliwienie <xref:System.AppDomainManager> obiektu w celu zastąpienia ustawień konfiguracji za pomocą <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości lub <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody <xref:System.AppDomainSetup> obiektu, który jest przekazywany do implementacji z <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody w Twojej podklasą klasy <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-133">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="6b6f4-134">Dla domyślnej domeny aplikacji ustawienia, które można zmienić zastępują ustawienia, które zostały określone w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="6b6f4-135">W przypadku innych domen aplikacji zastępują one ustawienia konfiguracji, które zostały przekazane do <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6b6f4-136">Możesz przekazać nowe informacje o konfiguracji, lub należy przekazać wartość null (`Nothing` w języku Visual Basic) w celu usunięcia informacji o konfiguracji, która została przekazana.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="6b6f4-137">Informacje o konfiguracji nie są przekazywane do obu <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości i <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="6b6f4-138">Zarówno w przypadku przekazania informacji o konfiguracji, informacje są przekazywane do <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwość jest ignorowana, ponieważ <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda zastępuje informacje o konfiguracji z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="6b6f4-139">Jeśli używasz <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości, można przekazać wartości null (`Nothing` w języku Visual Basic) do <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metodę, aby wyeliminować żadnych bajtów konfiguracji, które zostały określone w wywołaniu <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6b6f4-140">Oprócz informacji o konfiguracji, można zmienić następujących ustawień na <xref:System.AppDomainSetup> obiekt, który jest przekazywany do implementacji <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, i <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="6b6f4-141">Alternatywą wobec przy użyciu `<disableFusionUpdatesFromADManager>` elementu, można wyłączyć domyślnego zachowania tworząc ustawienie rejestru lub przez ustawienie zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="6b6f4-142">W rejestrze, utwórz wartość DWORD o nazwie `COMPLUS_disableFusionUpdatesFromADManager` w obszarze `HKCU\Software\Microsoft\.NETFramework` lub `HKLM\Software\Microsoft\.NETFramework`, a następnie ustaw wartość na 1.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="6b6f4-143">W wierszu polecenia, ustaw zmienną środowiskową `COMPLUS_disableFusionUpdatesFromADManager` do 1.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b6f4-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b6f4-144">Example</span></span>  
 <span data-ttu-id="6b6f4-145">Poniższy przykład pokazuje, jak wyłączenie możliwości zastępują ustawienia Fusion przy użyciu `<disableFusionUpdatesFromADManager>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6b6f4-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b6f4-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b6f4-146">See Also</span></span>  
 [<span data-ttu-id="6b6f4-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6b6f4-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="6b6f4-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6b6f4-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6b6f4-149">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6b6f4-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
