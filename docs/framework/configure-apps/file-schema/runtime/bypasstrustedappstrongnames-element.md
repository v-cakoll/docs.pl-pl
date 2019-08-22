---
title: <bypassTrustedAppStrongNames>, element
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aac7079d941e6774ca6c00fbece8ff72fbf3f0e1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663874"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="51b05-102">\<bypassTrustedAppStrongNames> Element</span><span class="sxs-lookup"><span data-stu-id="51b05-102">\<bypassTrustedAppStrongNames> Element</span></span>
<span data-ttu-id="51b05-103">Określa, czy pomijać weryfikację silnych nazw w zestawach pełnego zaufania, które są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="51b05-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="51b05-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="51b05-104">\<configuration></span></span>  
<span data-ttu-id="51b05-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="51b05-105">\<runtime></span></span>  
<span data-ttu-id="51b05-106">\<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="51b05-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b05-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="51b05-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51b05-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="51b05-108">Attributes and Elements</span></span>  
 <span data-ttu-id="51b05-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="51b05-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51b05-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="51b05-110">Attributes</span></span>  
  
|<span data-ttu-id="51b05-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="51b05-111">Attribute</span></span>|<span data-ttu-id="51b05-112">Opis</span><span class="sxs-lookup"><span data-stu-id="51b05-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="51b05-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="51b05-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="51b05-114">Określa, czy Funkcja pomijania, która pozwala uniknąć weryfikowania silnych nazw dla zestawów pełnego zaufania jest włączona.</span><span class="sxs-lookup"><span data-stu-id="51b05-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="51b05-115">Gdy ta funkcja jest włączona, silne nazwy nie są sprawdzane pod kątem poprawności podczas ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="51b05-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="51b05-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="51b05-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="51b05-117">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="51b05-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="51b05-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="51b05-118">Value</span></span>|<span data-ttu-id="51b05-119">Opis</span><span class="sxs-lookup"><span data-stu-id="51b05-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="51b05-120">Sygnatury o silnej nazwie w zestawach pełnego zaufania nie są sprawdzane, gdy zestawy są ładowane do pełnego <xref:System.AppDomain>zaufania.</span><span class="sxs-lookup"><span data-stu-id="51b05-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="51b05-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="51b05-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="51b05-122">Sygnatury silnej nazwy w zestawach pełnego zaufania są weryfikowane podczas ładowania zestawów do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="51b05-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="51b05-123">Sygnatura o silnej nazwie jest sprawdzana tylko w celu poprawienia podpisu; nie jest porównywana z inną silną nazwą dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="51b05-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51b05-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="51b05-124">Child Elements</span></span>  
 <span data-ttu-id="51b05-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="51b05-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51b05-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="51b05-126">Parent Elements</span></span>  
  
|<span data-ttu-id="51b05-127">Element</span><span class="sxs-lookup"><span data-stu-id="51b05-127">Element</span></span>|<span data-ttu-id="51b05-128">Opis</span><span class="sxs-lookup"><span data-stu-id="51b05-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="51b05-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51b05-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="51b05-130">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="51b05-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51b05-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51b05-131">Remarks</span></span>  
 <span data-ttu-id="51b05-132">Funkcja pomijania silnej nazwy pozwala uniknąć narzutu na weryfikację podpisów o silnej nazwie w przypadku zestawów o pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="51b05-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="51b05-133">Funkcja Bypass ma zastosowanie do każdego zestawu, który jest podpisany silną nazwą i ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="51b05-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
- <span data-ttu-id="51b05-134">W pełni zaufane bez <xref:System.Security.Policy.StrongName> dowodu (na przykład zawiera `MyComputer` dowody strefy).</span><span class="sxs-lookup"><span data-stu-id="51b05-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
- <span data-ttu-id="51b05-135">Załadowano w pełni zaufany <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="51b05-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="51b05-136">Załadowany z lokalizacji pod <xref:System.AppDomainSetup.ApplicationBase%2A> właściwością. <xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="51b05-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="51b05-137">Nie jest podpisany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="51b05-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51b05-138">Jeśli funkcja pomijania została wyłączona dla wszystkich aplikacji na komputerze przy użyciu klucza rejestru, to ustawienie tego pliku konfiguracji nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="51b05-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="51b05-139">Aby uzyskać więcej informacji, zobacz [jak: Wyłącz funkcję](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)pomijania silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="51b05-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51b05-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="51b05-140">Example</span></span>  
 <span data-ttu-id="51b05-141">Poniższy przykład pokazuje, jak określić zachowanie, które sprawdza podpis silnej nazwy w zestawach pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="51b05-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51b05-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51b05-142">See also</span></span>

- [<span data-ttu-id="51b05-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="51b05-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="51b05-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="51b05-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="51b05-145">Instrukcje: Wyłącz funkcję pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="51b05-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)
