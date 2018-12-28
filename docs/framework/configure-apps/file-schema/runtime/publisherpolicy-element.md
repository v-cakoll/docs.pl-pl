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
ms.openlocfilehash: 4c81b403fa4d633428946d36960d5df32df76d21
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613781"
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="85407-102">&lt;publisherPolicy&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="85407-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="85407-103">Określa, czy środowisko uruchomieniowe mają zastosowanie zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="85407-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="85407-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="85407-104">\<configuration></span></span>  
<span data-ttu-id="85407-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="85407-105">\<runtime></span></span>  
<span data-ttu-id="85407-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="85407-106">\<assemblyBinding></span></span>  
<span data-ttu-id="85407-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="85407-107">\<dependentAssembly></span></span>  
<span data-ttu-id="85407-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="85407-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85407-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="85407-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85407-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="85407-110">Attributes and Elements</span></span>  
 <span data-ttu-id="85407-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="85407-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85407-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="85407-112">Attributes</span></span>  
  
|<span data-ttu-id="85407-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="85407-113">Attribute</span></span>|<span data-ttu-id="85407-114">Opis</span><span class="sxs-lookup"><span data-stu-id="85407-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="85407-115">Określa, czy zastosować zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="85407-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="85407-116">Zastosuj atrybut</span><span class="sxs-lookup"><span data-stu-id="85407-116">apply Attribute</span></span>  
  
|<span data-ttu-id="85407-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="85407-117">Value</span></span>|<span data-ttu-id="85407-118">Opis</span><span class="sxs-lookup"><span data-stu-id="85407-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="85407-119">Zastosowanie zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="85407-119">Applies publisher policy.</span></span> <span data-ttu-id="85407-120">To jest ustawienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="85407-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="85407-121">Nie ma zastosowania zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="85407-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85407-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="85407-122">Child Elements</span></span>  
 <span data-ttu-id="85407-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="85407-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85407-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="85407-124">Parent Elements</span></span>  
  
|<span data-ttu-id="85407-125">Element</span><span class="sxs-lookup"><span data-stu-id="85407-125">Element</span></span>|<span data-ttu-id="85407-126">Opis</span><span class="sxs-lookup"><span data-stu-id="85407-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="85407-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85407-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="85407-128">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="85407-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85407-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85407-129">Remarks</span></span>  
 <span data-ttu-id="85407-130">Jeśli dostawcy składników udostępnia nową wersję zestawu, dostawcy mogą być zasad wydawcy, dzięki czemu aplikacje, które używają starej wersji teraz używać nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="85407-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="85407-131">Aby określić, czy do zastosowania zasad wydawcy dla określonego zestawu, należy umieścić  **\<publisherPolicy >** element  **\<dependentAssembly >** elementu.</span><span class="sxs-lookup"><span data-stu-id="85407-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="85407-132">Ustawieniem domyślnym dla **zastosować** atrybut jest **tak**.</span><span class="sxs-lookup"><span data-stu-id="85407-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="85407-133">Ustawienie **zastosować** atrybutu **nie** zastępuje wszystkie poprzednie **tak** ustawienia zestawu.</span><span class="sxs-lookup"><span data-stu-id="85407-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="85407-134">Uprawnienie jest wymagane dla aplikacji, aby jawnie Ignoruj przy użyciu zasad wydawcy [ \<zastosować publisherPolicy = "no" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85407-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="85407-135">To uprawnienie jest przydzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagą <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="85407-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="85407-136">Aby uzyskać więcej informacji, zobacz [uprawnienie zabezpieczeń przekierowania powiązania zestawu](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="85407-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85407-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="85407-137">Example</span></span>  
 <span data-ttu-id="85407-138">Poniższy przykład powoduje wyłączenie zasad wydawcy dla zestawu, `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="85407-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="85407-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85407-139">See Also</span></span>  
- [<span data-ttu-id="85407-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="85407-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="85407-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="85407-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="85407-142">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="85407-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [<span data-ttu-id="85407-143">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="85407-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
