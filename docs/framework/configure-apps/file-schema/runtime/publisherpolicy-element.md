---
title: '&lt;publisherPolicy&gt; — Element'
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
ms.openlocfilehash: cc33405d8fbb3e5f66be9ea2deb4545bd4ca0971
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620594"
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="d10cf-102">&lt;publisherPolicy&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="d10cf-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="d10cf-103">Określa, czy środowisko uruchomieniowe mają zastosowanie zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="d10cf-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="d10cf-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d10cf-104">\<configuration></span></span>  
<span data-ttu-id="d10cf-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="d10cf-105">\<runtime></span></span>  
<span data-ttu-id="d10cf-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="d10cf-106">\<assemblyBinding></span></span>  
<span data-ttu-id="d10cf-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="d10cf-107">\<dependentAssembly></span></span>  
<span data-ttu-id="d10cf-108">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="d10cf-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d10cf-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d10cf-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d10cf-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d10cf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d10cf-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d10cf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d10cf-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d10cf-112">Attributes</span></span>  
  
|<span data-ttu-id="d10cf-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d10cf-113">Attribute</span></span>|<span data-ttu-id="d10cf-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d10cf-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="d10cf-115">Określa, czy zastosować zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="d10cf-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="d10cf-116">Zastosuj atrybut</span><span class="sxs-lookup"><span data-stu-id="d10cf-116">apply Attribute</span></span>  
  
|<span data-ttu-id="d10cf-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="d10cf-117">Value</span></span>|<span data-ttu-id="d10cf-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d10cf-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="d10cf-119">Zastosowanie zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="d10cf-119">Applies publisher policy.</span></span> <span data-ttu-id="d10cf-120">To jest ustawienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="d10cf-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="d10cf-121">Nie ma zastosowania zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="d10cf-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d10cf-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d10cf-122">Child Elements</span></span>  
 <span data-ttu-id="d10cf-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="d10cf-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d10cf-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d10cf-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d10cf-125">Element</span><span class="sxs-lookup"><span data-stu-id="d10cf-125">Element</span></span>|<span data-ttu-id="d10cf-126">Opis</span><span class="sxs-lookup"><span data-stu-id="d10cf-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d10cf-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d10cf-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d10cf-128">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d10cf-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d10cf-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d10cf-129">Remarks</span></span>  
 <span data-ttu-id="d10cf-130">Jeśli dostawcy składników udostępnia nową wersję zestawu, dostawcy mogą być zasad wydawcy, dzięki czemu aplikacje, które używają starej wersji teraz używać nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="d10cf-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="d10cf-131">Aby określić, czy do zastosowania zasad wydawcy dla określonego zestawu, należy umieścić  **\<publisherPolicy >** element  **\<dependentAssembly >** elementu.</span><span class="sxs-lookup"><span data-stu-id="d10cf-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="d10cf-132">Ustawieniem domyślnym dla **zastosować** atrybut jest **tak**.</span><span class="sxs-lookup"><span data-stu-id="d10cf-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="d10cf-133">Ustawienie **zastosować** atrybutu **nie** zastępuje wszystkie poprzednie **tak** ustawienia zestawu.</span><span class="sxs-lookup"><span data-stu-id="d10cf-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="d10cf-134">Uprawnienie jest wymagane dla aplikacji, aby jawnie Ignoruj przy użyciu zasad wydawcy [ \<zastosować publisherPolicy = "no" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d10cf-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="d10cf-135">To uprawnienie jest przydzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagą <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="d10cf-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="d10cf-136">Aby uzyskać więcej informacji, zobacz [uprawnienie zabezpieczeń przekierowania powiązania zestawu](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="d10cf-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d10cf-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="d10cf-137">Example</span></span>  
 <span data-ttu-id="d10cf-138">Poniższy przykład powoduje wyłączenie zasad wydawcy dla zestawu, `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="d10cf-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d10cf-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d10cf-139">See also</span></span>
- [<span data-ttu-id="d10cf-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d10cf-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="d10cf-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d10cf-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="d10cf-142">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d10cf-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d10cf-143">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="d10cf-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
