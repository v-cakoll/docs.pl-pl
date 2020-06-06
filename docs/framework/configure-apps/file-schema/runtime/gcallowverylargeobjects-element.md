---
title: <gcAllowVeryLargeObjects> Element
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154130"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="6ccc4-102">\<gcAllowVeryLargeObjects> Element</span><span class="sxs-lookup"><span data-stu-id="6ccc4-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="6ccc4-103">Na platformach 64-bitowych program umożliwia korzystanie z tablic o rozmiarze większym niż 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="6ccc4-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="6ccc4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ccc4-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ccc4-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6ccc4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6ccc4-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ccc4-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6ccc4-107">Attributes</span></span>  
  
|<span data-ttu-id="6ccc4-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6ccc4-108">Attribute</span></span>|<span data-ttu-id="6ccc4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6ccc4-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6ccc4-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="6ccc4-111">Określa, czy tablice o rozmiarze większym niż 2 GB są włączone na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-111">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6ccc4-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="6ccc4-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="6ccc4-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="6ccc4-113">Value</span></span>|<span data-ttu-id="6ccc4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6ccc4-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6ccc4-115">Tablice o rozmiarze większym niż 2 GB nie są włączone.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-115">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="6ccc4-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6ccc4-117">Tablice o rozmiarze większym niż 2 GB są włączone na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-117">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ccc4-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6ccc4-118">Child Elements</span></span>  
 <span data-ttu-id="6ccc4-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ccc4-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6ccc4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6ccc4-121">Element</span><span class="sxs-lookup"><span data-stu-id="6ccc4-121">Element</span></span>|<span data-ttu-id="6ccc4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="6ccc4-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ccc4-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6ccc4-124">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ccc4-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ccc4-125">Remarks</span></span>  
 <span data-ttu-id="6ccc4-126">Użycie tego elementu w pliku konfiguracji aplikacji umożliwia korzystanie z tablic o rozmiarze większym niż 2 GB, ale nie powoduje zmiany innych limitów rozmiaru obiektu lub rozmiaru tablicy:</span><span class="sxs-lookup"><span data-stu-id="6ccc4-126">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="6ccc4-127">Maksymalna liczba elementów w tablicy to <xref:System.UInt32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6ccc4-127">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="6ccc4-128">Maksymalny indeks w dowolnym pojedynczym wymiarze to 2 147 483 591 (0x7FFFFFC7) dla tablic bajtowych i tablic jednobajtowych struktur oraz 2 146 435 071 (0X7FEFFFFF) dla innych typów.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-128">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="6ccc4-129">Maksymalny rozmiar ciągów i innych obiektów niebędących tablicami jest niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-129">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="6ccc4-130">Przed włączeniem tej funkcji upewnij się, że aplikacja nie zawiera niebezpiecznego kodu, który zakłada, że wszystkie tablice mają rozmiar mniejszy niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-130">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="6ccc4-131">Na przykład kod niebezpieczny używający tablic jako bufory może być podatny na przepełnienia buforu, jeśli zostanie zapisany w założeniu, że tablice nie przekroczą 2 GB.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-131">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ccc4-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ccc4-132">Example</span></span>  
 <span data-ttu-id="6ccc4-133">Poniższy przykład pokazuje, jak włączyć tę funkcję dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-133">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="6ccc4-134">Obsługiwane w</span><span class="sxs-lookup"><span data-stu-id="6ccc4-134">Supported in</span></span>

<span data-ttu-id="6ccc4-135">.NET Framework 4,5 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="6ccc4-135">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="6ccc4-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ccc4-136">See also</span></span>

- [<span data-ttu-id="6ccc4-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6ccc4-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6ccc4-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6ccc4-138">Configuration File Schema</span></span>](../index.md)
