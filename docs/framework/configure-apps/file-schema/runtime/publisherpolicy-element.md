---
title: <publisherPolicy>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc206e584440778858e61fc0bab51fc8ffa2009a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252379"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="b8483-102">\<publisherPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="b8483-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="b8483-103">Określa, czy środowisko uruchomieniowe stosuje zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="b8483-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
<span data-ttu-id="b8483-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8483-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b8483-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8483-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b8483-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zestawubinding**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="b8483-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="b8483-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8483-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="b8483-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<publisherPolicy Apply >**</span><span class="sxs-lookup"><span data-stu-id="b8483-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8483-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8483-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8483-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b8483-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b8483-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b8483-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8483-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b8483-112">Attributes</span></span>  
  
|<span data-ttu-id="b8483-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b8483-113">Attribute</span></span>|<span data-ttu-id="b8483-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b8483-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="b8483-115">Określa, czy mają być stosowane zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="b8483-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="b8483-116">Zastosuj atrybut</span><span class="sxs-lookup"><span data-stu-id="b8483-116">apply Attribute</span></span>  
  
|<span data-ttu-id="b8483-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="b8483-117">Value</span></span>|<span data-ttu-id="b8483-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b8483-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="b8483-119">Stosuje zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="b8483-119">Applies publisher policy.</span></span> <span data-ttu-id="b8483-120">To jest ustawienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="b8483-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="b8483-121">Nie stosuje zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="b8483-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8483-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b8483-122">Child Elements</span></span>  

<span data-ttu-id="b8483-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="b8483-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8483-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b8483-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b8483-125">Element</span><span class="sxs-lookup"><span data-stu-id="b8483-125">Element</span></span>|<span data-ttu-id="b8483-126">Opis</span><span class="sxs-lookup"><span data-stu-id="b8483-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="b8483-127">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="b8483-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="b8483-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8483-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="b8483-129">Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b8483-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="b8483-130">Użyj jednego `<dependentAssembly>` elementu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b8483-130">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="b8483-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b8483-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8483-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8483-132">Remarks</span></span>  
 <span data-ttu-id="b8483-133">Gdy dostawca składnika zwalnia nową wersję zestawu, dostawca może uwzględnić zasady wydawcy, aby aplikacje używające starej wersji używały teraz nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="b8483-133">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="b8483-134">Aby określić, czy zastosować zasady wydawcy dla określonego zestawu, umieść  **\<element publisherPolicy Apply >** w  **\<elemencie dependentAssembly >** .</span><span class="sxs-lookup"><span data-stu-id="b8483-134">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="b8483-135">Ustawieniem domyślnym dla atrybutu **apply** jest **tak**.</span><span class="sxs-lookup"><span data-stu-id="b8483-135">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="b8483-136">Ustawienie atrybutu **Zastosuj** do **nie** zastępuje żadnych poprzednich ustawień **tak** dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="b8483-136">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="b8483-137">Uprawnienie jest wymagane, aby aplikacja jawnie ignorował zasady wydawcy przy użyciu [ \<elementu publisherPolicy Apply Apply = "No"/>](publisherpolicy-element.md) w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b8483-137">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="b8483-138">Uprawnienie jest udzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagi <xref:System.Security.Permissions.SecurityPermission>na.</span><span class="sxs-lookup"><span data-stu-id="b8483-138">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="b8483-139">Aby uzyskać więcej informacji, zobacz [uprawnienia zabezpieczeń przekierowania powiązania zestawu](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="b8483-139">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8483-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8483-140">Example</span></span>  
 <span data-ttu-id="b8483-141">Poniższy przykład powoduje wyłączenie zasad wydawcy dla zestawu `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="b8483-141">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8483-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8483-142">See also</span></span>

- [<span data-ttu-id="b8483-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b8483-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b8483-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b8483-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b8483-145">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b8483-145">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b8483-146">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="b8483-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
