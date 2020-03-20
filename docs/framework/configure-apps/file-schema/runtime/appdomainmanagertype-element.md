---
title: <appDomainManagerType>, element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154432"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="13b73-102">\<element>> appDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="13b73-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="13b73-103">Określa typ, który służy jako menedżer domeny aplikacji dla domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13b73-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
<span data-ttu-id="13b73-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="13b73-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="13b73-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="13b73-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="13b73-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>typu>aplikacji DomainManagerType**</span><span class="sxs-lookup"><span data-stu-id="13b73-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13b73-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="13b73-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13b73-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="13b73-108">Attributes and Elements</span></span>  
 <span data-ttu-id="13b73-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="13b73-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13b73-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="13b73-110">Attributes</span></span>  
  
|<span data-ttu-id="13b73-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="13b73-111">Attribute</span></span>|<span data-ttu-id="13b73-112">Opis</span><span class="sxs-lookup"><span data-stu-id="13b73-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="13b73-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="13b73-113">Required attribute.</span></span> <span data-ttu-id="13b73-114">Określa nazwę typu, w tym obszar nazw, który służy jako menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="13b73-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13b73-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="13b73-115">Child Elements</span></span>  
 <span data-ttu-id="13b73-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="13b73-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13b73-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="13b73-117">Parent Elements</span></span>  
  
|<span data-ttu-id="13b73-118">Element</span><span class="sxs-lookup"><span data-stu-id="13b73-118">Element</span></span>|<span data-ttu-id="13b73-119">Opis</span><span class="sxs-lookup"><span data-stu-id="13b73-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="13b73-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13b73-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="13b73-121">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="13b73-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13b73-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13b73-122">Remarks</span></span>  
 <span data-ttu-id="13b73-123">Aby określić typ menedżera domeny aplikacji, należy określić zarówno ten element, jak i [ \<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="13b73-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="13b73-124">Jeśli którykolwiek z tych elementów nie jest określony, drugi jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="13b73-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="13b73-125">Po załadowaniu domyślnej <xref:System.TypeLoadException> domeny aplikacji jest generowany, jeśli określony typ nie istnieje w zestawie, który jest określony przez [ \<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; i proces nie uruchamia się.</span><span class="sxs-lookup"><span data-stu-id="13b73-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="13b73-126">Po określeniu typu menedżera domeny aplikacji dla domyślnej domeny aplikacji inne domeny aplikacji utworzone z domyślnej domeny aplikacji dziedziczą typ menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13b73-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="13b73-127">Użyj <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> właściwości <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> i, aby określić inny typ menedżera domeny aplikacji dla nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13b73-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="13b73-128">Określenie typu menedżera domeny aplikacji wymaga pełnego zaufania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13b73-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="13b73-129">(Na przykład aplikacja uruchomiona na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełnego <xref:System.TypeLoadException> zaufania, a jest generowany.</span><span class="sxs-lookup"><span data-stu-id="13b73-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="13b73-130">Format typu i obszaru nazw jest tym samym formatem, który jest używany dla <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="13b73-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="13b73-131">Ten element konfiguracji jest dostępny tylko w programie .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="13b73-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13b73-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="13b73-132">Example</span></span>  
 <span data-ttu-id="13b73-133">Poniższy przykład pokazuje, jak określić, że menedżer domeny aplikacji `MyMgr` dla domyślnej domeny aplikacji procesu jest typem `AdMgrExample` w zestawie.</span><span class="sxs-lookup"><span data-stu-id="13b73-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13b73-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13b73-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="13b73-135">\<appDomainManagerAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="13b73-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="13b73-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="13b73-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="13b73-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="13b73-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="13b73-138">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="13b73-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
