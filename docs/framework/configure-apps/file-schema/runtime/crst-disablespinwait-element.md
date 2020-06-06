---
title: Element <Crst_DisableSpinWait>
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 0683081183081e249b2a9c89e1a6a15f638fb339
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117637"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="1297f-102">\<Crst_DisableSpinWait>, element</span><span class="sxs-lookup"><span data-stu-id="1297f-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="1297f-103">Określa, czy należy wyłączyć funkcję "oczekiwanie" podczas oczekiwania na sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="1297f-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="1297f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1297f-104">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1297f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1297f-105">Attributes and Elements</span></span>

<span data-ttu-id="1297f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1297f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1297f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1297f-107">Attributes</span></span>  
  
|<span data-ttu-id="1297f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1297f-108">Attribute</span></span>|<span data-ttu-id="1297f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1297f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1297f-110">**dostępny**</span><span class="sxs-lookup"><span data-stu-id="1297f-110">**enabled**</span></span>|<span data-ttu-id="1297f-111">Określa, czy oczekiwanie na przejście na sekcje krytyczne, gdy są one z nimi związane, jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="1297f-111">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1297f-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="1297f-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="1297f-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="1297f-113">Value</span></span>|<span data-ttu-id="1297f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1297f-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1297f-115">1</span><span class="sxs-lookup"><span data-stu-id="1297f-115">1</span></span>|<span data-ttu-id="1297f-116">Wyłączenie pokrętła — oczekiwanie, jeśli nie można uzyskać sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="1297f-116">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="1297f-117">0</span><span class="sxs-lookup"><span data-stu-id="1297f-117">0</span></span>|<span data-ttu-id="1297f-118">Nie należy wyłączać elementu "oczekiwanie", jeśli nie można uzyskać sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="1297f-118">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="1297f-119">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="1297f-119">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1297f-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1297f-120">Child Elements</span></span>  
 <span data-ttu-id="1297f-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="1297f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1297f-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1297f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1297f-123">Element</span><span class="sxs-lookup"><span data-stu-id="1297f-123">Element</span></span>|<span data-ttu-id="1297f-124">Opis</span><span class="sxs-lookup"><span data-stu-id="1297f-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1297f-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1297f-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1297f-126">Zawiera informacje o różnych ustawieniach konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1297f-126">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1297f-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="1297f-127">Example</span></span>  

<span data-ttu-id="1297f-128">W poniższym przykładzie jest wyłączone obracanie w sekcji o kluczowym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="1297f-128">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1297f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1297f-129">See also</span></span>

- [<span data-ttu-id="1297f-130">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1297f-130">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1297f-131">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1297f-131">Configuration File Schema</span></span>](../index.md)
