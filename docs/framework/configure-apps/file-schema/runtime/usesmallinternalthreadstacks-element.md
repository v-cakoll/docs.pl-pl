---
title: <UseSmallInternalThreadStacks> Element
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 2fd776ce8605e6dcf288dcb3852ded16638a1873
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73114927"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="4e7f1-102">\<UseSmallInternalThreadStacks> Element</span><span class="sxs-lookup"><span data-stu-id="4e7f1-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="4e7f1-103">Żądania, które zmniejszają użycie pamięci przez środowisko uruchomieniowe języka wspólnego (CLR) przez określenie jawnych rozmiarów stosu podczas tworzenia niektórych wątków, które używają wewnętrznie, zamiast używania domyślnego rozmiaru stosu dla tych wątków.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a><span data-ttu-id="4e7f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e7f1-104">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e7f1-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e7f1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4e7f1-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e7f1-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e7f1-107">Attributes</span></span>  
  
|<span data-ttu-id="4e7f1-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4e7f1-108">Attribute</span></span>|<span data-ttu-id="4e7f1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4e7f1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e7f1-110">enabled</span><span class="sxs-lookup"><span data-stu-id="4e7f1-110">enabled</span></span>|<span data-ttu-id="4e7f1-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="4e7f1-112">Określa, czy należy zażądać, aby środowisko CLR używało jawnych rozmiarów stosu zamiast domyślnego rozmiaru stosu, gdy tworzy pewne wątki używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-112">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="4e7f1-113">Jawne rozmiary stosu są mniejsze niż domyślny rozmiar stosu wynoszący 1 MB.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-113">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4e7f1-114">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="4e7f1-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="4e7f1-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="4e7f1-115">Value</span></span>|<span data-ttu-id="4e7f1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="4e7f1-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e7f1-117">true</span><span class="sxs-lookup"><span data-stu-id="4e7f1-117">true</span></span>|<span data-ttu-id="4e7f1-118">Żądaj jawnych rozmiarów stosu.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-118">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="4e7f1-119">fałsz</span><span class="sxs-lookup"><span data-stu-id="4e7f1-119">false</span></span>|<span data-ttu-id="4e7f1-120">Użyj domyślnego rozmiaru stosu.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-120">Use the default stack size.</span></span> <span data-ttu-id="4e7f1-121">Jest to wartość domyślna dla .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-121">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e7f1-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e7f1-122">Child Elements</span></span>  
 <span data-ttu-id="4e7f1-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e7f1-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e7f1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4e7f1-125">Element</span><span class="sxs-lookup"><span data-stu-id="4e7f1-125">Element</span></span>|<span data-ttu-id="4e7f1-126">Opis</span><span class="sxs-lookup"><span data-stu-id="4e7f1-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4e7f1-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4e7f1-128">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e7f1-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e7f1-129">Remarks</span></span>  
 <span data-ttu-id="4e7f1-130">Ten element konfiguracji jest używany do żądania zredukowania użycia pamięci wirtualnej w procesie, ponieważ jawne rozmiary wątków używane przez środowisko CLR dla wewnętrznych wątków, jeśli żądanie jest honorowane, są mniejsze niż rozmiar domyślny.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-130">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4e7f1-131">Ten element konfiguracji jest żądaniem do środowiska CLR, a nie bezwzględnym wymaganiem.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-131">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="4e7f1-132">W .NET Framework 4 żądanie jest uznawane za tylko dla architektury x86.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-132">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="4e7f1-133">Ten element może zostać całkowicie zignorowany w przyszłych wersjach środowiska CLR lub zastąpiony przez jawne rozmiary stosu, które są zawsze używane dla wybranych wewnętrznych wątków.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-133">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="4e7f1-134">Określenie tego elementu konfiguracji zapewnia niezawodność dla mniejszej ilości pamięci wirtualnej, jeśli środowisko CLR honoruje żądanie, ponieważ mniejsze rozmiary stosu mogą potencjalnie spowodować przepełnienie stosu.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-134">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e7f1-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e7f1-135">Example</span></span>  
 <span data-ttu-id="4e7f1-136">Poniższy przykład pokazuje, jak zażądać, aby środowisko CLR używało jawnych rozmiarów stosu dla niektórych wątków używanych wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="4e7f1-136">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e7f1-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e7f1-137">See also</span></span>

- [<span data-ttu-id="4e7f1-138">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="4e7f1-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4e7f1-139">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4e7f1-139">Configuration File Schema</span></span>](../index.md)
