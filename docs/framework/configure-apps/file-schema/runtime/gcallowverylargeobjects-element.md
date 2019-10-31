---
title: <gcAllowVeryLargeObjects> Element
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: b6230833808ec45d702502e36f929db4e03173e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116792"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="6ea77-102">\<element > gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="6ea77-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="6ea77-103">Na platformach 64-bitowych program umożliwia korzystanie z tablic o rozmiarze większym niż 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="6ea77-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="6ea77-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6ea77-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6ea77-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ea77-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6ea77-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcAllowVeryLargeObjects >**</span><span class="sxs-lookup"><span data-stu-id="6ea77-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ea77-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ea77-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ea77-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6ea77-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6ea77-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6ea77-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ea77-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6ea77-110">Attributes</span></span>  
  
|<span data-ttu-id="6ea77-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6ea77-111">Attribute</span></span>|<span data-ttu-id="6ea77-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6ea77-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6ea77-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6ea77-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6ea77-114">Określa, czy tablice o rozmiarze większym niż 2 GB są włączone na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="6ea77-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6ea77-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="6ea77-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6ea77-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="6ea77-116">Value</span></span>|<span data-ttu-id="6ea77-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6ea77-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6ea77-118">Tablice o rozmiarze większym niż 2 GB nie są włączone.</span><span class="sxs-lookup"><span data-stu-id="6ea77-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="6ea77-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="6ea77-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6ea77-120">Tablice o rozmiarze większym niż 2 GB są włączone na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="6ea77-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ea77-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6ea77-121">Child Elements</span></span>  
 <span data-ttu-id="6ea77-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="6ea77-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ea77-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6ea77-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6ea77-124">Element</span><span class="sxs-lookup"><span data-stu-id="6ea77-124">Element</span></span>|<span data-ttu-id="6ea77-125">Opis</span><span class="sxs-lookup"><span data-stu-id="6ea77-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ea77-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ea77-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6ea77-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6ea77-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ea77-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ea77-128">Remarks</span></span>  
 <span data-ttu-id="6ea77-129">Użycie tego elementu w pliku konfiguracji aplikacji umożliwia korzystanie z tablic o rozmiarze większym niż 2 GB, ale nie powoduje zmiany innych limitów rozmiaru obiektu lub rozmiaru tablicy:</span><span class="sxs-lookup"><span data-stu-id="6ea77-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="6ea77-130">Maksymalna liczba elementów w tablicy jest <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ea77-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="6ea77-131">Maksymalny indeks w dowolnym pojedynczym wymiarze to 2 147 483 591 (0x7FFFFFC7) dla tablic bajtowych i tablic jednobajtowych struktur oraz 2 146 435 071 (0X7FEFFFFF) dla innych typów.</span><span class="sxs-lookup"><span data-stu-id="6ea77-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="6ea77-132">Maksymalny rozmiar ciągów i innych obiektów niebędących tablicami jest niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="6ea77-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="6ea77-133">Przed włączeniem tej funkcji upewnij się, że aplikacja nie zawiera niebezpiecznego kodu, który zakłada, że wszystkie tablice mają rozmiar mniejszy niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="6ea77-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="6ea77-134">Na przykład kod niebezpieczny używający tablic jako bufory może być podatny na przepełnienia buforu, jeśli zostanie zapisany w założeniu, że tablice nie przekroczą 2 GB.</span><span class="sxs-lookup"><span data-stu-id="6ea77-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ea77-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ea77-135">Example</span></span>  
 <span data-ttu-id="6ea77-136">Poniższy przykład pokazuje, jak włączyć tę funkcję dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6ea77-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="6ea77-137">Obsługiwane w</span><span class="sxs-lookup"><span data-stu-id="6ea77-137">Supported in</span></span>

<span data-ttu-id="6ea77-138">.NET Framework 4,5 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="6ea77-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="6ea77-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ea77-139">See also</span></span>

- [<span data-ttu-id="6ea77-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6ea77-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6ea77-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6ea77-141">Configuration File Schema</span></span>](../index.md)
