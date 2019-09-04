---
title: < element > Crst_DisableSpinWait
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a91e21120ecebbe7af2fb93798bc68d274fa92c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252715"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="c2659-102">\<Crst_DisableSpinWait, element ></span><span class="sxs-lookup"><span data-stu-id="c2659-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="c2659-103">Określa, czy należy wyłączyć funkcję "oczekiwanie" podczas oczekiwania na sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="c2659-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
<span data-ttu-id="c2659-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2659-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c2659-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2659-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c2659-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Crst_DisableSpinWait >**</span><span class="sxs-lookup"><span data-stu-id="c2659-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2659-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2659-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2659-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c2659-108">Attributes and Elements</span></span>

<span data-ttu-id="c2659-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2659-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2659-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c2659-110">Attributes</span></span>  
  
|<span data-ttu-id="c2659-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c2659-111">Attribute</span></span>|<span data-ttu-id="c2659-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c2659-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2659-113">**dostępny**</span><span class="sxs-lookup"><span data-stu-id="c2659-113">**enabled**</span></span>|<span data-ttu-id="c2659-114">Określa, czy oczekiwanie na przejście na sekcje krytyczne, gdy są one z nimi związane, jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c2659-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c2659-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="c2659-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c2659-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="c2659-116">Value</span></span>|<span data-ttu-id="c2659-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c2659-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c2659-118">1</span><span class="sxs-lookup"><span data-stu-id="c2659-118">1</span></span>|<span data-ttu-id="c2659-119">Wyłączenie pokrętła — oczekiwanie, jeśli nie można uzyskać sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="c2659-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="c2659-120">0</span><span class="sxs-lookup"><span data-stu-id="c2659-120">0</span></span>|<span data-ttu-id="c2659-121">Nie należy wyłączać elementu "oczekiwanie", jeśli nie można uzyskać sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="c2659-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="c2659-122">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="c2659-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2659-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c2659-123">Child Elements</span></span>  
 <span data-ttu-id="c2659-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="c2659-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2659-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2659-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c2659-126">Element</span><span class="sxs-lookup"><span data-stu-id="c2659-126">Element</span></span>|<span data-ttu-id="c2659-127">Opis</span><span class="sxs-lookup"><span data-stu-id="c2659-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c2659-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2659-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c2659-129">Zawiera informacje o różnych ustawieniach konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c2659-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c2659-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2659-130">Example</span></span>  

<span data-ttu-id="c2659-131">W poniższym przykładzie jest wyłączone obracanie w sekcji o kluczowym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="c2659-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2659-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2659-132">See also</span></span>

- [<span data-ttu-id="c2659-133">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c2659-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c2659-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c2659-134">Configuration File Schema</span></span>](../index.md)
