---
title: "&lt;bypasstrustedappstrongnames —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0343aef083076249325b9577f90964d066867f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a><span data-ttu-id="495f3-102">&lt;bypasstrustedappstrongnames —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="495f3-102">&lt;bypassTrustedAppStrongNames&gt; Element</span></span>
<span data-ttu-id="495f3-103">Określa, czy pominąć weryfikacji silnych nazw zestawów pełnego zaufania, które są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="495f3-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="495f3-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="495f3-104">\<configuration></span></span>  
<span data-ttu-id="495f3-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="495f3-105">\<runtime></span></span>  
<span data-ttu-id="495f3-106">\<bypasstrustedappstrongnames — ></span><span class="sxs-lookup"><span data-stu-id="495f3-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="495f3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="495f3-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="495f3-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="495f3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="495f3-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="495f3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="495f3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="495f3-110">Attributes</span></span>  
  
|<span data-ttu-id="495f3-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="495f3-111">Attribute</span></span>|<span data-ttu-id="495f3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="495f3-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="495f3-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="495f3-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="495f3-114">Określa, czy jest włączona funkcja obejścia, która pozwala uniknąć weryfikacji silnej nazwy zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="495f3-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="495f3-115">Gdy ta funkcja jest włączona, silne nazwy nie zostaną sprawdzone pod kątem poprawności, gdy zestaw jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="495f3-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="495f3-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="495f3-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="495f3-117">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="495f3-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="495f3-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="495f3-118">Value</span></span>|<span data-ttu-id="495f3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="495f3-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="495f3-120">Podpisy silnej nazwy zestawów pełnego zaufania nie są weryfikowane podczas zestawy są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="495f3-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="495f3-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="495f3-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="495f3-122">Podpisy silnej nazwy zestawów pełnego zaufania są weryfikowane podczas zestawy są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="495f3-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="495f3-123">Podpis silnej nazwy jest sprawdzany tylko pod kątem poprawności podpisu; nie była porównywana do innego silnej nazwy pod kątem dopasowania.</span><span class="sxs-lookup"><span data-stu-id="495f3-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="495f3-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="495f3-124">Child Elements</span></span>  
 <span data-ttu-id="495f3-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="495f3-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="495f3-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="495f3-126">Parent Elements</span></span>  
  
|<span data-ttu-id="495f3-127">Element</span><span class="sxs-lookup"><span data-stu-id="495f3-127">Element</span></span>|<span data-ttu-id="495f3-128">Opis</span><span class="sxs-lookup"><span data-stu-id="495f3-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="495f3-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="495f3-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="495f3-130">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="495f3-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="495f3-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="495f3-131">Remarks</span></span>  
 <span data-ttu-id="495f3-132">Funkcja pomijania silnej nazwy pozwala uniknąć obciążenie weryfikacji podpisu silnej nazwy zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="495f3-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="495f3-133">Funkcja pomijania ma zastosowanie do dowolnego zestawu, który jest podpisany przy użyciu silnej nazwy i ma następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="495f3-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="495f3-134">Pełni zaufany bez <xref:System.Security.Policy.StrongName> dowód (na przykład `MyComputer` strefy dowód).</span><span class="sxs-lookup"><span data-stu-id="495f3-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="495f3-135">Załadowane w pełni zaufany <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="495f3-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="495f3-136">Załadowane z lokalizacji w <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości tego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="495f3-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="495f3-137">Nie podpisywany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="495f3-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="495f3-138">Jeśli funkcja pomijania została wyłączona dla wszystkich aplikacji na komputerze przy użyciu klucza rejestru, to ustawienie pliku konfiguracji nie ma żadnego skutku.</span><span class="sxs-lookup"><span data-stu-id="495f3-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="495f3-139">Aby uzyskać więcej informacji, zobacz [porady: wyłączanie funkcji pomijania silnej nazwy](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="495f3-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="495f3-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="495f3-140">Example</span></span>  
 <span data-ttu-id="495f3-141">Poniższy przykład pokazuje, jak do określania zachowania, która weryfikuje podpisu silnej nazwy zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="495f3-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="495f3-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="495f3-142">See Also</span></span>  
 [<span data-ttu-id="495f3-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="495f3-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="495f3-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="495f3-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="495f3-145">Instrukcje: wyłączanie funkcji pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="495f3-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
