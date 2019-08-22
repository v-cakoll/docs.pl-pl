---
title: <disableCommitThreadStack>, element
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
ms.openlocfilehash: 4b1f55f056ef1aed4a5eff655650cefe778c97ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663780"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="28bbe-102">\<disableCommitThreadStack> Element</span><span class="sxs-lookup"><span data-stu-id="28bbe-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="28bbe-103">Określa, czy pełny stos wątków jest zatwierdzany podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="28bbe-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="28bbe-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="28bbe-104">\<configuration></span></span>  
<span data-ttu-id="28bbe-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="28bbe-105">\<runtime></span></span>  
<span data-ttu-id="28bbe-106">\<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="28bbe-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28bbe-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="28bbe-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28bbe-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="28bbe-108">Attributes and Elements</span></span>  
 <span data-ttu-id="28bbe-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="28bbe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28bbe-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28bbe-110">Attributes</span></span>  
  
|<span data-ttu-id="28bbe-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28bbe-111">Attribute</span></span>|<span data-ttu-id="28bbe-112">Opis</span><span class="sxs-lookup"><span data-stu-id="28bbe-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28bbe-113">dostępny</span><span class="sxs-lookup"><span data-stu-id="28bbe-113">enabled</span></span>|<span data-ttu-id="28bbe-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="28bbe-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="28bbe-115">Określa, czy zatwierdzanie pełnego stosu wątków podczas uruchamiania wątku (zachowanie domyślne) jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="28bbe-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="28bbe-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="28bbe-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="28bbe-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="28bbe-117">Value</span></span>|<span data-ttu-id="28bbe-118">Opis</span><span class="sxs-lookup"><span data-stu-id="28bbe-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="28bbe-119">0</span><span class="sxs-lookup"><span data-stu-id="28bbe-119">0</span></span>|<span data-ttu-id="28bbe-120">Nie należy wyłączać domyślnego zachowania środowiska uruchomieniowego języka wspólnego, czyli zatwierdzić pełny stos wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="28bbe-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="28bbe-121">1</span><span class="sxs-lookup"><span data-stu-id="28bbe-121">1</span></span>|<span data-ttu-id="28bbe-122">Wyłączenie domyślnego zachowania środowiska uruchomieniowego języka wspólnego, które polega na zatwierdzeniu pełnego stosu wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="28bbe-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28bbe-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28bbe-123">Child Elements</span></span>  
 <span data-ttu-id="28bbe-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="28bbe-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28bbe-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="28bbe-125">Parent Elements</span></span>  
  
|<span data-ttu-id="28bbe-126">Element</span><span class="sxs-lookup"><span data-stu-id="28bbe-126">Element</span></span>|<span data-ttu-id="28bbe-127">Opis</span><span class="sxs-lookup"><span data-stu-id="28bbe-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="28bbe-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28bbe-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="28bbe-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="28bbe-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28bbe-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28bbe-130">Remarks</span></span>  
 <span data-ttu-id="28bbe-131">Domyślne zachowanie środowiska uruchomieniowego języka wspólnego polega na zatwierdzeniu pełnego stosu wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="28bbe-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="28bbe-132">Jeśli na serwerze, który ma ograniczoną ilość pamięci, należy utworzyć dużą liczbę wątków, a większość z nich będzie używać bardzo małej ilości miejsca na stosie, serwer może działać lepiej, jeśli środowisko uruchomieniowe języka wspólnego nie zatwierdzi pełnego stosu wątków natychmiast, gdy wątek ma wartość St chomiona.</span><span class="sxs-lookup"><span data-stu-id="28bbe-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28bbe-133">Hosty niezarządzane mogą używać `STARTUP_DISABLE_COMMITTHREADSTACK` flagi uruchamiania w wyliczeniu [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) , aby osiągnąć ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="28bbe-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28bbe-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="28bbe-134">Example</span></span>  
 <span data-ttu-id="28bbe-135">Poniższy przykład pokazuje, jak wyłączyć domyślne zachowanie środowiska uruchomieniowego języka wspólnego, czyli zatwierdzić pełny stos wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="28bbe-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28bbe-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28bbe-136">See also</span></span>

- [<span data-ttu-id="28bbe-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="28bbe-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="28bbe-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="28bbe-138">Configuration File Schema</span></span>](../index.md)
