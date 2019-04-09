---
title: <disableCommitThreadStack> Element
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
ms.openlocfilehash: 08ffd6ffcb9a8fa356d486f6d2ae1113de0fa682
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106518"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="dbbca-102">\<disableCommitThreadStack> Element</span><span class="sxs-lookup"><span data-stu-id="dbbca-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="dbbca-103">Określa, czy stos pełnego wątku jest zatwierdzona, gdy wątek jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="dbbca-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="dbbca-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="dbbca-104">\<configuration></span></span>  
<span data-ttu-id="dbbca-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="dbbca-105">\<runtime></span></span>  
<span data-ttu-id="dbbca-106">\<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="dbbca-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbbca-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbbca-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbbca-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dbbca-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dbbca-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dbbca-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbbca-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dbbca-110">Attributes</span></span>  
  
|<span data-ttu-id="dbbca-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dbbca-111">Attribute</span></span>|<span data-ttu-id="dbbca-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dbbca-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbbca-113">Włączone</span><span class="sxs-lookup"><span data-stu-id="dbbca-113">enabled</span></span>|<span data-ttu-id="dbbca-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="dbbca-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="dbbca-115">Określa, czy zatwierdzenie stos pełnego wątku podczas uruchamiania wątku (zachowanie domyślne) jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="dbbca-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dbbca-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="dbbca-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="dbbca-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="dbbca-117">Value</span></span>|<span data-ttu-id="dbbca-118">Opis</span><span class="sxs-lookup"><span data-stu-id="dbbca-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbbca-119">0</span><span class="sxs-lookup"><span data-stu-id="dbbca-119">0</span></span>|<span data-ttu-id="dbbca-120">Nie należy wyłączać domyślne zachowanie środowiska CLR, czyli aby zatwierdzić stos pełnego wątku, gdy wątek jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="dbbca-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="dbbca-121">1</span><span class="sxs-lookup"><span data-stu-id="dbbca-121">1</span></span>|<span data-ttu-id="dbbca-122">Wyłączyć zachowanie domyślne środowisko uruchomieniowe języka wspólnego, czyli aby zatwierdzić stos pełnego wątku, gdy wątek jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="dbbca-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbbca-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dbbca-123">Child Elements</span></span>  
 <span data-ttu-id="dbbca-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="dbbca-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbbca-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dbbca-125">Parent Elements</span></span>  
  
|<span data-ttu-id="dbbca-126">Element</span><span class="sxs-lookup"><span data-stu-id="dbbca-126">Element</span></span>|<span data-ttu-id="dbbca-127">Opis</span><span class="sxs-lookup"><span data-stu-id="dbbca-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dbbca-128">Element główny w każdym pliku konfiguracji używane przez środowisko uruchomieniowe języka wspólnego i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbbca-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="dbbca-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dbbca-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbbca-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dbbca-130">Remarks</span></span>  
 <span data-ttu-id="dbbca-131">Domyślne zachowanie środowiska uruchomieniowego języka wspólnego jest zatwierdzenie stos pełnego wątku, gdy wątek jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="dbbca-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="dbbca-132">Jeśli duża liczba wątków musi zostać utworzona na serwerze, który ma ograniczoną pamięć, a większość te wątki użyje bardzo mało miejsca na stosie, serwer może działać lepiej natychmiast, gdy wątek jest st, środowisko uruchomieniowe języka wspólnego nie zatwierdzić stos pełnego wątku chomiona.</span><span class="sxs-lookup"><span data-stu-id="dbbca-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbbca-133">Można użyć niezarządzane hosty `STARTUP_DISABLE_COMMITTHREADSTACK` Flaga uruchamiania [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczeniu, aby osiągnąć ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="dbbca-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbbca-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbbca-134">Example</span></span>  
 <span data-ttu-id="dbbca-135">Poniższy przykład pokazuje, jak wyłączyć zachowanie domyślne środowisko uruchomieniowe języka wspólnego, czyli aby zatwierdzić stos pełnego wątku podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="dbbca-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbbca-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbbca-136">See also</span></span>

- [<span data-ttu-id="dbbca-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="dbbca-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="dbbca-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dbbca-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
