---
title: <gcAllowVeryLargeObjects>, element
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19103b2ac6e6dbba930050074fcea3cfd5a97661
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704664"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="ec863-102">\<gcAllowVeryLargeObjects> Element</span><span class="sxs-lookup"><span data-stu-id="ec863-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="ec863-103">Na platformach 64-bitowych umożliwia tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="ec863-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="ec863-104">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="ec863-104">\<configuration> Element</span></span>  
<span data-ttu-id="ec863-105">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="ec863-105">\<runtime> Element</span></span>  
<span data-ttu-id="ec863-106">\<gcAllowVeryLargeObjects> Element</span><span class="sxs-lookup"><span data-stu-id="ec863-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec863-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec863-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec863-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ec863-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ec863-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ec863-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec863-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ec863-110">Attributes</span></span>  
  
|<span data-ttu-id="ec863-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ec863-111">Attribute</span></span>|<span data-ttu-id="ec863-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ec863-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ec863-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ec863-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ec863-114">Określa, czy tablic, które są większe niż 2 GB w łącznym rozmiarze są włączone na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="ec863-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ec863-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ec863-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ec863-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="ec863-116">Value</span></span>|<span data-ttu-id="ec863-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ec863-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ec863-118">Większa niż 2 GB łącznego rozmiaru tablic nie są włączone.</span><span class="sxs-lookup"><span data-stu-id="ec863-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="ec863-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="ec863-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ec863-120">Tablic większych niż 2 GB w łącznym rozmiarze są włączone na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="ec863-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec863-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ec863-121">Child Elements</span></span>  
 <span data-ttu-id="ec863-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="ec863-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec863-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ec863-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ec863-124">Element</span><span class="sxs-lookup"><span data-stu-id="ec863-124">Element</span></span>|<span data-ttu-id="ec863-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ec863-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ec863-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec863-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ec863-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ec863-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec863-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec863-128">Remarks</span></span>  
 <span data-ttu-id="ec863-129">Przy użyciu tego elementu w pliku konfiguracyjnym aplikacji umożliwia tablic, które są większe niż 2 GB, rozmiar, ale nie zmienia się inne ograniczenia dotyczące rozmiaru obiektu lub rozmiar tablicy:</span><span class="sxs-lookup"><span data-stu-id="ec863-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="ec863-130">Maksymalna liczba elementów w tablicy to <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ec863-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="ec863-131">Maksymalna wartość indeksu w dowolnym jeden wymiar jest 2,147,483,591 (0x7FFFFFC7) dla tablic bajtów i tablic struktur jednobajtowe i 2,146,435,071 (0X7FEFFFFF) w przypadku innych typów.</span><span class="sxs-lookup"><span data-stu-id="ec863-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="ec863-132">Maksymalny rozmiar dla ciągów i innych obiektów inny niż tablica jest bez zmian.</span><span class="sxs-lookup"><span data-stu-id="ec863-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ec863-133">Przed włączeniem tej funkcji, upewnij się, czy aplikacja nie zawiera niebezpieczny kod, który przyjęto założenie, że wszystkie tablice są mniejsze niż rozmiar 2 GB.</span><span class="sxs-lookup"><span data-stu-id="ec863-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="ec863-134">Na przykład niebezpieczny kod, który używa tablic jako buforów może być podatny na przepełnienia buforu, zostanie zapisany na założeniu, że tablice nie przekroczy 2 GB.</span><span class="sxs-lookup"><span data-stu-id="ec863-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec863-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec863-135">Example</span></span>  
 <span data-ttu-id="ec863-136">Poniższy przykład pokazuje, jak włączyć tę funkcję dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ec863-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec863-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec863-137">See also</span></span>

- [<span data-ttu-id="ec863-138">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ec863-138">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ec863-139">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ec863-139">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
