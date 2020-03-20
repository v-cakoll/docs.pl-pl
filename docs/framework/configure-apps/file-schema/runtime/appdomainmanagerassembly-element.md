---
title: <appDomainManagerAssembly>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154433"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="e85fd-102">\<appDomainManagerAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="e85fd-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="e85fd-103">Określa zestaw, który udostępnia menedżera domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="e85fd-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="e85fd-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e85fd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e85fd-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e85fd-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e85fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span><span class="sxs-lookup"><span data-stu-id="e85fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85fd-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e85fd-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e85fd-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e85fd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e85fd-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e85fd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e85fd-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e85fd-110">Attributes</span></span>  
  
|<span data-ttu-id="e85fd-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e85fd-111">Attribute</span></span>|<span data-ttu-id="e85fd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e85fd-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="e85fd-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="e85fd-113">Required attribute.</span></span> <span data-ttu-id="e85fd-114">Określa wyświetlaną nazwę zestawu, który udostępnia menedżera domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="e85fd-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e85fd-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e85fd-115">Child Elements</span></span>  
 <span data-ttu-id="e85fd-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="e85fd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e85fd-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e85fd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e85fd-118">Element</span><span class="sxs-lookup"><span data-stu-id="e85fd-118">Element</span></span>|<span data-ttu-id="e85fd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e85fd-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e85fd-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e85fd-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e85fd-121">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e85fd-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e85fd-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e85fd-122">Remarks</span></span>  
 <span data-ttu-id="e85fd-123">Aby określić typ menedżera domeny aplikacji, należy określić zarówno ten element, jak i [ \<element>appDomainManagerType.](appdomainmanagertype-element.md)</span><span class="sxs-lookup"><span data-stu-id="e85fd-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="e85fd-124">Jeśli którykolwiek z tych elementów nie jest określony, drugi jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="e85fd-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="e85fd-125">Po załadowaniu domyślnej <xref:System.TypeLoadException> domeny aplikacji jest generowany, jeśli określony zestaw nie istnieje lub jeśli zestaw nie zawiera typu określonego przez [ \<appDomainManagerType>](appdomainmanagertype-element.md) element; i proces nie uruchamia się.</span><span class="sxs-lookup"><span data-stu-id="e85fd-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="e85fd-126">Jeśli zestaw zostanie znaleziony, ale informacje o <xref:System.IO.FileLoadException> wersji nie są zgodne, a jest generowany.</span><span class="sxs-lookup"><span data-stu-id="e85fd-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="e85fd-127">Po określeniu typu menedżera domeny aplikacji dla domyślnej domeny aplikacji inne domeny aplikacji utworzone z domyślnej domeny aplikacji dziedziczą typ menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e85fd-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="e85fd-128">Użyj <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> właściwości <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> i, aby określić inny typ menedżera domeny aplikacji dla nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e85fd-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="e85fd-129">Określenie typu menedżera domeny aplikacji wymaga pełnego zaufania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e85fd-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="e85fd-130">(Na przykład aplikacja uruchomiona na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełnego <xref:System.TypeLoadException> zaufania, a jest generowany.</span><span class="sxs-lookup"><span data-stu-id="e85fd-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="e85fd-131">Aby uzyskać format nazwy wyświetlanej <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> zestawu, zobacz właściwość.</span><span class="sxs-lookup"><span data-stu-id="e85fd-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="e85fd-132">Ten element konfiguracji jest dostępny tylko w programie .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="e85fd-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e85fd-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="e85fd-133">Example</span></span>  
 <span data-ttu-id="e85fd-134">Poniższy przykład pokazuje, jak określić, że menedżer domeny aplikacji `MyMgr` dla domyślnej domeny aplikacji procesu jest typem `AdMgrExample` w zestawie.</span><span class="sxs-lookup"><span data-stu-id="e85fd-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e85fd-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e85fd-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e85fd-136">\<element>> appDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="e85fd-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="e85fd-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e85fd-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e85fd-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e85fd-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e85fd-139">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="e85fd-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
