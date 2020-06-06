---
title: <shadowCopyVerifyByTimestamp> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115727"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="e8bbe-102">\<shadowCopyVerifyByTimestamp> Element</span><span class="sxs-lookup"><span data-stu-id="e8bbe-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="e8bbe-103">Określa, czy kopiowanie w tle używa domyślnego zachowania uruchamiania wprowadzonego w .NET Framework 4, czy przywraca zachowanie uruchamiania wcześniejszych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="e8bbe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8bbe-104">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8bbe-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8bbe-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e8bbe-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8bbe-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8bbe-107">Attributes</span></span>  
  
|<span data-ttu-id="e8bbe-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e8bbe-108">Attribute</span></span>|<span data-ttu-id="e8bbe-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e8bbe-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8bbe-110">enabled</span><span class="sxs-lookup"><span data-stu-id="e8bbe-110">enabled</span></span>|<span data-ttu-id="e8bbe-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e8bbe-112">Określa, czy domeny aplikacji używające kopiowania w tle porównują sygnatury czasowe zestawów podczas uruchamiania, aby określić, czy zestaw został zaktualizowany przed skopiowaniem zestawu w tle.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-112">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e8bbe-113">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="e8bbe-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="e8bbe-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8bbe-114">Value</span></span>|<span data-ttu-id="e8bbe-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e8bbe-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e8bbe-116">true</span><span class="sxs-lookup"><span data-stu-id="e8bbe-116">true</span></span>|<span data-ttu-id="e8bbe-117">Podczas uruchamiania program kopiuje tylko te zestawy, które zostały zaktualizowane od czasu ostatniego skopiowania do katalogu kopii w tle.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-117">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="e8bbe-118">Jest to wartość domyślna dla .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-118">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="e8bbe-119">fałsz</span><span class="sxs-lookup"><span data-stu-id="e8bbe-119">false</span></span>|<span data-ttu-id="e8bbe-120">Przywraca zachowanie uruchamiania poprzednich wersji .NET Framework, które było skopiowane wszystkie pliki podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-120">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8bbe-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8bbe-121">Child Elements</span></span>  
 <span data-ttu-id="e8bbe-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8bbe-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8bbe-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e8bbe-124">Element</span><span class="sxs-lookup"><span data-stu-id="e8bbe-124">Element</span></span>|<span data-ttu-id="e8bbe-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e8bbe-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e8bbe-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e8bbe-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8bbe-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8bbe-128">Remarks</span></span>  
 <span data-ttu-id="e8bbe-129">Począwszy od .NET Framework 4, zestawy są kopiowane w tle, tylko wtedy, gdy ich sygnatury czasowe wskazują, że zostały zmienione od czasu ostatniego skopiowania do katalogu kopii w tle.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-129">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="e8bbe-130">Skraca to czas uruchamiania dla wielu aplikacji używających kopiowania w tle, zgodnie z opisem w obszarze [kopiowania w tle](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="e8bbe-130">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="e8bbe-131">W przypadku aplikacji z wysoką wartością procentową i częstotliwością aktualizacji zestawu mogą nie być korzystne zmiany w zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-131">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="e8bbe-132">W takim przypadku można użyć tego elementu, aby przywrócić zachowanie poprzednich wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-132">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8bbe-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8bbe-133">Example</span></span>  
 <span data-ttu-id="e8bbe-134">Poniższy przykład pokazuje, jak wyłączyć domyślne zachowanie podczas uruchamiania kopiowania w tle w .NET Framework 4 i przywrócić zachowanie uruchamiania poprzednich wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8bbe-134">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8bbe-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8bbe-135">See also</span></span>

- [<span data-ttu-id="e8bbe-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e8bbe-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e8bbe-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e8bbe-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e8bbe-138">Kopiowanie zestawów w tle</span><span class="sxs-lookup"><span data-stu-id="e8bbe-138">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
