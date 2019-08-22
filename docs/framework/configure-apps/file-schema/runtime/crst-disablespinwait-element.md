---
title: < element > Crst_DisableSpinWait
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a52dd671f1fbf6fda5bdc92c0935784181eb4b03
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663841"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="e9d16-102">\<Crst_DisableSpinWait, element ></span><span class="sxs-lookup"><span data-stu-id="e9d16-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="e9d16-103">Określa, czy należy wyłączyć funkcję "oczekiwanie" podczas oczekiwania na sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="e9d16-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="e9d16-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e9d16-104">\<configuration></span></span>  
<span data-ttu-id="e9d16-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="e9d16-105">\<runtime></span></span>  
<span data-ttu-id="e9d16-106">\<Crst_DisableSpinWait ></span><span class="sxs-lookup"><span data-stu-id="e9d16-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9d16-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9d16-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9d16-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e9d16-108">Attributes and Elements</span></span>

<span data-ttu-id="e9d16-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e9d16-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9d16-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e9d16-110">Attributes</span></span>  
  
|<span data-ttu-id="e9d16-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e9d16-111">Attribute</span></span>|<span data-ttu-id="e9d16-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e9d16-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9d16-113">**dostępny**</span><span class="sxs-lookup"><span data-stu-id="e9d16-113">**enabled**</span></span>|<span data-ttu-id="e9d16-114">Określa, czy oczekiwanie na przejście na sekcje krytyczne, gdy są one z nimi związane, jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e9d16-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e9d16-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="e9d16-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e9d16-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="e9d16-116">Value</span></span>|<span data-ttu-id="e9d16-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e9d16-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9d16-118">1</span><span class="sxs-lookup"><span data-stu-id="e9d16-118">1</span></span>|<span data-ttu-id="e9d16-119">Wyłączenie pokrętła — oczekiwanie, jeśli nie można uzyskać sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="e9d16-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="e9d16-120">0</span><span class="sxs-lookup"><span data-stu-id="e9d16-120">0</span></span>|<span data-ttu-id="e9d16-121">Nie należy wyłączać elementu "oczekiwanie", jeśli nie można uzyskać sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="e9d16-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="e9d16-122">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="e9d16-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9d16-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e9d16-123">Child Elements</span></span>  
 <span data-ttu-id="e9d16-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="e9d16-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9d16-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e9d16-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e9d16-126">Element</span><span class="sxs-lookup"><span data-stu-id="e9d16-126">Element</span></span>|<span data-ttu-id="e9d16-127">Opis</span><span class="sxs-lookup"><span data-stu-id="e9d16-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e9d16-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9d16-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e9d16-129">Zawiera informacje o różnych ustawieniach konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e9d16-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e9d16-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9d16-130">Example</span></span>  

<span data-ttu-id="e9d16-131">W poniższym przykładzie jest wyłączone obracanie w sekcji o kluczowym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="e9d16-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9d16-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9d16-132">See also</span></span>

- [<span data-ttu-id="e9d16-133">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e9d16-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e9d16-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e9d16-134">Configuration File Schema</span></span>](../index.md)
