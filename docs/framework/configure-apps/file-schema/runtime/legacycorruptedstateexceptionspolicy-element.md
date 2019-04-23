---
title: <legacyCorruptedStateExceptionsPolicy>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 777d496614435106b84b47b9aa3d35d964bc3e07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115105"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="7cf6b-102">\<legacyCorruptedStateExceptionsPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="7cf6b-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="7cf6b-103">Określa, czy środowisko uruchomieniowe języka wspólnego umożliwia kodu zarządzanego wykryć naruszenia zasad dostępu i inne wyjątki uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="7cf6b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="7cf6b-104">\<configuration></span></span>  
<span data-ttu-id="7cf6b-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="7cf6b-105">\<runtime></span></span>  
<span data-ttu-id="7cf6b-106">\<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="7cf6b-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf6b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cf6b-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cf6b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7cf6b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7cf6b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cf6b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7cf6b-110">Attributes</span></span>  
  
|<span data-ttu-id="7cf6b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7cf6b-111">Attribute</span></span>|<span data-ttu-id="7cf6b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7cf6b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7cf6b-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7cf6b-114">Określa, że aplikacja będzie przechwytywać uszkodzenia stan wyjątku awarie, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7cf6b-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="7cf6b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7cf6b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="7cf6b-116">Value</span></span>|<span data-ttu-id="7cf6b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="7cf6b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7cf6b-118">Aplikacja nie będzie przechwytywać uszkodzenia stan wyjątku awarie, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="7cf6b-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="7cf6b-120">Aplikacja będzie przechwytywać uszkodzenia stan wyjątku awarie, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cf6b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7cf6b-121">Child Elements</span></span>  
 <span data-ttu-id="7cf6b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7cf6b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7cf6b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7cf6b-124">Element</span><span class="sxs-lookup"><span data-stu-id="7cf6b-124">Element</span></span>|<span data-ttu-id="7cf6b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="7cf6b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7cf6b-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7cf6b-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cf6b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cf6b-128">Remarks</span></span>  
 <span data-ttu-id="7cf6b-129">W .NET Framework w wersji 3.5 i starszych środowisko uruchomieniowe języka wspólnego mogą przechwytywać wyjątków, które zostały zgłoszone przez Państwa uszkodzony procesu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="7cf6b-130">Naruszenie zasad dostępu znajduje się przykład tego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="7cf6b-131">Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], zarządzany kod nie jest już przechwytuje tego rodzaju wyjątków w `catch` bloków.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="7cf6b-132">Można jednak zastąpić tę zmianę i obsługa z obsługą wyjątków uszkodzony na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="7cf6b-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="7cf6b-133">Ustaw `<legacyCorruptedStateExceptionsPolicy>` elementu `enabled` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="7cf6b-134">To ustawienie konfiguracji jest zastosowany processwide i ma wpływ na wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="7cf6b-135">—lub—</span><span class="sxs-lookup"><span data-stu-id="7cf6b-135">-or-</span></span>  
  
-   <span data-ttu-id="7cf6b-136">Zastosuj <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atrybutu do metody, która zawiera wyjątki `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="7cf6b-137">Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cf6b-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cf6b-138">Example</span></span>  
 <span data-ttu-id="7cf6b-139">Poniższy przykład pokazuje, jak określić, że aplikacji należy powrócić do zachowania przed [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]i przechwytywać wszystkie błędny stan wyjątku błędów.</span><span class="sxs-lookup"><span data-stu-id="7cf6b-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7cf6b-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cf6b-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="7cf6b-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7cf6b-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="7cf6b-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7cf6b-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
