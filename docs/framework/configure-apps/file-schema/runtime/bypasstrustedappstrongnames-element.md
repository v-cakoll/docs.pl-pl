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
ms.openlocfilehash: 725e2ee19c97cf2642134058ece07b32455516a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565478"
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a><span data-ttu-id="28227-102">&lt;bypasstrustedappstrongnames —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="28227-102">&lt;bypassTrustedAppStrongNames&gt; Element</span></span>
<span data-ttu-id="28227-103">Określa, czy pominąć weryfikacji silnych nazw zestawów pełnego zaufania, które są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="28227-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="28227-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="28227-104">\<configuration></span></span>  
<span data-ttu-id="28227-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="28227-105">\<runtime></span></span>  
<span data-ttu-id="28227-106">\<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="28227-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28227-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="28227-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28227-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="28227-108">Attributes and Elements</span></span>  
 <span data-ttu-id="28227-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="28227-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28227-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28227-110">Attributes</span></span>  
  
|<span data-ttu-id="28227-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28227-111">Attribute</span></span>|<span data-ttu-id="28227-112">Opis</span><span class="sxs-lookup"><span data-stu-id="28227-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="28227-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="28227-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="28227-114">Określa, czy jest włączona funkcja obejścia, która pozwala uniknąć sprawdzania poprawności silne nazwy dla zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="28227-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="28227-115">Gdy ta funkcja jest włączona, silne nazwy nie są weryfikowane pod kątem poprawności, gdy zestaw jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="28227-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="28227-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="28227-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="28227-117">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="28227-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="28227-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="28227-118">Value</span></span>|<span data-ttu-id="28227-119">Opis</span><span class="sxs-lookup"><span data-stu-id="28227-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="28227-120">Podpisy silnej nazwy zestawów pełnego zaufania nie są weryfikowane, gdy zestawy są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="28227-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="28227-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="28227-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="28227-122">Podpisy silnej nazwy zestawów pełnego zaufania są weryfikowane, gdy zestawy są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="28227-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="28227-123">Podpis silnej nazwy jest sprawdzany tylko w przypadku poprawność podpisu; nie była porównywana do innego silnej nazwy, pod kątem dopasowania.</span><span class="sxs-lookup"><span data-stu-id="28227-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28227-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28227-124">Child Elements</span></span>  
 <span data-ttu-id="28227-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="28227-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28227-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="28227-126">Parent Elements</span></span>  
  
|<span data-ttu-id="28227-127">Element</span><span class="sxs-lookup"><span data-stu-id="28227-127">Element</span></span>|<span data-ttu-id="28227-128">Opis</span><span class="sxs-lookup"><span data-stu-id="28227-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="28227-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28227-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="28227-130">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="28227-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28227-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28227-131">Remarks</span></span>  
 <span data-ttu-id="28227-132">Funkcji pomijania silnej nazwy pozwala uniknąć konieczności weryfikacji podpisu silnej nazwy zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="28227-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="28227-133">Funkcja pomijania ma zastosowanie do dowolnego złożenia, który jest podpisany silną nazwą i ma następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="28227-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="28227-134">W pełni zaufany, bez <xref:System.Security.Policy.StrongName> dowodów (na przykład `MyComputer` strefa dowód).</span><span class="sxs-lookup"><span data-stu-id="28227-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="28227-135">Ładowany do w pełni zaufany <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="28227-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="28227-136">Ładowane z lokalizacji w obszarze <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość, która <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="28227-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="28227-137">Nie podpisywane z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="28227-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28227-138">Jeśli funkcja pomijania została wyłączona dla wszystkich aplikacji na komputerze przy użyciu klucza rejestru, to ustawienie pliku konfiguracji nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="28227-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="28227-139">Aby uzyskać więcej informacji, zobacz [jak: Wyłączanie funkcji pomijania silnej nazwy](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="28227-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28227-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="28227-140">Example</span></span>  
 <span data-ttu-id="28227-141">Poniższy przykład pokazuje, jak określić zachowanie, które sprawdza poprawność podpisu silnej nazwy zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="28227-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28227-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28227-142">See also</span></span>
- [<span data-ttu-id="28227-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="28227-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="28227-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="28227-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="28227-145">Instrukcje: Wyłączanie funkcji pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="28227-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
