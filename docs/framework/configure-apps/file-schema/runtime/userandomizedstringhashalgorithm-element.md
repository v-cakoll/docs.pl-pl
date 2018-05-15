---
title: '&lt;Userandomizedstringhashalgorithm —&gt; — Element'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a515c3011905c4f5c18ed9d3e8edf489428c04d8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a><span data-ttu-id="1245b-102">&lt;Userandomizedstringhashalgorithm —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="1245b-102">&lt;UseRandomizedStringHashAlgorithm&gt; Element</span></span>
<span data-ttu-id="1245b-103">Określa, czy środowisko uruchomieniowe języka wspólnego oblicza skrótu dla ciągów na poszczególnych domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1245b-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
 <span data-ttu-id="1245b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1245b-104">\<configuration></span></span>  
<span data-ttu-id="1245b-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="1245b-105">\<runtime></span></span>  
<span data-ttu-id="1245b-106">\<Userandomizedstringhashalgorithm — ></span><span class="sxs-lookup"><span data-stu-id="1245b-106">\<UseRandomizedStringHashAlgorithm></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1245b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1245b-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1245b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1245b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1245b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1245b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1245b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1245b-110">Attributes</span></span>  
  
|<span data-ttu-id="1245b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1245b-111">Attribute</span></span>|<span data-ttu-id="1245b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1245b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1245b-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1245b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1245b-114">Określa, czy skrótu dla ciągów są obliczane na podstawie domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1245b-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1245b-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="1245b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1245b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="1245b-116">Value</span></span>|<span data-ttu-id="1245b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1245b-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="1245b-118">Środowisko uruchomieniowe języka wspólnego nie obliczeniowe skrótu dla ciągów na poszczególnych domen aplikacji; jeden algorytm służy do obliczania skrótu ciągu.</span><span class="sxs-lookup"><span data-stu-id="1245b-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="1245b-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="1245b-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="1245b-120">Środowisko uruchomieniowe języka wspólnego oblicza skrótu dla ciągów na poszczególnych domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1245b-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="1245b-121">Identycznych ciągów w różnych domenach aplikacji i w różnych procesów będzie miał inną skrótu.</span><span class="sxs-lookup"><span data-stu-id="1245b-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1245b-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1245b-122">Child Elements</span></span>  
 <span data-ttu-id="1245b-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="1245b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1245b-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1245b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1245b-125">Element</span><span class="sxs-lookup"><span data-stu-id="1245b-125">Element</span></span>|<span data-ttu-id="1245b-126">Opis</span><span class="sxs-lookup"><span data-stu-id="1245b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1245b-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1245b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1245b-128">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1245b-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1245b-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1245b-129">Remarks</span></span>  
 <span data-ttu-id="1245b-130">Domyślnie <xref:System.StringComparer> klasy i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metody użyć pojedynczego algorytmu wyznaczania wartości skrótu, tworzącego spójne skrótu w domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1245b-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="1245b-131">Jest to równoważne ustawienie `enabled` atrybutu `<UseRandomizedStringHashAlgorithm>` elementu `0`.</span><span class="sxs-lookup"><span data-stu-id="1245b-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="1245b-132">Jest to algorytmu wyznaczania wartości skrótu używany w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1245b-132">This is the hashing algorithm used in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="1245b-133"><xref:System.StringComparer> Klasy i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metody można również użyć innego algorytmu wyznaczania wartości skrótu, który oblicza skrótu na poszczególnych domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1245b-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="1245b-134">W związku z tym skrótu dla ciągów równoważne różnią się między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1245b-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="1245b-135">Jest to funkcji opcjonalnych; Aby móc korzystać z niego, należy ustawić `enabled` atrybutu `<UseRandomizedStringHashAlgorithm>` elementu `1`.</span><span class="sxs-lookup"><span data-stu-id="1245b-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="1245b-136">Operacja O(1) jest zwykle wyszukiwania ciągu w tablicy skrótów.</span><span class="sxs-lookup"><span data-stu-id="1245b-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="1245b-137">Jednak w przypadku wystąpienia dużej liczby kolizji wyszukiwania może stać się O (n<sup>2</sup>) operacji.</span><span class="sxs-lookup"><span data-stu-id="1245b-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="1245b-138">Można użyć `<UseRandomizedStringHashAlgorithm>` element konfiguracji do generowania losowego algorytmu wyznaczania wartości skrótu dla domeny aplikacji, co z kolei ogranicza liczbę potencjalnych konfliktów, szczególnie w przypadku, gdy klucze, z których mają być obliczane kodów skrótów są oparte na danych wejściowych przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="1245b-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1245b-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="1245b-139">Example</span></span>  
 <span data-ttu-id="1245b-140">W poniższym przykładzie zdefiniowano `DisplayString` klasy, który obejmuje stałą typu string prywatne, `s`, którego wartość wynosi "Jest ciągiem".</span><span class="sxs-lookup"><span data-stu-id="1245b-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="1245b-141">Zawiera także `ShowStringHashCode` metodę, która wyświetla wartość ciągu i jego skrótu wraz z nazwą domeny aplikacji, w którym jest wykonywany metody.</span><span class="sxs-lookup"><span data-stu-id="1245b-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="1245b-142">Po uruchomieniu przykładzie bez podawania plik konfiguracji, wyświetla dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="1245b-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="1245b-143">Należy zauważyć, że skrótu ciągu identyczne w domenach dwóch aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1245b-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="1245b-144">Jednak jeśli dodać następującego pliku konfiguracji do katalogu w tym przykładzie, a następnie uruchomić przykład, kodów skrótów dla tych samych parametrach różnią się według domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1245b-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="1245b-145">Gdy plik konfiguracji jest obecny, w przykładzie przedstawiono następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1245b-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="1245b-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1245b-146">See Also</span></span>  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
