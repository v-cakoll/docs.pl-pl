---
title: "&lt;gcallowverylargeobjects —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49046c343ef749e597402f7e19a08fe1f2c98ca0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltgcallowverylargeobjectsgt-element"></a><span data-ttu-id="5fd16-102">&lt;gcallowverylargeobjects —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="5fd16-102">&lt;gcAllowVeryLargeObjects&gt; Element</span></span>
<span data-ttu-id="5fd16-103">Na platformach 64-bitowych umożliwia tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="5fd16-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="5fd16-104">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="5fd16-104">\<configuration> Element</span></span>  
<span data-ttu-id="5fd16-105">\<środowisko uruchomieniowe > — Element</span><span class="sxs-lookup"><span data-stu-id="5fd16-105">\<runtime> Element</span></span>  
<span data-ttu-id="5fd16-106">\<gcallowverylargeobjects — > — Element</span><span class="sxs-lookup"><span data-stu-id="5fd16-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fd16-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fd16-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fd16-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5fd16-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5fd16-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5fd16-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fd16-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5fd16-110">Attributes</span></span>  
  
|<span data-ttu-id="5fd16-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5fd16-111">Attribute</span></span>|<span data-ttu-id="5fd16-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5fd16-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5fd16-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5fd16-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5fd16-114">Określa, czy włączono tablic, które są większe niż 2 GB rozmiar całkowitą na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="5fd16-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5fd16-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="5fd16-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5fd16-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="5fd16-116">Value</span></span>|<span data-ttu-id="5fd16-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5fd16-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5fd16-118">Tablice większe niż 2 GB w łącznym rozmiarze nie są włączone.</span><span class="sxs-lookup"><span data-stu-id="5fd16-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="5fd16-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="5fd16-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5fd16-120">Tablice większe niż 2 GB w łącznym rozmiarze są włączone na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="5fd16-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fd16-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5fd16-121">Child Elements</span></span>  
 <span data-ttu-id="5fd16-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5fd16-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fd16-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5fd16-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5fd16-124">Element</span><span class="sxs-lookup"><span data-stu-id="5fd16-124">Element</span></span>|<span data-ttu-id="5fd16-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5fd16-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5fd16-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5fd16-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5fd16-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5fd16-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fd16-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5fd16-128">Remarks</span></span>  
 <span data-ttu-id="5fd16-129">Za pomocą tego elementu w pliku konfiguracyjnym aplikacji umożliwia tablic, które są większe niż 2 GB, rozmiar, ale nie powoduje zmiany innych limity rozmiaru obiektu lub rozmiar tablicy:</span><span class="sxs-lookup"><span data-stu-id="5fd16-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
-   <span data-ttu-id="5fd16-130">Maksymalna liczba elementów w tablicy jest <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5fd16-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="5fd16-131">Maksymalna wartość indeksu w dowolnym pojedynczy wymiarze jest 2,147,483,591 (0x7FFFFFC7) dla tablic bajtowych i tablice struktur jednobajtowe i 2,146,435,071 (0X7FEFFFFF) dla innych typów.</span><span class="sxs-lookup"><span data-stu-id="5fd16-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
-   <span data-ttu-id="5fd16-132">Maksymalny rozmiar ciągów i innych obiektów z systemem innym niż tablica jest bez zmian.</span><span class="sxs-lookup"><span data-stu-id="5fd16-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5fd16-133">Przed włączeniem tej funkcji, upewnij się, aplikacja nie ma niebezpieczny kod, który założono, że wszystkie tablice jest mniejszy niż rozmiar 2 GB.</span><span class="sxs-lookup"><span data-stu-id="5fd16-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="5fd16-134">Na przykład niebezpieczny kod, który korzysta z tablic jako buforów może być narażony na przepełnienia buforu zostanie zapisany na założeniu, że tablice nie przekroczy 2 GB.</span><span class="sxs-lookup"><span data-stu-id="5fd16-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fd16-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fd16-135">Example</span></span>  
 <span data-ttu-id="5fd16-136">Poniższy przykład przedstawia sposób włączyć tę funkcję dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5fd16-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fd16-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fd16-137">See Also</span></span>  
 [<span data-ttu-id="5fd16-138">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5fd16-138">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5fd16-139">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5fd16-139">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
