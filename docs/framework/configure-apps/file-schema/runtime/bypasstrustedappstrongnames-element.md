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
ms.openlocfilehash: 92873277b4b25e4c1c5981628187078ac7cb5704
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920890"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="fd8e3-102">\<bypassTrustedAppStrongNames> Element</span><span class="sxs-lookup"><span data-stu-id="fd8e3-102">\<bypassTrustedAppStrongNames> Element</span></span>
<span data-ttu-id="fd8e3-103">Określa, czy pomijać weryfikację silnych nazw w zestawach pełnego zaufania, które są ładowane do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="fd8e3-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fd8e3-104">\<configuration></span></span>  
<span data-ttu-id="fd8e3-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="fd8e3-105">\<runtime></span></span>  
<span data-ttu-id="fd8e3-106">\<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="fd8e3-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8e3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd8e3-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd8e3-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fd8e3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fd8e3-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd8e3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd8e3-110">Attributes</span></span>  
  
|<span data-ttu-id="fd8e3-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd8e3-111">Attribute</span></span>|<span data-ttu-id="fd8e3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fd8e3-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fd8e3-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fd8e3-114">Określa, czy Funkcja pomijania, która pozwala uniknąć weryfikowania silnych nazw dla zestawów pełnego zaufania jest włączona.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="fd8e3-115">Gdy ta funkcja jest włączona, silne nazwy nie są sprawdzane pod kątem poprawności podczas ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="fd8e3-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fd8e3-117">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="fd8e3-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="fd8e3-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="fd8e3-118">Value</span></span>|<span data-ttu-id="fd8e3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="fd8e3-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="fd8e3-120">Sygnatury o silnej nazwie w zestawach pełnego zaufania nie są sprawdzane, gdy zestawy są ładowane do pełnego <xref:System.AppDomain>zaufania.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="fd8e3-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="fd8e3-122">Sygnatury silnej nazwy w zestawach pełnego zaufania są weryfikowane podczas ładowania zestawów do pełnego zaufania <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="fd8e3-123">Sygnatura o silnej nazwie jest sprawdzana tylko w celu poprawienia podpisu; nie jest porównywana z inną silną nazwą dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd8e3-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd8e3-124">Child Elements</span></span>  
 <span data-ttu-id="fd8e3-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd8e3-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd8e3-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fd8e3-127">Element</span><span class="sxs-lookup"><span data-stu-id="fd8e3-127">Element</span></span>|<span data-ttu-id="fd8e3-128">Opis</span><span class="sxs-lookup"><span data-stu-id="fd8e3-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fd8e3-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fd8e3-130">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd8e3-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd8e3-131">Remarks</span></span>  
 <span data-ttu-id="fd8e3-132">Funkcja pomijania silnej nazwy pozwala uniknąć narzutu na weryfikację podpisów o silnej nazwie w przypadku zestawów o pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="fd8e3-133">Funkcja Bypass ma zastosowanie do każdego zestawu, który jest podpisany silną nazwą i ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="fd8e3-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
- <span data-ttu-id="fd8e3-134">W pełni zaufane bez <xref:System.Security.Policy.StrongName> dowodu (na przykład zawiera `MyComputer` dowody strefy).</span><span class="sxs-lookup"><span data-stu-id="fd8e3-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
- <span data-ttu-id="fd8e3-135">Załadowano w pełni zaufany <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="fd8e3-136">Załadowany z lokalizacji pod <xref:System.AppDomainSetup.ApplicationBase%2A> właściwością. <xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="fd8e3-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="fd8e3-137">Nie jest podpisany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-137">Not delay-signed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd8e3-138">Jeśli funkcja pomijania została wyłączona dla wszystkich aplikacji na komputerze przy użyciu klucza rejestru, to ustawienie tego pliku konfiguracji nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="fd8e3-139">Aby uzyskać więcej informacji, zobacz [jak: Wyłącz funkcję](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)pomijania silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd8e3-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd8e3-140">Example</span></span>  
 <span data-ttu-id="fd8e3-141">Poniższy przykład pokazuje, jak określić zachowanie, które sprawdza podpis silnej nazwy w zestawach pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="fd8e3-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd8e3-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd8e3-142">See also</span></span>

- [<span data-ttu-id="fd8e3-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fd8e3-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fd8e3-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fd8e3-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fd8e3-145">Instrukcje: Wyłącz funkcję pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="fd8e3-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)
