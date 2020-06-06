---
title: <legacyCorruptedStateExceptionsPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116458"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="425c2-102">\<legacyCorruptedStateExceptionsPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="425c2-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="425c2-103">Określa, czy środowisko uruchomieniowe języka wspólnego umożliwia kodowi zarządzanemu przechwytywanie naruszeń dostępu i innych wyjątków uszkodzonych Stanów.</span><span class="sxs-lookup"><span data-stu-id="425c2-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="425c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="425c2-104">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="425c2-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="425c2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="425c2-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="425c2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="425c2-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="425c2-107">Attributes</span></span>  
  
|<span data-ttu-id="425c2-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="425c2-108">Attribute</span></span>|<span data-ttu-id="425c2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="425c2-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="425c2-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="425c2-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="425c2-111">Określa, że aplikacja będzie przechwytywać błędy wyjątku stanu, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="425c2-111">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="425c2-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="425c2-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="425c2-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="425c2-113">Value</span></span>|<span data-ttu-id="425c2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="425c2-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="425c2-115">Aplikacja nie będzie przechwytywać uszkodzonych błędów wyjątku stanu, takich jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="425c2-115">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="425c2-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="425c2-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="425c2-117">Aplikacja będzie przechwycić błędy wyjątku stanu, takie jak naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="425c2-117">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="425c2-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="425c2-118">Child Elements</span></span>  
 <span data-ttu-id="425c2-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="425c2-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="425c2-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="425c2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="425c2-121">Element</span><span class="sxs-lookup"><span data-stu-id="425c2-121">Element</span></span>|<span data-ttu-id="425c2-122">Opis</span><span class="sxs-lookup"><span data-stu-id="425c2-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="425c2-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="425c2-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="425c2-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="425c2-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="425c2-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="425c2-125">Remarks</span></span>  
 <span data-ttu-id="425c2-126">W .NET Framework w wersji 3,5 i starszych środowisko uruchomieniowe języka wspólnego może przechwytywać wyjątki, które zostały zgłoszone przez uszkodzone Stany procesów.</span><span class="sxs-lookup"><span data-stu-id="425c2-126">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="425c2-127">Naruszenie zasad dostępu jest przykładem tego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="425c2-127">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="425c2-128">Począwszy od .NET Framework 4, kod zarządzany nie przechwytuje już tych typów wyjątków w `catch` blokach.</span><span class="sxs-lookup"><span data-stu-id="425c2-128">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="425c2-129">Można jednak zastąpić tę zmianę i zachować obsługę wyjątków uszkodzonych Stanów na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="425c2-129">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="425c2-130">Ustaw `<legacyCorruptedStateExceptionsPolicy>` `enabled` atrybut elementu na `true` .</span><span class="sxs-lookup"><span data-stu-id="425c2-130">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="425c2-131">To ustawienie konfiguracji jest stosowane processwide i ma wpływ na wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="425c2-131">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="425c2-132">-lub-</span><span class="sxs-lookup"><span data-stu-id="425c2-132">-or-</span></span>  
  
- <span data-ttu-id="425c2-133">Zastosuj <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atrybut do metody, która zawiera `catch` blok wyjątków.</span><span class="sxs-lookup"><span data-stu-id="425c2-133">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="425c2-134">Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="425c2-134">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="425c2-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="425c2-135">Example</span></span>  
 <span data-ttu-id="425c2-136">Poniższy przykład pokazuje, jak określić, że aplikacja ma zostać przywrócona do zachowania przed .NET Framework 4 i przechwycić wszystkie błędy wyjątków spowodowanych uszkodzeniem stanu.</span><span class="sxs-lookup"><span data-stu-id="425c2-136">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="425c2-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="425c2-137">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="425c2-138">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="425c2-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="425c2-139">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="425c2-139">Configuration File Schema</span></span>](../index.md)
