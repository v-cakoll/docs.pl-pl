---
title: <developmentMode> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117632"
---
# <a name="developmentmode-element"></a><span data-ttu-id="1d706-102">\<developmentMode> Element</span><span class="sxs-lookup"><span data-stu-id="1d706-102">\<developmentMode> Element</span></span>
<span data-ttu-id="1d706-103">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1d706-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="1d706-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d706-104">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d706-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d706-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1d706-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d706-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d706-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d706-107">Attributes</span></span>  
  
|<span data-ttu-id="1d706-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1d706-108">Attribute</span></span>|<span data-ttu-id="1d706-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1d706-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d706-110">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="1d706-110">**developerInstallation**</span></span>|<span data-ttu-id="1d706-111">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1d706-111">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="1d706-112">developerInstallation — atrybut</span><span class="sxs-lookup"><span data-stu-id="1d706-112">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="1d706-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="1d706-113">Value</span></span>|<span data-ttu-id="1d706-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1d706-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d706-115">**oznacza**</span><span class="sxs-lookup"><span data-stu-id="1d706-115">**true**</span></span>|<span data-ttu-id="1d706-116">Wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1d706-116">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="1d706-117">**false**</span><span class="sxs-lookup"><span data-stu-id="1d706-117">**false**</span></span>|<span data-ttu-id="1d706-118">Nie wyszukuje zestawów w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1d706-118">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="1d706-119">Jest to wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="1d706-119">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d706-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d706-120">Child Elements</span></span>  
 <span data-ttu-id="1d706-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="1d706-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d706-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d706-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1d706-123">Element</span><span class="sxs-lookup"><span data-stu-id="1d706-123">Element</span></span>|<span data-ttu-id="1d706-124">Opis</span><span class="sxs-lookup"><span data-stu-id="1d706-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1d706-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d706-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1d706-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1d706-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d706-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d706-127">Remarks</span></span>  
 <span data-ttu-id="1d706-128">Tego ustawienia należy używać tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="1d706-128">Use this setting only at development time.</span></span> <span data-ttu-id="1d706-129">Środowisko uruchomieniowe nie sprawdza wersji w zestawach o silnej nazwie znalezionych w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1d706-129">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="1d706-130">Po prostu używa pierwszego zestawu, który znajdzie.</span><span class="sxs-lookup"><span data-stu-id="1d706-130">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d706-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d706-131">Example</span></span>  
 <span data-ttu-id="1d706-132">Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1d706-132">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d706-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d706-133">See also</span></span>

- [<span data-ttu-id="1d706-134">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1d706-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1d706-135">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1d706-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1d706-136">Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="1d706-136">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
