---
title: element < Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f89f0558c11e229fef2ca3cd619e3c033f12c858
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754676"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="9cabc-102">\<Crst_DisableSpinWait > element</span><span class="sxs-lookup"><span data-stu-id="9cabc-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="9cabc-103">Określa, czy wyłączyć pokrętła — oczekiwanie na sekcję krytyczną rywalizacją.</span><span class="sxs-lookup"><span data-stu-id="9cabc-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="9cabc-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="9cabc-104">\<configuration></span></span>  
<span data-ttu-id="9cabc-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="9cabc-105">\<runtime></span></span>  
<span data-ttu-id="9cabc-106">\<Crst_DisableSpinWait ></span><span class="sxs-lookup"><span data-stu-id="9cabc-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cabc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cabc-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cabc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9cabc-108">Attributes and Elements</span></span>

<span data-ttu-id="9cabc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9cabc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cabc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9cabc-110">Attributes</span></span>  
  
|<span data-ttu-id="9cabc-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9cabc-111">Attribute</span></span>|<span data-ttu-id="9cabc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9cabc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9cabc-113">**Włączone**</span><span class="sxs-lookup"><span data-stu-id="9cabc-113">**enabled**</span></span>|<span data-ttu-id="9cabc-114">Określa, czy pokrętła — oczekiwanie na sekcje krytyczne, gdy są one rywalizacją jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="9cabc-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9cabc-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="9cabc-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9cabc-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="9cabc-116">Value</span></span>|<span data-ttu-id="9cabc-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9cabc-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9cabc-118">1</span><span class="sxs-lookup"><span data-stu-id="9cabc-118">1</span></span>|<span data-ttu-id="9cabc-119">Wyłącz pokrętła oczekiwania, gdy nie można pobrać sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="9cabc-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="9cabc-120">0</span><span class="sxs-lookup"><span data-stu-id="9cabc-120">0</span></span>|<span data-ttu-id="9cabc-121">Nie należy wyłączać pokrętła oczekiwania, gdy sekcję krytyczną, nie można pobrać.</span><span class="sxs-lookup"><span data-stu-id="9cabc-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="9cabc-122">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="9cabc-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cabc-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9cabc-123">Child Elements</span></span>  
 <span data-ttu-id="9cabc-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="9cabc-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cabc-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9cabc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9cabc-126">Element</span><span class="sxs-lookup"><span data-stu-id="9cabc-126">Element</span></span>|<span data-ttu-id="9cabc-127">Opis</span><span class="sxs-lookup"><span data-stu-id="9cabc-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9cabc-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9cabc-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9cabc-129">Zawiera informacje o różnych ustawień konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9cabc-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9cabc-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cabc-130">Example</span></span>  

<span data-ttu-id="9cabc-131">Poniższy przykład wyłącza pokrętła waiting, w sekcji krytycznych, gdy z rywalizacją.</span><span class="sxs-lookup"><span data-stu-id="9cabc-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cabc-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cabc-132">See also</span></span>

- [<span data-ttu-id="9cabc-133">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9cabc-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="9cabc-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9cabc-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
