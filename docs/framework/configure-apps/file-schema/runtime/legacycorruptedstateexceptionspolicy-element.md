---
title: <legacyCorruptedStateExceptionsPolicy>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8733e11aba30ebea30fc71a5350f76dfd041eb4
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456414"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="df598-102">\<legacyCorruptedStateExceptionsPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="df598-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="df598-103">Określa, czy środowisko uruchomieniowe języka wspólnego umożliwia kodu zarządzanego wykryć naruszenia zasad dostępu i inne wyjątki uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="df598-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="df598-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="df598-104">\<configuration></span></span>  
<span data-ttu-id="df598-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="df598-105">\<runtime></span></span>  
<span data-ttu-id="df598-106">\<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="df598-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df598-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="df598-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df598-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="df598-108">Attributes and Elements</span></span>  
 <span data-ttu-id="df598-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="df598-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df598-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="df598-110">Attributes</span></span>  
  
|<span data-ttu-id="df598-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="df598-111">Attribute</span></span>|<span data-ttu-id="df598-112">Opis</span><span class="sxs-lookup"><span data-stu-id="df598-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="df598-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="df598-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="df598-114">Określa, że aplikacja będzie przechwytywać uszkodzenia stan wyjątku awarie, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="df598-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="df598-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="df598-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="df598-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="df598-116">Value</span></span>|<span data-ttu-id="df598-117">Opis</span><span class="sxs-lookup"><span data-stu-id="df598-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="df598-118">Aplikacja nie będzie przechwytywać uszkodzenia stan wyjątku awarie, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="df598-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="df598-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="df598-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="df598-120">Aplikacja będzie przechwytywać uszkodzenia stan wyjątku awarie, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="df598-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df598-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="df598-121">Child Elements</span></span>  
 <span data-ttu-id="df598-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="df598-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df598-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="df598-123">Parent Elements</span></span>  
  
|<span data-ttu-id="df598-124">Element</span><span class="sxs-lookup"><span data-stu-id="df598-124">Element</span></span>|<span data-ttu-id="df598-125">Opis</span><span class="sxs-lookup"><span data-stu-id="df598-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="df598-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="df598-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="df598-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="df598-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df598-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df598-128">Remarks</span></span>  
 <span data-ttu-id="df598-129">W .NET Framework w wersji 3.5 i starszych środowisko uruchomieniowe języka wspólnego mogą przechwytywać wyjątków, które zostały zgłoszone przez Państwa uszkodzony procesu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="df598-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="df598-130">Naruszenie zasad dostępu znajduje się przykład tego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="df598-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="df598-131">Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], zarządzany kod nie jest już przechwytuje tego rodzaju wyjątków w `catch` bloków.</span><span class="sxs-lookup"><span data-stu-id="df598-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="df598-132">Można jednak zastąpić tę zmianę i obsługa z obsługą wyjątków uszkodzony na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="df598-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="df598-133">Ustaw `<legacyCorruptedStateExceptionsPolicy>` elementu `enabled` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="df598-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="df598-134">To ustawienie konfiguracji jest zastosowany processwide i ma wpływ na wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="df598-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="df598-135">—lub—</span><span class="sxs-lookup"><span data-stu-id="df598-135">-or-</span></span>  
  
- <span data-ttu-id="df598-136">Zastosuj <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atrybutu do metody, która zawiera wyjątki `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="df598-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="df598-137">Ten element konfiguracji jest dostępny tylko w programie .NET Framework 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="df598-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df598-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="df598-138">Example</span></span>  
 <span data-ttu-id="df598-139">Jak określić, że aplikacja powinna powrócić do zachowania przed programu .NET Framework 4 i przechwytywać wszystkie błędny stan wyjątku błędów można znaleźć w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="df598-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df598-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df598-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="df598-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="df598-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="df598-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="df598-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
