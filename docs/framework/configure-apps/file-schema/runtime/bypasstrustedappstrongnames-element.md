---
title: '&lt;bypasstrustedappstrongnames —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6988be28e3129748ee7f7996a66c728ccde3c70b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a><span data-ttu-id="1560c-102">&lt;bypasstrustedappstrongnames —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="1560c-102">&lt;bypassTrustedAppStrongNames&gt; Element</span></span>
<span data-ttu-id="1560c-103">Określa, czy pominąć weryfikacji silnych nazw zestawów pełnego zaufania, które są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1560c-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="1560c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1560c-104">\<configuration></span></span>  
<span data-ttu-id="1560c-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="1560c-105">\<runtime></span></span>  
<span data-ttu-id="1560c-106">\<bypasstrustedappstrongnames — ></span><span class="sxs-lookup"><span data-stu-id="1560c-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1560c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1560c-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1560c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1560c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1560c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1560c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1560c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1560c-110">Attributes</span></span>  
  
|<span data-ttu-id="1560c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1560c-111">Attribute</span></span>|<span data-ttu-id="1560c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1560c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1560c-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1560c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1560c-114">Określa, czy jest włączona funkcja obejścia, która pozwala uniknąć weryfikacji silnej nazwy zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="1560c-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="1560c-115">Gdy ta funkcja jest włączona, silne nazwy nie zostaną sprawdzone pod kątem poprawności, gdy zestaw jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="1560c-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="1560c-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="1560c-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1560c-117">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="1560c-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="1560c-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="1560c-118">Value</span></span>|<span data-ttu-id="1560c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1560c-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="1560c-120">Podpisy silnej nazwy zestawów pełnego zaufania nie są weryfikowane podczas zestawy są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1560c-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="1560c-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="1560c-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="1560c-122">Podpisy silnej nazwy zestawów pełnego zaufania są weryfikowane podczas zestawy są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1560c-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="1560c-123">Podpis silnej nazwy jest sprawdzany tylko pod kątem poprawności podpisu; nie była porównywana do innego silnej nazwy pod kątem dopasowania.</span><span class="sxs-lookup"><span data-stu-id="1560c-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1560c-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1560c-124">Child Elements</span></span>  
 <span data-ttu-id="1560c-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="1560c-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1560c-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1560c-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1560c-127">Element</span><span class="sxs-lookup"><span data-stu-id="1560c-127">Element</span></span>|<span data-ttu-id="1560c-128">Opis</span><span class="sxs-lookup"><span data-stu-id="1560c-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1560c-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1560c-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1560c-130">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1560c-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1560c-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1560c-131">Remarks</span></span>  
 <span data-ttu-id="1560c-132">Funkcja pomijania silnej nazwy pozwala uniknąć obciążenie weryfikacji podpisu silnej nazwy zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="1560c-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="1560c-133">Funkcja pomijania ma zastosowanie do dowolnego zestawu, który jest podpisany przy użyciu silnej nazwy i ma następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="1560c-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="1560c-134">Pełni zaufany bez <xref:System.Security.Policy.StrongName> dowód (na przykład `MyComputer` strefy dowód).</span><span class="sxs-lookup"><span data-stu-id="1560c-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="1560c-135">Załadowane w pełni zaufany <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1560c-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="1560c-136">Załadowane z lokalizacji w <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości tego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1560c-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="1560c-137">Nie podpisywany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="1560c-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1560c-138">Jeśli funkcja pomijania została wyłączona dla wszystkich aplikacji na komputerze przy użyciu klucza rejestru, to ustawienie pliku konfiguracji nie ma żadnego skutku.</span><span class="sxs-lookup"><span data-stu-id="1560c-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="1560c-139">Aby uzyskać więcej informacji, zobacz [porady: wyłączanie funkcji pomijania silnej nazwy](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="1560c-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1560c-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="1560c-140">Example</span></span>  
 <span data-ttu-id="1560c-141">Poniższy przykład pokazuje, jak do określania zachowania, która weryfikuje podpisu silnej nazwy zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="1560c-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1560c-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1560c-142">See Also</span></span>  
 [<span data-ttu-id="1560c-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1560c-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="1560c-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1560c-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1560c-145">Instrukcje: wyłączanie funkcji pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="1560c-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
