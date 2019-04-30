---
title: element < Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cde26250db0b3d11c51a18b7ebd378953ae0958
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704833"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="c5a7b-102">\<Crst_DisableSpinWait > element</span><span class="sxs-lookup"><span data-stu-id="c5a7b-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="c5a7b-103">Określa, czy wyłączyć pokrętła — oczekiwanie na sekcję krytyczną rywalizacją.</span><span class="sxs-lookup"><span data-stu-id="c5a7b-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span> \ 
  
 <span data-ttu-id="c5a7b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="c5a7b-104">\<configuration></span></span>  
<span data-ttu-id="c5a7b-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="c5a7b-105">\<runtime></span></span>  
<span data-ttu-id="c5a7b-106">\<Crst_DisableSpinWait ></span><span class="sxs-lookup"><span data-stu-id="c5a7b-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a7b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5a7b-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5a7b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c5a7b-108">Attributes and Elements</span></span>

<span data-ttu-id="c5a7b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5a7b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5a7b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c5a7b-110">Attributes</span></span>  
  
|<span data-ttu-id="c5a7b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c5a7b-111">Attribute</span></span>|<span data-ttu-id="c5a7b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c5a7b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5a7b-113">**Włączone**</span><span class="sxs-lookup"><span data-stu-id="c5a7b-113">**enabled**</span></span>|<span data-ttu-id="c5a7b-114">Określa, czy pokrętła — oczekiwanie na sekcje krytyczne jest włączona, gdy są one rywalizacją.</span><span class="sxs-lookup"><span data-stu-id="c5a7b-114">Specifies whether spin-waiting for critical sections is enabled when they are contended.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c5a7b-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="c5a7b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c5a7b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="c5a7b-116">Value</span></span>|<span data-ttu-id="c5a7b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c5a7b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5a7b-118">1</span><span class="sxs-lookup"><span data-stu-id="c5a7b-118">1</span></span>|<span data-ttu-id="c5a7b-119">Oczekiwania pokrętła jest włączona.</span><span class="sxs-lookup"><span data-stu-id="c5a7b-119">Spin-waiting is enabled.</span></span>|  
|<span data-ttu-id="c5a7b-120">0</span><span class="sxs-lookup"><span data-stu-id="c5a7b-120">0</span></span>|<span data-ttu-id="c5a7b-121">Oczekiwania pokrętła jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="c5a7b-121">Spin-waiting is disabled.</span></span> <span data-ttu-id="c5a7b-122">Jest to opcja domyślna</span><span class="sxs-lookup"><span data-stu-id="c5a7b-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5a7b-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c5a7b-123">Child Elements</span></span>  
 <span data-ttu-id="c5a7b-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="c5a7b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5a7b-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c5a7b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c5a7b-126">Element</span><span class="sxs-lookup"><span data-stu-id="c5a7b-126">Element</span></span>|<span data-ttu-id="c5a7b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="c5a7b-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c5a7b-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5a7b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c5a7b-129">Zawiera informacje o różnych ustawień konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c5a7b-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5a7b-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5a7b-130">Example</span></span>  

<span data-ttu-id="c5a7b-131">Poniższy przykład wyłącza pokrętła waiting, w sekcji krytycznych, gdy z rywalizacją.</span><span class="sxs-lookup"><span data-stu-id="c5a7b-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5a7b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5a7b-132">See also</span></span>

- [<span data-ttu-id="c5a7b-133">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c5a7b-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="c5a7b-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c5a7b-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
