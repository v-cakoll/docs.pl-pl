---
title: <appDomainManagerType> Element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154432"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="bed82-102">\<appDomainManagerType> Element</span><span class="sxs-lookup"><span data-stu-id="bed82-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="bed82-103">Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bed82-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a><span data-ttu-id="bed82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bed82-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bed82-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bed82-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bed82-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bed82-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bed82-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bed82-107">Attributes</span></span>  
  
|<span data-ttu-id="bed82-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bed82-108">Attribute</span></span>|<span data-ttu-id="bed82-109">Opis</span><span class="sxs-lookup"><span data-stu-id="bed82-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="bed82-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="bed82-110">Required attribute.</span></span> <span data-ttu-id="bed82-111">Określa nazwę typu, w tym przestrzeń nazw, która służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="bed82-111">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bed82-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bed82-112">Child Elements</span></span>  
 <span data-ttu-id="bed82-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="bed82-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bed82-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bed82-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bed82-115">Element</span><span class="sxs-lookup"><span data-stu-id="bed82-115">Element</span></span>|<span data-ttu-id="bed82-116">Opis</span><span class="sxs-lookup"><span data-stu-id="bed82-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bed82-117">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bed82-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bed82-118">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bed82-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bed82-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bed82-119">Remarks</span></span>  
 <span data-ttu-id="bed82-120">Aby określić typ Menedżera domeny aplikacji, należy określić zarówno ten element, jak i [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="bed82-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="bed82-121">Jeśli jeden z tych elementów nie zostanie określony, drugi zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="bed82-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="bed82-122">W przypadku załadowania domyślnej domeny aplikacji <xref:System.TypeLoadException> jest zgłaszany, jeśli określony typ nie istnieje w zestawie, który jest określony przez [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; a proces nie zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="bed82-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="bed82-123">W przypadku określenia typu Menedżera domeny aplikacji dla domyślnej domeny aplikacji inne domeny aplikacji utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bed82-123">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="bed82-124">Użyj <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> właściwości i, <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Aby określić inny typ Menedżera domeny aplikacji dla nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bed82-124">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="bed82-125">Określenie typu Menedżera domeny aplikacji wymaga, aby aplikacja miała pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="bed82-125">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="bed82-126">(Na przykład aplikacja uruchomiona na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełnego zaufania, <xref:System.TypeLoadException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="bed82-126">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="bed82-127">Format typu i przestrzeni nazw jest tym samym formatem, który jest używany dla <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bed82-127">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="bed82-128">Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="bed82-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bed82-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="bed82-129">Example</span></span>  
 <span data-ttu-id="bed82-130">Poniższy przykład pokazuje, jak określić, że Menedżer domeny aplikacji dla domyślnej domeny aplikacji procesu jest `MyMgr` typem w `AdMgrExample` zestawie.</span><span class="sxs-lookup"><span data-stu-id="bed82-130">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bed82-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bed82-131">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bed82-132">\<appDomainManagerAssembly>Postaci</span><span class="sxs-lookup"><span data-stu-id="bed82-132">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="bed82-133">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="bed82-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bed82-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bed82-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bed82-135">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="bed82-135">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
