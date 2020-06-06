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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739085"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="2d094-102">\<bypassTrustedAppStrongNames> Element</span><span class="sxs-lookup"><span data-stu-id="2d094-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="2d094-103">Określa, czy pomijać weryfikację silnych nazw w zestawach pełnego zaufania, które są ładowane do pełnego zaufania <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="2d094-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="2d094-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d094-104">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d094-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2d094-105">Attributes and Elements</span></span>

<span data-ttu-id="2d094-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2d094-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d094-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2d094-107">Attributes</span></span>

|<span data-ttu-id="2d094-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2d094-108">Attribute</span></span>|<span data-ttu-id="2d094-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2d094-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="2d094-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="2d094-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="2d094-111">Określa, czy Funkcja pomijania, która pozwala uniknąć weryfikowania silnych nazw dla zestawów pełnego zaufania jest włączona.</span><span class="sxs-lookup"><span data-stu-id="2d094-111">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="2d094-112">Gdy ta funkcja jest włączona, silne nazwy nie są sprawdzane pod kątem poprawności podczas ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="2d094-112">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="2d094-113">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2d094-113">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="2d094-114">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="2d094-114">enabled Attribute</span></span>

|<span data-ttu-id="2d094-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="2d094-115">Value</span></span>|<span data-ttu-id="2d094-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2d094-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="2d094-117">Sygnatury o silnej nazwie w zestawach pełnego zaufania nie są sprawdzane, gdy zestawy są ładowane do pełnego zaufania <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="2d094-117">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="2d094-118">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="2d094-118">This is the default.</span></span>|
|`false`|<span data-ttu-id="2d094-119">Sygnatury silnej nazwy w zestawach pełnego zaufania są weryfikowane podczas ładowania zestawów do pełnego zaufania <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="2d094-119">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="2d094-120">Sygnatura o silnej nazwie jest sprawdzana tylko w celu poprawienia podpisu; nie jest porównywana z inną silną nazwą dla dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2d094-120">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2d094-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2d094-121">Child Elements</span></span>

<span data-ttu-id="2d094-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="2d094-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d094-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2d094-123">Parent Elements</span></span>

|<span data-ttu-id="2d094-124">Element</span><span class="sxs-lookup"><span data-stu-id="2d094-124">Element</span></span>|<span data-ttu-id="2d094-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2d094-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2d094-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d094-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="2d094-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2d094-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2d094-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d094-128">Remarks</span></span>

<span data-ttu-id="2d094-129">Funkcja pomijania silnej nazwy pozwala uniknąć narzutu na weryfikację podpisów o silnej nazwie w przypadku zestawów o pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="2d094-129">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="2d094-130">Funkcja Bypass ma zastosowanie do każdego zestawu, który jest podpisany silną nazwą i ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="2d094-130">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="2d094-131">W pełni zaufane bez <xref:System.Security.Policy.StrongName> dowodu (na przykład zawiera `MyComputer` dowody strefy).</span><span class="sxs-lookup"><span data-stu-id="2d094-131">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="2d094-132">Załadowano w pełni zaufany <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="2d094-132">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="2d094-133">Załadowany z lokalizacji pod <xref:System.AppDomainSetup.ApplicationBase%2A> właściwością <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="2d094-133">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="2d094-134">Nie jest podpisany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="2d094-134">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="2d094-135">Jeśli funkcja pomijania została wyłączona dla wszystkich aplikacji na komputerze przy użyciu klucza rejestru, to ustawienie tego pliku konfiguracji nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="2d094-135">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="2d094-136">Aby uzyskać więcej informacji, zobacz [jak: wyłączanie funkcji pomijania silnej nazwy](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="2d094-136">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="2d094-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d094-137">Example</span></span>

<span data-ttu-id="2d094-138">Poniższy przykład pokazuje, jak określić zachowanie, które sprawdza podpis silnej nazwy w zestawach pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="2d094-138">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2d094-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d094-139">See also</span></span>

- [<span data-ttu-id="2d094-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2d094-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2d094-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2d094-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2d094-142">Instrukcje: wyłączanie funkcji pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="2d094-142">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
