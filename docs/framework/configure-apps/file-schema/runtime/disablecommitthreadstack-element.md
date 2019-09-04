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
ms.openlocfilehash: 2fa32d64f3ce440981c5f26d731051a118ed9254
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252668"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="71d8e-102">\<disableCommitThreadStack> Element</span><span class="sxs-lookup"><span data-stu-id="71d8e-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="71d8e-103">Określa, czy pełny stos wątków jest zatwierdzany podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="71d8e-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
<span data-ttu-id="71d8e-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="71d8e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="71d8e-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="71d8e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="71d8e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack>**</span><span class="sxs-lookup"><span data-stu-id="71d8e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d8e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="71d8e-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71d8e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="71d8e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="71d8e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="71d8e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71d8e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="71d8e-110">Attributes</span></span>  
  
|<span data-ttu-id="71d8e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="71d8e-111">Attribute</span></span>|<span data-ttu-id="71d8e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="71d8e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71d8e-113">dostępny</span><span class="sxs-lookup"><span data-stu-id="71d8e-113">enabled</span></span>|<span data-ttu-id="71d8e-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="71d8e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="71d8e-115">Określa, czy zatwierdzanie pełnego stosu wątków podczas uruchamiania wątku (zachowanie domyślne) jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="71d8e-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="71d8e-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="71d8e-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="71d8e-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="71d8e-117">Value</span></span>|<span data-ttu-id="71d8e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="71d8e-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71d8e-119">0</span><span class="sxs-lookup"><span data-stu-id="71d8e-119">0</span></span>|<span data-ttu-id="71d8e-120">Nie należy wyłączać domyślnego zachowania środowiska uruchomieniowego języka wspólnego, czyli zatwierdzić pełny stos wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="71d8e-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="71d8e-121">1</span><span class="sxs-lookup"><span data-stu-id="71d8e-121">1</span></span>|<span data-ttu-id="71d8e-122">Wyłączenie domyślnego zachowania środowiska uruchomieniowego języka wspólnego, które polega na zatwierdzeniu pełnego stosu wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="71d8e-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71d8e-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="71d8e-123">Child Elements</span></span>  
 <span data-ttu-id="71d8e-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="71d8e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71d8e-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="71d8e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="71d8e-126">Element</span><span class="sxs-lookup"><span data-stu-id="71d8e-126">Element</span></span>|<span data-ttu-id="71d8e-127">Opis</span><span class="sxs-lookup"><span data-stu-id="71d8e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="71d8e-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71d8e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="71d8e-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="71d8e-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71d8e-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71d8e-130">Remarks</span></span>  
 <span data-ttu-id="71d8e-131">Domyślne zachowanie środowiska uruchomieniowego języka wspólnego polega na zatwierdzeniu pełnego stosu wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="71d8e-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="71d8e-132">Jeśli na serwerze, który ma ograniczoną ilość pamięci, należy utworzyć dużą liczbę wątków, a większość z nich będzie używać bardzo małej ilości miejsca na stosie, serwer może działać lepiej, jeśli środowisko uruchomieniowe języka wspólnego nie zatwierdzi pełnego stosu wątków natychmiast, gdy wątek ma wartość St chomiona.</span><span class="sxs-lookup"><span data-stu-id="71d8e-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71d8e-133">Hosty niezarządzane mogą używać `STARTUP_DISABLE_COMMITTHREADSTACK` flagi uruchamiania w wyliczeniu [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) , aby osiągnąć ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="71d8e-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71d8e-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="71d8e-134">Example</span></span>  
 <span data-ttu-id="71d8e-135">Poniższy przykład pokazuje, jak wyłączyć domyślne zachowanie środowiska uruchomieniowego języka wspólnego, czyli zatwierdzić pełny stos wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="71d8e-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71d8e-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71d8e-136">See also</span></span>

- [<span data-ttu-id="71d8e-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="71d8e-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="71d8e-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="71d8e-138">Configuration File Schema</span></span>](../index.md)
