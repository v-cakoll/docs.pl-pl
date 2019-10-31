---
title: <legacyCorruptedStateExceptionsPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116458"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="5634a-102">\<element > legacyCorruptedStateExceptionsPolicy</span><span class="sxs-lookup"><span data-stu-id="5634a-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="5634a-103">Określa, czy środowisko uruchomieniowe języka wspólnego umożliwia kodowi zarządzanemu przechwytywanie naruszeń dostępu i innych wyjątków uszkodzonych Stanów.</span><span class="sxs-lookup"><span data-stu-id="5634a-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
<span data-ttu-id="5634a-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5634a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5634a-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5634a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5634a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyCorruptedStateExceptionsPolicy >**</span><span class="sxs-lookup"><span data-stu-id="5634a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5634a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5634a-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5634a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5634a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5634a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5634a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5634a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5634a-110">Attributes</span></span>  
  
|<span data-ttu-id="5634a-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5634a-111">Attribute</span></span>|<span data-ttu-id="5634a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5634a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5634a-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5634a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5634a-114">Określa, że aplikacja będzie przechwytywać błędy wyjątku stanu, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="5634a-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5634a-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="5634a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5634a-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="5634a-116">Value</span></span>|<span data-ttu-id="5634a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5634a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5634a-118">Aplikacja nie będzie przechwytywać uszkodzonych błędów wyjątku stanu, takich jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="5634a-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="5634a-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="5634a-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5634a-120">Aplikacja będzie przechwycić błędy wyjątku stanu, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="5634a-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5634a-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5634a-121">Child Elements</span></span>  
 <span data-ttu-id="5634a-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5634a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5634a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5634a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5634a-124">Element</span><span class="sxs-lookup"><span data-stu-id="5634a-124">Element</span></span>|<span data-ttu-id="5634a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5634a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5634a-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5634a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5634a-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5634a-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5634a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5634a-128">Remarks</span></span>  
 <span data-ttu-id="5634a-129">W .NET Framework w wersji 3,5 i starszych środowisko uruchomieniowe języka wspólnego może przechwytywać wyjątki, które zostały zgłoszone przez uszkodzone Stany procesów.</span><span class="sxs-lookup"><span data-stu-id="5634a-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="5634a-130">Naruszenie zasad dostępu jest przykładem tego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5634a-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="5634a-131">Począwszy od .NET Framework 4, kod zarządzany nie przechwytuje już tych typów wyjątków w blokach `catch`.</span><span class="sxs-lookup"><span data-stu-id="5634a-131">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="5634a-132">Można jednak zastąpić tę zmianę i zachować obsługę wyjątków uszkodzonych Stanów na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="5634a-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="5634a-133">Ustaw atrybut `enabled` elementu `<legacyCorruptedStateExceptionsPolicy>` na `true`.</span><span class="sxs-lookup"><span data-stu-id="5634a-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="5634a-134">To ustawienie konfiguracji jest stosowane processwide i ma wpływ na wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="5634a-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="5634a-135">—lub—</span><span class="sxs-lookup"><span data-stu-id="5634a-135">-or-</span></span>  
  
- <span data-ttu-id="5634a-136">Zastosuj atrybut <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> do metody zawierającej blok `catch` wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5634a-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="5634a-137">Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="5634a-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5634a-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="5634a-138">Example</span></span>  
 <span data-ttu-id="5634a-139">Poniższy przykład pokazuje, jak określić, że aplikacja ma zostać przywrócona do zachowania przed .NET Framework 4 i przechwycić wszystkie błędy wyjątków spowodowanych uszkodzeniem stanu.</span><span class="sxs-lookup"><span data-stu-id="5634a-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5634a-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5634a-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="5634a-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5634a-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5634a-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5634a-142">Configuration File Schema</span></span>](../index.md)
