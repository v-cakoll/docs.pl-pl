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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117471"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="f04b1-102">\<disableCommitThreadStack> Element</span><span class="sxs-lookup"><span data-stu-id="f04b1-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="f04b1-103">Określa, czy pełny stos wątków jest zatwierdzany podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="f04b1-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="f04b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f04b1-104">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f04b1-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f04b1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f04b1-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f04b1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f04b1-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f04b1-107">Attributes</span></span>  
  
|<span data-ttu-id="f04b1-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f04b1-108">Attribute</span></span>|<span data-ttu-id="f04b1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f04b1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f04b1-110">enabled</span><span class="sxs-lookup"><span data-stu-id="f04b1-110">enabled</span></span>|<span data-ttu-id="f04b1-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f04b1-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="f04b1-112">Określa, czy zatwierdzanie pełnego stosu wątków podczas uruchamiania wątku (zachowanie domyślne) jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f04b1-112">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f04b1-113">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="f04b1-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="f04b1-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="f04b1-114">Value</span></span>|<span data-ttu-id="f04b1-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f04b1-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f04b1-116">0</span><span class="sxs-lookup"><span data-stu-id="f04b1-116">0</span></span>|<span data-ttu-id="f04b1-117">Nie należy wyłączać domyślnego zachowania środowiska uruchomieniowego języka wspólnego, czyli zatwierdzić pełny stos wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="f04b1-117">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="f04b1-118">1</span><span class="sxs-lookup"><span data-stu-id="f04b1-118">1</span></span>|<span data-ttu-id="f04b1-119">Wyłączenie domyślnego zachowania środowiska uruchomieniowego języka wspólnego, które polega na zatwierdzeniu pełnego stosu wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="f04b1-119">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f04b1-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f04b1-120">Child Elements</span></span>  
 <span data-ttu-id="f04b1-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="f04b1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f04b1-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f04b1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f04b1-123">Element</span><span class="sxs-lookup"><span data-stu-id="f04b1-123">Element</span></span>|<span data-ttu-id="f04b1-124">Opis</span><span class="sxs-lookup"><span data-stu-id="f04b1-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f04b1-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f04b1-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f04b1-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f04b1-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f04b1-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f04b1-127">Remarks</span></span>  
 <span data-ttu-id="f04b1-128">Domyślne zachowanie środowiska uruchomieniowego języka wspólnego polega na zatwierdzeniu pełnego stosu wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="f04b1-128">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="f04b1-129">Jeśli na serwerze, który ma ograniczoną ilość pamięci, należy utworzyć dużą liczbę wątków, a większość z nich będzie używać bardzo małej ilości miejsca na stosie, serwer może działać lepiej, jeśli środowisko uruchomieniowe języka wspólnego nie zatwierdzi pełnego stosu wątków natychmiast po rozpoczęciu wątku.</span><span class="sxs-lookup"><span data-stu-id="f04b1-129">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f04b1-130">Hosty niezarządzane mogą używać `STARTUP_DISABLE_COMMITTHREADSTACK` flagi uruchamiania w wyliczeniu [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) , aby osiągnąć ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="f04b1-130">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f04b1-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="f04b1-131">Example</span></span>  
 <span data-ttu-id="f04b1-132">Poniższy przykład pokazuje, jak wyłączyć domyślne zachowanie środowiska uruchomieniowego języka wspólnego, czyli zatwierdzić pełny stos wątków podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="f04b1-132">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f04b1-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f04b1-133">See also</span></span>

- [<span data-ttu-id="f04b1-134">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="f04b1-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f04b1-135">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f04b1-135">Configuration File Schema</span></span>](../index.md)
