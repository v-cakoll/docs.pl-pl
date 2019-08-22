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
ms.openlocfilehash: 7c8f8744d3ef1ca30eb05a4c8c3290d8a514714b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663512"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="aacf0-102">\<publisherPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="aacf0-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="aacf0-103">Określa, czy środowisko uruchomieniowe stosuje zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="aacf0-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="aacf0-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="aacf0-104">\<configuration></span></span>  
<span data-ttu-id="aacf0-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="aacf0-105">\<runtime></span></span>  
<span data-ttu-id="aacf0-106">\<> zestawubinding</span><span class="sxs-lookup"><span data-stu-id="aacf0-106">\<assemblyBinding></span></span>  
<span data-ttu-id="aacf0-107">\<> dependentAssembly</span><span class="sxs-lookup"><span data-stu-id="aacf0-107">\<dependentAssembly></span></span>  
<span data-ttu-id="aacf0-108">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="aacf0-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aacf0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="aacf0-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aacf0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aacf0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aacf0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aacf0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aacf0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aacf0-112">Attributes</span></span>  
  
|<span data-ttu-id="aacf0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aacf0-113">Attribute</span></span>|<span data-ttu-id="aacf0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="aacf0-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="aacf0-115">Określa, czy mają być stosowane zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="aacf0-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="aacf0-116">Zastosuj atrybut</span><span class="sxs-lookup"><span data-stu-id="aacf0-116">apply Attribute</span></span>  
  
|<span data-ttu-id="aacf0-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="aacf0-117">Value</span></span>|<span data-ttu-id="aacf0-118">Opis</span><span class="sxs-lookup"><span data-stu-id="aacf0-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="aacf0-119">Stosuje zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="aacf0-119">Applies publisher policy.</span></span> <span data-ttu-id="aacf0-120">To jest ustawienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="aacf0-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="aacf0-121">Nie stosuje zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="aacf0-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aacf0-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aacf0-122">Child Elements</span></span>  
 <span data-ttu-id="aacf0-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="aacf0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aacf0-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aacf0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="aacf0-125">Element</span><span class="sxs-lookup"><span data-stu-id="aacf0-125">Element</span></span>|<span data-ttu-id="aacf0-126">Opis</span><span class="sxs-lookup"><span data-stu-id="aacf0-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aacf0-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aacf0-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="aacf0-128">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="aacf0-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aacf0-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aacf0-129">Remarks</span></span>  
 <span data-ttu-id="aacf0-130">Gdy dostawca składnika zwalnia nową wersję zestawu, dostawca może uwzględnić zasady wydawcy, aby aplikacje używające starej wersji używały teraz nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="aacf0-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="aacf0-131">Aby określić, czy zastosować zasady wydawcy dla określonego zestawu, umieść  **\<element publisherPolicy Apply >** w  **\<elemencie dependentAssembly >** .</span><span class="sxs-lookup"><span data-stu-id="aacf0-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="aacf0-132">Ustawieniem domyślnym dla atrybutu **apply** jest **tak**.</span><span class="sxs-lookup"><span data-stu-id="aacf0-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="aacf0-133">Ustawienie atrybutu **Zastosuj** do **nie** zastępuje żadnych poprzednich ustawień **tak** dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="aacf0-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="aacf0-134">Uprawnienie jest wymagane, aby aplikacja jawnie ignorował zasady wydawcy przy użyciu [ \<elementu publisherPolicy Apply Apply = "No"/>](publisherpolicy-element.md) w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aacf0-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="aacf0-135">Uprawnienie jest udzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagi <xref:System.Security.Permissions.SecurityPermission>na.</span><span class="sxs-lookup"><span data-stu-id="aacf0-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="aacf0-136">Aby uzyskać więcej informacji, zobacz [uprawnienia zabezpieczeń przekierowania powiązania zestawu](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="aacf0-136">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aacf0-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="aacf0-137">Example</span></span>  
 <span data-ttu-id="aacf0-138">Poniższy przykład powoduje wyłączenie zasad wydawcy dla zestawu `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="aacf0-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aacf0-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aacf0-139">See also</span></span>

- [<span data-ttu-id="aacf0-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="aacf0-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="aacf0-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="aacf0-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="aacf0-142">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="aacf0-142">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="aacf0-143">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="aacf0-143">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
