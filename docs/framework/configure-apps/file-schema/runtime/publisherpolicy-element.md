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
ms.openlocfilehash: 2cc3b7220fe34f5dc049a3da71b160a88f82fdb1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746101"
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="eaa19-102">&lt;publisherPolicy&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="eaa19-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="eaa19-103">Określa, czy środowisko wykonawcze ma zastosowanie zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="eaa19-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="eaa19-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="eaa19-104">\<configuration></span></span>  
<span data-ttu-id="eaa19-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="eaa19-105">\<runtime></span></span>  
<span data-ttu-id="eaa19-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="eaa19-106">\<assemblyBinding></span></span>  
<span data-ttu-id="eaa19-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="eaa19-107">\<dependentAssembly></span></span>  
<span data-ttu-id="eaa19-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="eaa19-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa19-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="eaa19-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eaa19-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eaa19-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eaa19-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eaa19-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eaa19-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eaa19-112">Attributes</span></span>  
  
|<span data-ttu-id="eaa19-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="eaa19-113">Attribute</span></span>|<span data-ttu-id="eaa19-114">Opis</span><span class="sxs-lookup"><span data-stu-id="eaa19-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="eaa19-115">Określa, czy zastosować zasady wydawcy.</span><span class="sxs-lookup"><span data-stu-id="eaa19-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="eaa19-116">zastosowanie atrybutu</span><span class="sxs-lookup"><span data-stu-id="eaa19-116">apply Attribute</span></span>  
  
|<span data-ttu-id="eaa19-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="eaa19-117">Value</span></span>|<span data-ttu-id="eaa19-118">Opis</span><span class="sxs-lookup"><span data-stu-id="eaa19-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="eaa19-119">Zastosowanie zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="eaa19-119">Applies publisher policy.</span></span> <span data-ttu-id="eaa19-120">To jest ustawienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="eaa19-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="eaa19-121">Nie ma zastosowania zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="eaa19-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eaa19-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eaa19-122">Child Elements</span></span>  
 <span data-ttu-id="eaa19-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="eaa19-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eaa19-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eaa19-124">Parent Elements</span></span>  
  
|<span data-ttu-id="eaa19-125">Element</span><span class="sxs-lookup"><span data-stu-id="eaa19-125">Element</span></span>|<span data-ttu-id="eaa19-126">Opis</span><span class="sxs-lookup"><span data-stu-id="eaa19-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eaa19-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eaa19-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="eaa19-128">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="eaa19-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaa19-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eaa19-129">Remarks</span></span>  
 <span data-ttu-id="eaa19-130">Jeśli dostawcy składnika udostępnia nową wersję zestawu, dostawcy mogą być zasad wydawcy, aplikacje używające starą wersję teraz używać nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="eaa19-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="eaa19-131">Aby określić, czy zastosować zasady wydawcy dla danego zestawu, umieść  **\<publisherPolicy >** element  **\<dependentAssembly >** elementu.</span><span class="sxs-lookup"><span data-stu-id="eaa19-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="eaa19-132">Ustawieniem domyślnym dla **zastosować** atrybutu **tak**.</span><span class="sxs-lookup"><span data-stu-id="eaa19-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="eaa19-133">Ustawienie **zastosować** atrybutu **nie** zastąpienia żadnych poprzednich **tak** ustawienia dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="eaa19-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="eaa19-134">Uprawnienie jest wymagane dla aplikacji, aby jawnie Ignoruj przy użyciu zasad wydawcy [ \<zastosować publisherPolicy = "nie" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eaa19-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="eaa19-135">Uprawnienie zostanie udzielone przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> Flaga na <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="eaa19-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="eaa19-136">Aby uzyskać więcej informacji, zobacz [uprawnienie zabezpieczeń przekierowania powiązania zestawu](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="eaa19-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaa19-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="eaa19-137">Example</span></span>  
 <span data-ttu-id="eaa19-138">Poniższy przykład powoduje wyłączenie zasad wydawcy dla zestawu, `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="eaa19-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eaa19-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eaa19-139">See Also</span></span>  
 [<span data-ttu-id="eaa19-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="eaa19-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="eaa19-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eaa19-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="eaa19-142">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="eaa19-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="eaa19-143">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="eaa19-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
