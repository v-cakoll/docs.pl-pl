---
title: "&lt;appdomainmanagerassembly —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e07b7bd18f19439f64ed8eaef5bda3bad5cef77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltappdomainmanagerassemblygt-element"></a><span data-ttu-id="c5ac1-102">&lt;appdomainmanagerassembly —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="c5ac1-102">&lt;appDomainManagerAssembly&gt; Element</span></span>
<span data-ttu-id="c5ac1-103">Określa zestaw, który udostępnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
 <span data-ttu-id="c5ac1-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="c5ac1-104">\<configuration></span></span>  
<span data-ttu-id="c5ac1-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="c5ac1-105">\<runtime></span></span>  
<span data-ttu-id="c5ac1-106">\<appdomainmanagerassembly — ></span><span class="sxs-lookup"><span data-stu-id="c5ac1-106">\<appDomainManagerAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ac1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5ac1-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5ac1-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c5ac1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c5ac1-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5ac1-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c5ac1-110">Attributes</span></span>  
  
|<span data-ttu-id="c5ac1-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c5ac1-111">Attribute</span></span>|<span data-ttu-id="c5ac1-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c5ac1-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="c5ac1-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-113">Required attribute.</span></span> <span data-ttu-id="c5ac1-114">Określa nazwę wyświetlaną zestawu, który udostępnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5ac1-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c5ac1-115">Child Elements</span></span>  
 <span data-ttu-id="c5ac1-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5ac1-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c5ac1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c5ac1-118">Element</span><span class="sxs-lookup"><span data-stu-id="c5ac1-118">Element</span></span>|<span data-ttu-id="c5ac1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c5ac1-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c5ac1-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c5ac1-121">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5ac1-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5ac1-122">Remarks</span></span>  
 <span data-ttu-id="c5ac1-123">Aby określić typ Menedżer domeny aplikacji, należy określić zarówno tego elementu i [ \<appdomainmanagertype — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="c5ac1-124">Jeśli nie określono żadnego z tych elementów, druga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="c5ac1-125">Po załadowaniu domyślnej domeny aplikacji <xref:System.TypeLoadException> jest generowany, jeśli określony zestaw nie istnieje lub zestaw nie zawiera typu określonego przez [ \<appdomainmanagertype — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; i proces nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="c5ac1-126">Jeśli zostanie znaleziony w zestawie, ale informacje o wersji nie jest zgodny, <xref:System.IO.FileLoadException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="c5ac1-127">Po określeniu typu Menedżer domeny aplikacji dla domyślnej domeny aplikacji innych domen aplikacji utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="c5ac1-128">Użyj <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> i <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> właściwości, aby określić typ Menedżera domeny w innej aplikacji dla nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="c5ac1-129">Określanie typu Menedżer domeny aplikacji wymaga aplikacja miała pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="c5ac1-130">(Na przykład aplikacja uruchomiona na komputerze ma pełnego zaufania). Jeśli aplikacja jest w pełni zaufany <xref:System.TypeLoadException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="c5ac1-131">Format nazwy wyświetlanej zestawu dla <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="c5ac1-132">Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszych.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-132">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5ac1-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5ac1-133">Example</span></span>  
 <span data-ttu-id="c5ac1-134">Poniższy przykład przedstawia sposób określić, że Menedżer domeny aplikacji dla domyślnej domeny aplikacji procesu jest `MyMgr` wpisz `AdMgrExample` zestawu.</span><span class="sxs-lookup"><span data-stu-id="c5ac1-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5ac1-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5ac1-135">See Also</span></span>  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="c5ac1-136">\<appdomainmanagertype — > — Element</span><span class="sxs-lookup"><span data-stu-id="c5ac1-136">\<appDomainManagerType> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
 [<span data-ttu-id="c5ac1-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c5ac1-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="c5ac1-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c5ac1-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="c5ac1-139">SetAppDomainManagerType — metoda</span><span class="sxs-lookup"><span data-stu-id="c5ac1-139">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
