---
title: "&lt;legacycorruptedstateexceptionspolicy —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4379f6f38c886504905483cefd7c7a6bbd519ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a><span data-ttu-id="cbae5-102">&lt;legacycorruptedstateexceptionspolicy —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="cbae5-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; Element</span></span>
<span data-ttu-id="cbae5-103">Określa, czy środowisko uruchomieniowe języka wspólnego umożliwia kodu zarządzanego do wychwytywania naruszenia zasad dostępu i innych wyjątków uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="cbae5-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="cbae5-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="cbae5-104">\<configuration></span></span>  
<span data-ttu-id="cbae5-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="cbae5-105">\<runtime></span></span>  
<span data-ttu-id="cbae5-106">\<legacycorruptedstateexceptionspolicy — ></span><span class="sxs-lookup"><span data-stu-id="cbae5-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbae5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbae5-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbae5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cbae5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cbae5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cbae5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbae5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cbae5-110">Attributes</span></span>  
  
|<span data-ttu-id="cbae5-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cbae5-111">Attribute</span></span>|<span data-ttu-id="cbae5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cbae5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="cbae5-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="cbae5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="cbae5-114">Określa, że aplikacja będzie przechwytywać uszkodzenia stanu wyjątek błędów, np. naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="cbae5-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="cbae5-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="cbae5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="cbae5-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="cbae5-116">Value</span></span>|<span data-ttu-id="cbae5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="cbae5-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="cbae5-118">Aplikacja nie będzie przechwytywać uszkodzenia stanu wyjątek błędów, np. naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="cbae5-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="cbae5-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="cbae5-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="cbae5-120">Aplikacja będzie przechwytywać uszkodzenia stanu wyjątek błędów, np. naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="cbae5-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbae5-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cbae5-121">Child Elements</span></span>  
 <span data-ttu-id="cbae5-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="cbae5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbae5-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cbae5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="cbae5-124">Element</span><span class="sxs-lookup"><span data-stu-id="cbae5-124">Element</span></span>|<span data-ttu-id="cbae5-125">Opis</span><span class="sxs-lookup"><span data-stu-id="cbae5-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cbae5-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbae5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="cbae5-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cbae5-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbae5-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbae5-128">Remarks</span></span>  
 <span data-ttu-id="cbae5-129">W programie .NET Framework w wersji 3.5 lub starszym środowisko uruchomieniowe języka wspólnego dozwolone kodu zarządzanego przechwytują wyjątki, które zostały zgłoszone przez Państwa uszkodzony procesu.</span><span class="sxs-lookup"><span data-stu-id="cbae5-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="cbae5-130">Przykładem tego typu wyjątku jest naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="cbae5-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="cbae5-131">Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]zarządzanego kodu nie przechwytuje tych typów wyjątków w `catch` bloków.</span><span class="sxs-lookup"><span data-stu-id="cbae5-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="cbae5-132">Można jednak zastąpić tę zmianę i obsługa obsługi wyjątków uszkodzony na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="cbae5-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="cbae5-133">Ustaw `<legacyCorruptedStateExceptionsPolicy>` elementu `enabled` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="cbae5-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="cbae5-134">To ustawienie konfiguracji jest stosowane processwide i ma wpływ na wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="cbae5-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="cbae5-135">—lub—</span><span class="sxs-lookup"><span data-stu-id="cbae5-135">-or-</span></span>  
  
-   <span data-ttu-id="cbae5-136">Zastosuj <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atrybut do metody, która zawiera wyłączenia `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="cbae5-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="cbae5-137">Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych.</span><span class="sxs-lookup"><span data-stu-id="cbae5-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbae5-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbae5-138">Example</span></span>  
 <span data-ttu-id="cbae5-139">Poniższy przykład przedstawia sposób określić, że aplikacja powinna przywrócić zachowanie przed [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]i catch błędny wszystkie błędy wyjątek stanu.</span><span class="sxs-lookup"><span data-stu-id="cbae5-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbae5-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbae5-140">See Also</span></span>  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [<span data-ttu-id="cbae5-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="cbae5-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="cbae5-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cbae5-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
