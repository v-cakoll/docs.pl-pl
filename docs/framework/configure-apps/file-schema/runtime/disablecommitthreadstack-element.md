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
ms.openlocfilehash: 8aefb8a20d6a95c5b8062d0c03dcb28a3557ca3d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117471"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="fa2ee-102">\<element > disableCommitThreadStack</span><span class="sxs-lookup"><span data-stu-id="fa2ee-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="fa2ee-103">Określa, czy pełny stos wątków jest zatwierdzany podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
<span data-ttu-id="fa2ee-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="fa2ee-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fa2ee-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa2ee-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="fa2ee-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack >**</span><span class="sxs-lookup"><span data-stu-id="fa2ee-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa2ee-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa2ee-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa2ee-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fa2ee-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fa2ee-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa2ee-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fa2ee-110">Attributes</span></span>  
  
|<span data-ttu-id="fa2ee-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fa2ee-111">Attribute</span></span>|<span data-ttu-id="fa2ee-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fa2ee-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa2ee-113">dostępny</span><span class="sxs-lookup"><span data-stu-id="fa2ee-113">enabled</span></span>|<span data-ttu-id="fa2ee-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="fa2ee-115">Określa, czy zatwierdzanie pełnego stosu wątków podczas uruchamiania wątku (zachowanie domyślne) jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fa2ee-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="fa2ee-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="fa2ee-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="fa2ee-117">Value</span></span>|<span data-ttu-id="fa2ee-118">Opis</span><span class="sxs-lookup"><span data-stu-id="fa2ee-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fa2ee-119">0</span><span class="sxs-lookup"><span data-stu-id="fa2ee-119">0</span></span>|<span data-ttu-id="fa2ee-120">Nie należy wyłączać domyślnego zachowania środowiska uruchomieniowego języka wspólnego, czyli zatwierdzić pełny stos wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="fa2ee-121">1</span><span class="sxs-lookup"><span data-stu-id="fa2ee-121">1</span></span>|<span data-ttu-id="fa2ee-122">Wyłączenie domyślnego zachowania środowiska uruchomieniowego języka wspólnego, które polega na zatwierdzeniu pełnego stosu wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa2ee-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fa2ee-123">Child Elements</span></span>  
 <span data-ttu-id="fa2ee-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa2ee-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fa2ee-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fa2ee-126">Element</span><span class="sxs-lookup"><span data-stu-id="fa2ee-126">Element</span></span>|<span data-ttu-id="fa2ee-127">Opis</span><span class="sxs-lookup"><span data-stu-id="fa2ee-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fa2ee-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fa2ee-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa2ee-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa2ee-130">Remarks</span></span>  
 <span data-ttu-id="fa2ee-131">Domyślne zachowanie środowiska uruchomieniowego języka wspólnego polega na zatwierdzeniu pełnego stosu wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="fa2ee-132">Jeśli na serwerze, który ma ograniczoną ilość pamięci, należy utworzyć dużą liczbę wątków, a większość z nich będzie używać bardzo małej ilości miejsca na stosie, serwer może działać lepiej, jeśli środowisko uruchomieniowe języka wspólnego nie zatwierdzi pełnego stosu wątków natychmiast, gdy wątek ma wartość St chomiona.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa2ee-133">Hosty niezarządzane mogą używać flagi uruchamiania `STARTUP_DISABLE_COMMITTHREADSTACK` w wyliczeniu [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) , aby osiągnąć ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa2ee-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa2ee-134">Example</span></span>  
 <span data-ttu-id="fa2ee-135">Poniższy przykład pokazuje, jak wyłączyć domyślne zachowanie środowiska uruchomieniowego języka wspólnego, czyli zatwierdzić pełny stos wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa2ee-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa2ee-136">See also</span></span>

- [<span data-ttu-id="fa2ee-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fa2ee-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fa2ee-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fa2ee-138">Configuration File Schema</span></span>](../index.md)
