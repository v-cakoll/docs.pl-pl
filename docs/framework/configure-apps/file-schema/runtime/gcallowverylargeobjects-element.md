---
title: <gcAllowVeryLargeObjects>, element
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154130"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="5bb57-102">\<gcAllowVeryLargeObjects> Element</span><span class="sxs-lookup"><span data-stu-id="5bb57-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="5bb57-103">Na platformach 64-bitowych włącza macierze o całkowitym rozmiarze większym niż 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="5bb57-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="5bb57-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5bb57-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5bb57-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5bb57-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5bb57-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span><span class="sxs-lookup"><span data-stu-id="5bb57-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bb57-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bb57-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bb57-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5bb57-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5bb57-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5bb57-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bb57-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5bb57-110">Attributes</span></span>  
  
|<span data-ttu-id="5bb57-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5bb57-111">Attribute</span></span>|<span data-ttu-id="5bb57-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5bb57-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5bb57-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5bb57-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5bb57-114">Określa, czy tablice o całkowitym rozmiarze większym niż 2 GB są włączone na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="5bb57-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5bb57-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="5bb57-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5bb57-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="5bb57-116">Value</span></span>|<span data-ttu-id="5bb57-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5bb57-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5bb57-118">Tablice o całkowitym rozmiarze większe niż 2 GB nie są włączone.</span><span class="sxs-lookup"><span data-stu-id="5bb57-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="5bb57-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="5bb57-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5bb57-120">Macierze o całkowitym rozmiarze większej niż 2 GB są włączone na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="5bb57-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bb57-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5bb57-121">Child Elements</span></span>  
 <span data-ttu-id="5bb57-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5bb57-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bb57-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5bb57-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5bb57-124">Element</span><span class="sxs-lookup"><span data-stu-id="5bb57-124">Element</span></span>|<span data-ttu-id="5bb57-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5bb57-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5bb57-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5bb57-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5bb57-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5bb57-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bb57-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5bb57-128">Remarks</span></span>  
 <span data-ttu-id="5bb57-129">Użycie tego elementu w pliku konfiguracji aplikacji umożliwia tablice o rozmiarze większym niż 2 GB, ale nie zmienia innych limitów rozmiaru obiektu lub rozmiaru tablicy:</span><span class="sxs-lookup"><span data-stu-id="5bb57-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="5bb57-130">Maksymalna liczba elementów w <xref:System.UInt32.MaxValue?displayProperty=nameWithType>tablicy to .</span><span class="sxs-lookup"><span data-stu-id="5bb57-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="5bb57-131">Maksymalny indeks w dowolnym pojedynczym wymiarze wynosi 2 147 483 591 (0x7FFFFFC7) dla tablic bajtowych i tablic struktur jedno bajtowych oraz 2 146 435 071 (0X7FEFFFFF) dla innych typów.</span><span class="sxs-lookup"><span data-stu-id="5bb57-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="5bb57-132">Maksymalny rozmiar ciągów i innych obiektów innych niż tablica pozostaje niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="5bb57-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5bb57-133">Przed włączeniem tej funkcji upewnij się, że aplikacja nie zawiera niebezpieczny kod, który zakłada, że wszystkie tablice są mniejsze niż 2 GB w rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="5bb57-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="5bb57-134">Na przykład niebezpieczny kod, który używa tablic jako buforów może być podatny na przekroczenia buforu, jeśli jest napisane przy założeniu, że tablice nie przekroczy 2 GB.</span><span class="sxs-lookup"><span data-stu-id="5bb57-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bb57-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bb57-135">Example</span></span>  
 <span data-ttu-id="5bb57-136">W poniższym przykładzie pokazano, jak włączyć tę funkcję dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5bb57-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="5bb57-137">Obsługiwane w</span><span class="sxs-lookup"><span data-stu-id="5bb57-137">Supported in</span></span>

<span data-ttu-id="5bb57-138">.NET Framework 4.5 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="5bb57-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="5bb57-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bb57-139">See also</span></span>

- [<span data-ttu-id="5bb57-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5bb57-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5bb57-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5bb57-141">Configuration File Schema</span></span>](../index.md)
