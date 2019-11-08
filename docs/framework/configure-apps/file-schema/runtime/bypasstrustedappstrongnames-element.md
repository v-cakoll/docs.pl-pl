---
title: <bypassTrustedAppStrongNames> Element
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739085"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="d62cc-102">\<element > bypassTrustedAppStrongNames</span><span class="sxs-lookup"><span data-stu-id="d62cc-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="d62cc-103">Określa, czy pomijać weryfikację silnych nazw w zestawach pełnego zaufania, które są ładowane do <xref:System.AppDomain>pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="d62cc-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

<span data-ttu-id="d62cc-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d62cc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d62cc-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d62cc-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d62cc-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<bypassTrustedAppStrongNames >**</span><span class="sxs-lookup"><span data-stu-id="d62cc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d62cc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d62cc-107">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d62cc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d62cc-108">Attributes and Elements</span></span>

<span data-ttu-id="d62cc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d62cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d62cc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d62cc-110">Attributes</span></span>

|<span data-ttu-id="d62cc-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d62cc-111">Attribute</span></span>|<span data-ttu-id="d62cc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d62cc-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="d62cc-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d62cc-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d62cc-114">Określa, czy Funkcja pomijania, która pozwala uniknąć weryfikowania silnych nazw dla zestawów pełnego zaufania jest włączona.</span><span class="sxs-lookup"><span data-stu-id="d62cc-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="d62cc-115">Gdy ta funkcja jest włączona, silne nazwy nie są sprawdzane pod kątem poprawności podczas ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="d62cc-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="d62cc-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="d62cc-116">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="d62cc-117">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="d62cc-117">enabled Attribute</span></span>

|<span data-ttu-id="d62cc-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="d62cc-118">Value</span></span>|<span data-ttu-id="d62cc-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d62cc-119">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="d62cc-120">Sygnatury o silnej nazwie w zestawach pełnego zaufania nie są sprawdzane, gdy zestawy są ładowane do <xref:System.AppDomain>pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="d62cc-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="d62cc-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="d62cc-121">This is the default.</span></span>|
|`false`|<span data-ttu-id="d62cc-122">Sygnatury silnej nazwy w zestawach pełnego zaufania są weryfikowane podczas ładowania zestawów do <xref:System.AppDomain>pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="d62cc-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="d62cc-123">Sygnatura o silnej nazwie jest sprawdzana tylko w celu poprawienia podpisu; nie jest porównywana z inną silną nazwą dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="d62cc-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d62cc-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d62cc-124">Child Elements</span></span>

<span data-ttu-id="d62cc-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="d62cc-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d62cc-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d62cc-126">Parent Elements</span></span>

|<span data-ttu-id="d62cc-127">Element</span><span class="sxs-lookup"><span data-stu-id="d62cc-127">Element</span></span>|<span data-ttu-id="d62cc-128">Opis</span><span class="sxs-lookup"><span data-stu-id="d62cc-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="d62cc-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d62cc-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="d62cc-130">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d62cc-130">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d62cc-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d62cc-131">Remarks</span></span>

<span data-ttu-id="d62cc-132">Funkcja pomijania silnej nazwy pozwala uniknąć narzutu na weryfikację podpisów o silnej nazwie w przypadku zestawów o pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="d62cc-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="d62cc-133">Funkcja Bypass ma zastosowanie do każdego zestawu, który jest podpisany silną nazwą i ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="d62cc-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="d62cc-134">W pełni zaufane bez <xref:System.Security.Policy.StrongName> dowodów (na przykład ma `MyComputer`e dowody strefy).</span><span class="sxs-lookup"><span data-stu-id="d62cc-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="d62cc-135">Załadowano do w pełni zaufanego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="d62cc-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="d62cc-136">Załadowano z lokalizacji pod właściwością <xref:System.AppDomainSetup.ApplicationBase%2A> tej <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="d62cc-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="d62cc-137">Nie jest podpisany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="d62cc-137">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="d62cc-138">Jeśli funkcja pomijania została wyłączona dla wszystkich aplikacji na komputerze przy użyciu klucza rejestru, to ustawienie tego pliku konfiguracji nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="d62cc-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="d62cc-139">Aby uzyskać więcej informacji, zobacz [jak: wyłączanie funkcji pomijania silnej nazwy](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="d62cc-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="d62cc-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="d62cc-140">Example</span></span>

<span data-ttu-id="d62cc-141">Poniższy przykład pokazuje, jak określić zachowanie, które sprawdza podpis silnej nazwy w zestawach pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="d62cc-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d62cc-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d62cc-142">See also</span></span>

- [<span data-ttu-id="d62cc-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d62cc-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d62cc-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d62cc-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d62cc-145">Instrukcje: wyłączanie funkcji pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="d62cc-145">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
