---
title: '&lt;disablecommitthreadstack —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d8724d16a25cdec040fa5b1f5472da06b11f669
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltdisablecommitthreadstackgt-element"></a><span data-ttu-id="05bda-102">&lt;disablecommitthreadstack —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="05bda-102">&lt;disableCommitThreadStack&gt; Element</span></span>
<span data-ttu-id="05bda-103">Określa, czy po uruchomieniu wątku zatwierdzone stosu wątku pełna.</span><span class="sxs-lookup"><span data-stu-id="05bda-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="05bda-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="05bda-104">\<configuration></span></span>  
<span data-ttu-id="05bda-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="05bda-105">\<runtime></span></span>  
<span data-ttu-id="05bda-106">\<disablecommitthreadstack — ></span><span class="sxs-lookup"><span data-stu-id="05bda-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05bda-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="05bda-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05bda-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="05bda-108">Attributes and Elements</span></span>  
 <span data-ttu-id="05bda-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="05bda-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05bda-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05bda-110">Attributes</span></span>  
  
|<span data-ttu-id="05bda-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05bda-111">Attribute</span></span>|<span data-ttu-id="05bda-112">Opis</span><span class="sxs-lookup"><span data-stu-id="05bda-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05bda-113">włączone</span><span class="sxs-lookup"><span data-stu-id="05bda-113">enabled</span></span>|<span data-ttu-id="05bda-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="05bda-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="05bda-115">Określa, czy zatwierdzania stosu wątku pełne podczas uruchamiania wątku (domyślnie) jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="05bda-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="05bda-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="05bda-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="05bda-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="05bda-117">Value</span></span>|<span data-ttu-id="05bda-118">Opis</span><span class="sxs-lookup"><span data-stu-id="05bda-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05bda-119">0</span><span class="sxs-lookup"><span data-stu-id="05bda-119">0</span></span>|<span data-ttu-id="05bda-120">Nie należy wyłączać domyślne zachowanie środowiska CLR, czyli zatwierdzić stosu wątku pełne po uruchomieniu wątku.</span><span class="sxs-lookup"><span data-stu-id="05bda-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="05bda-121">1</span><span class="sxs-lookup"><span data-stu-id="05bda-121">1</span></span>|<span data-ttu-id="05bda-122">Wyłącz domyślne zachowanie środowiska CLR, czyli zatwierdzić stosu wątku pełne po uruchomieniu wątku.</span><span class="sxs-lookup"><span data-stu-id="05bda-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05bda-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="05bda-123">Child Elements</span></span>  
 <span data-ttu-id="05bda-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="05bda-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05bda-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="05bda-125">Parent Elements</span></span>  
  
|<span data-ttu-id="05bda-126">Element</span><span class="sxs-lookup"><span data-stu-id="05bda-126">Element</span></span>|<span data-ttu-id="05bda-127">Opis</span><span class="sxs-lookup"><span data-stu-id="05bda-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="05bda-128">Element główny w każdym pliku konfiguracyjnym używane przez środowisko uruchomieniowe języka wspólnego i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05bda-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="05bda-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="05bda-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05bda-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05bda-130">Remarks</span></span>  
 <span data-ttu-id="05bda-131">Domyślne zachowanie środowiska CLR jest zatwierdzić stosu wątku pełne po uruchomieniu wątku.</span><span class="sxs-lookup"><span data-stu-id="05bda-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="05bda-132">Jeśli należy utworzyć dużej liczby wątków na serwerze, która ma ograniczoną pamięci, a większość tych wątków użyje bardzo mało miejsca na stosie, serwer może działać lepiej środowisko uruchomieniowe języka wspólnego nie zadeklarować stosu wątku pełne natychmiast, gdy wątek jest st arted.</span><span class="sxs-lookup"><span data-stu-id="05bda-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05bda-133">Niezarządzane hostów można użyć `STARTUP_DISABLE_COMMITTHREADSTACK` Flaga uruchamiania w [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczeniu, aby osiągnąć ten sam rezultat.</span><span class="sxs-lookup"><span data-stu-id="05bda-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05bda-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="05bda-134">Example</span></span>  
 <span data-ttu-id="05bda-135">Poniższy przykład pokazuje, jak można wyłączyć domyślnego zachowania środowiska CLR, czyli zatwierdzić stosu wątku pełne podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="05bda-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05bda-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05bda-136">See Also</span></span>  
 [<span data-ttu-id="05bda-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="05bda-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="05bda-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="05bda-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
