---
title: <appDomainManagerType> Element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: bae4aa39f9c43480ac2ef984f78834b68646742d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118244"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="43296-102">\<element > appDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="43296-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="43296-103">Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43296-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
<span data-ttu-id="43296-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="43296-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43296-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="43296-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="43296-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerType >**</span><span class="sxs-lookup"><span data-stu-id="43296-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43296-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="43296-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43296-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="43296-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43296-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="43296-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43296-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="43296-110">Attributes</span></span>  
  
|<span data-ttu-id="43296-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="43296-111">Attribute</span></span>|<span data-ttu-id="43296-112">Opis</span><span class="sxs-lookup"><span data-stu-id="43296-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="43296-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="43296-113">Required attribute.</span></span> <span data-ttu-id="43296-114">Określa nazwę typu, w tym przestrzeń nazw, która służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="43296-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43296-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="43296-115">Child Elements</span></span>  
 <span data-ttu-id="43296-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="43296-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43296-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="43296-117">Parent Elements</span></span>  
  
|<span data-ttu-id="43296-118">Element</span><span class="sxs-lookup"><span data-stu-id="43296-118">Element</span></span>|<span data-ttu-id="43296-119">Opis</span><span class="sxs-lookup"><span data-stu-id="43296-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43296-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43296-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="43296-121">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="43296-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43296-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43296-122">Remarks</span></span>  
 <span data-ttu-id="43296-123">Aby określić typ Menedżera domeny aplikacji, należy określić zarówno element, jak i [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) .</span><span class="sxs-lookup"><span data-stu-id="43296-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="43296-124">Jeśli jeden z tych elementów nie zostanie określony, drugi zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="43296-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="43296-125">Podczas ładowania domyślnej domeny aplikacji <xref:System.TypeLoadException> jest zgłaszany, jeśli określony typ nie istnieje w zestawie, który jest określony przez [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) elementu; proces kończy się niepowodzeniem i nie można go uruchomić.</span><span class="sxs-lookup"><span data-stu-id="43296-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="43296-126">W przypadku określenia typu Menedżera domeny aplikacji dla domyślnej domeny aplikacji inne domeny aplikacji utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43296-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="43296-127">Użyj właściwości <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> i <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>, aby określić inny typ Menedżera domeny aplikacji dla nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43296-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="43296-128">Określenie typu Menedżera domeny aplikacji wymaga, aby aplikacja miała pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="43296-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="43296-129">(Na przykład aplikacja uruchomiona na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełnego zaufania, zostanie zgłoszony <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="43296-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="43296-130">Format typu i przestrzeni nazw jest tym samym formatem, który jest używany dla właściwości <xref:System.Type.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="43296-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="43296-131">Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="43296-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43296-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="43296-132">Example</span></span>  
 <span data-ttu-id="43296-133">Poniższy przykład pokazuje, jak określić, że Menedżer domeny aplikacji dla domyślnej domeny aplikacji procesu jest typem `MyMgr` w zestawie `AdMgrExample`.</span><span class="sxs-lookup"><span data-stu-id="43296-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43296-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43296-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="43296-135">\<element > appDomainManagerAssembly</span><span class="sxs-lookup"><span data-stu-id="43296-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="43296-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="43296-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="43296-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="43296-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="43296-138">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="43296-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
