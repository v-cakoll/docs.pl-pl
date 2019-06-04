---
title: <appDomainManagerType>, element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19cd74f0e2550ec91cb56e70cf34a03bd84fc60e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487739"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="7b14e-102">\<appdomainmanagertype — > Element</span><span class="sxs-lookup"><span data-stu-id="7b14e-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="7b14e-103">Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7b14e-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
 <span data-ttu-id="7b14e-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="7b14e-104">\<configuration></span></span>  
<span data-ttu-id="7b14e-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="7b14e-105">\<runtime></span></span>  
<span data-ttu-id="7b14e-106">\<appDomainManagerType></span><span class="sxs-lookup"><span data-stu-id="7b14e-106">\<appDomainManagerType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b14e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b14e-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b14e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7b14e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7b14e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7b14e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b14e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7b14e-110">Attributes</span></span>  
  
|<span data-ttu-id="7b14e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7b14e-111">Attribute</span></span>|<span data-ttu-id="7b14e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7b14e-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="7b14e-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7b14e-113">Required attribute.</span></span> <span data-ttu-id="7b14e-114">Określa nazwę typu, włącznie z przestrzenią nazw, która służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="7b14e-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b14e-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7b14e-115">Child Elements</span></span>  
 <span data-ttu-id="7b14e-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="7b14e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b14e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7b14e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7b14e-118">Element</span><span class="sxs-lookup"><span data-stu-id="7b14e-118">Element</span></span>|<span data-ttu-id="7b14e-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7b14e-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7b14e-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b14e-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7b14e-121">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7b14e-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b14e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b14e-122">Remarks</span></span>  
 <span data-ttu-id="7b14e-123">Aby określić typ Menedżer domeny aplikacji, należy określić zarówno ten element i [ \<appdomainmanagerassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7b14e-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="7b14e-124">Jedną z tych elementów nie zostanie określony, druga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="7b14e-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="7b14e-125">Po załadowaniu domyślnej domeny aplikacji <xref:System.TypeLoadException> jest generowany, jeśli określony typ nie istnieje w zestawie, który jest określony przez [ \<appdomainmanagerassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) elementu; a proces zakończy się niepowodzeniem do początek.</span><span class="sxs-lookup"><span data-stu-id="7b14e-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="7b14e-126">Kiedy określasz typ Menedżera domeny aplikacji dla domyślnej domeny aplikacji, innych domenach aplikacji, utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7b14e-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="7b14e-127">Użyj <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> i <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> właściwości, aby określić typ Menedżera domeny w innej aplikacji dla nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7b14e-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="7b14e-128">Określanie typu Menedżer domeny aplikacji wymaga aplikacja miała pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="7b14e-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="7b14e-129">(Na przykład aplikację działającą na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełne zaufanie <xref:System.TypeLoadException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="7b14e-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="7b14e-130">Format typu i przestrzeni nazw jest tym samym formacie, który służy do <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7b14e-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="7b14e-131">Ten element konfiguracji jest dostępny tylko w programie .NET Framework 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="7b14e-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b14e-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b14e-132">Example</span></span>  
 <span data-ttu-id="7b14e-133">Poniższy przykład pokazuje, jak określić, że Menedżer domeny aplikacji dla domyślnej domeny aplikacji procesu jest `MyMgr` wpisać `AdMgrExample` zestawu.</span><span class="sxs-lookup"><span data-stu-id="7b14e-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b14e-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b14e-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7b14e-135">\<appdomainmanagerassembly — > Element</span><span class="sxs-lookup"><span data-stu-id="7b14e-135">\<appDomainManagerAssembly> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)
- [<span data-ttu-id="7b14e-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7b14e-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="7b14e-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7b14e-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="7b14e-138">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="7b14e-138">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
