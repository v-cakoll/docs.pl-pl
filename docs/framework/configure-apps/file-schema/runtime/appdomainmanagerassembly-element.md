---
title: <appDomainManagerAssembly> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154433"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="680b9-102">\<appDomainManagerAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="680b9-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="680b9-103">Określa zestaw, który udostępnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="680b9-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="680b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="680b9-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="680b9-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="680b9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="680b9-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="680b9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="680b9-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="680b9-107">Attributes</span></span>  
  
|<span data-ttu-id="680b9-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="680b9-108">Attribute</span></span>|<span data-ttu-id="680b9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="680b9-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="680b9-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="680b9-110">Required attribute.</span></span> <span data-ttu-id="680b9-111">Określa nazwę wyświetlaną zestawu, który udostępnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="680b9-111">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="680b9-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="680b9-112">Child Elements</span></span>  
 <span data-ttu-id="680b9-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="680b9-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="680b9-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="680b9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="680b9-115">Element</span><span class="sxs-lookup"><span data-stu-id="680b9-115">Element</span></span>|<span data-ttu-id="680b9-116">Opis</span><span class="sxs-lookup"><span data-stu-id="680b9-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="680b9-117">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="680b9-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="680b9-118">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="680b9-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="680b9-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="680b9-119">Remarks</span></span>  
 <span data-ttu-id="680b9-120">Aby określić typ Menedżera domeny aplikacji, należy określić zarówno ten element, jak i [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="680b9-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="680b9-121">Jeśli jeden z tych elementów nie zostanie określony, drugi zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="680b9-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="680b9-122">Po załadowaniu domyślnej domeny aplikacji <xref:System.TypeLoadException> jest zgłaszany, jeśli określony zestaw nie istnieje lub jeśli zestaw nie zawiera typu określonego przez [\<appDomainManagerType>](appdomainmanagertype-element.md) element; a proces nie zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="680b9-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="680b9-123">Jeśli zestaw zostanie znaleziony, ale informacje o wersji nie są zgodne, <xref:System.IO.FileLoadException> zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="680b9-123">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="680b9-124">W przypadku określenia typu Menedżera domeny aplikacji dla domyślnej domeny aplikacji inne domeny aplikacji utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="680b9-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="680b9-125">Użyj <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> właściwości i, <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Aby określić inny typ Menedżera domeny aplikacji dla nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="680b9-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="680b9-126">Określenie typu Menedżera domeny aplikacji wymaga, aby aplikacja miała pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="680b9-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="680b9-127">(Na przykład aplikacja uruchomiona na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełnego zaufania, <xref:System.TypeLoadException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="680b9-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="680b9-128">Aby uzyskać format nazwy wyświetlanej zestawu, zapoznaj się z <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwością.</span><span class="sxs-lookup"><span data-stu-id="680b9-128">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="680b9-129">Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="680b9-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="680b9-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="680b9-130">Example</span></span>  
 <span data-ttu-id="680b9-131">Poniższy przykład pokazuje, jak określić, że Menedżer domeny aplikacji dla domyślnej domeny aplikacji procesu jest `MyMgr` typem w `AdMgrExample` zestawie.</span><span class="sxs-lookup"><span data-stu-id="680b9-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="680b9-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="680b9-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="680b9-133">\<appDomainManagerType>Postaci</span><span class="sxs-lookup"><span data-stu-id="680b9-133">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="680b9-134">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="680b9-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="680b9-135">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="680b9-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="680b9-136">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="680b9-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
