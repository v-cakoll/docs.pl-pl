---
title: <UseRandomizedStringHashAlgorithm>, element
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
ms.openlocfilehash: 2a51b9fb485da605effbad0e81b8baf5e05e382a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675094"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="7359a-102">\<UseRandomizedStringHashAlgorithm> Element</span><span class="sxs-lookup"><span data-stu-id="7359a-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="7359a-103">Określa, czy środowisko uruchomieniowe języka wspólnego oblicza kody skrótów dla ciągów na podstawie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7359a-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
 <span data-ttu-id="7359a-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="7359a-104">\<configuration></span></span>  
<span data-ttu-id="7359a-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="7359a-105">\<runtime></span></span>  
<span data-ttu-id="7359a-106">\<UseRandomizedStringHashAlgorithm></span><span class="sxs-lookup"><span data-stu-id="7359a-106">\<UseRandomizedStringHashAlgorithm></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7359a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7359a-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7359a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7359a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7359a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7359a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7359a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7359a-110">Attributes</span></span>  
  
|<span data-ttu-id="7359a-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7359a-111">Attribute</span></span>|<span data-ttu-id="7359a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7359a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7359a-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7359a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7359a-114">Określa, czy kody skrótów dla ciągów są obliczane na podstawie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7359a-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7359a-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="7359a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7359a-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="7359a-116">Value</span></span>|<span data-ttu-id="7359a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="7359a-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="7359a-118">Środowisko uruchomieniowe języka wspólnego nie może obliczyć kodów skrótu dla ciągów na podstawie domeny aplikacji; jeden algorytm jest używany do obliczania kodów wartości skrótu ciągu.</span><span class="sxs-lookup"><span data-stu-id="7359a-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="7359a-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="7359a-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="7359a-120">Środowisko uruchomieniowe języka wspólnego oblicza kody skrótów dla ciągów na podstawie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7359a-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="7359a-121">Identyczne ciągi w różnych domenach aplikacji i w różnych procesach będą miały różne wartości skrótów.</span><span class="sxs-lookup"><span data-stu-id="7359a-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7359a-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7359a-122">Child Elements</span></span>  
 <span data-ttu-id="7359a-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="7359a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7359a-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7359a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7359a-125">Element</span><span class="sxs-lookup"><span data-stu-id="7359a-125">Element</span></span>|<span data-ttu-id="7359a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="7359a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7359a-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7359a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7359a-128">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7359a-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7359a-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7359a-129">Remarks</span></span>  
 <span data-ttu-id="7359a-130">Domyślnie <xref:System.StringComparer> klasy i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metody użyć pojedynczego algorytmu mieszania, który produkuje spójny kod mieszany w różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7359a-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="7359a-131">Jest to równoważne ustawieniu `enabled` atrybutu `<UseRandomizedStringHashAlgorithm>` elementu `0`.</span><span class="sxs-lookup"><span data-stu-id="7359a-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="7359a-132">Jest to algorytm mieszania używany w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7359a-132">This is the hashing algorithm used in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="7359a-133"><xref:System.StringComparer> Klasy i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metodę można również użyć innego algorytmu wyznaczania wartości skrótu, który oblicza kody skrótów na poszczególnych domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7359a-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="7359a-134">W rezultacie kody skrótów dla równoważnych ciągów różnią się w różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7359a-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="7359a-135">Jest to opcjonalna funkcja; Aby z niej korzystać, należy ustawić `enabled` atrybutu `<UseRandomizedStringHashAlgorithm>` elementu `1`.</span><span class="sxs-lookup"><span data-stu-id="7359a-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="7359a-136">Wyszukiwanie ciągu w tabeli skrótów jest zazwyczaj operacją O(1).</span><span class="sxs-lookup"><span data-stu-id="7359a-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="7359a-137">Jednak w przypadku wystąpienia dużej liczby kolizji wyszukiwanie może stać się O (n<sup>2</sup>) operacji.</span><span class="sxs-lookup"><span data-stu-id="7359a-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="7359a-138">Możesz użyć `<UseRandomizedStringHashAlgorithm>` element konfiguracji, aby wygenerować losowy algorytm mieszania dla domeny aplikacji, co z kolei ogranicza liczbę potencjalnych konfliktów, szczególnie w przypadku, gdy klucze, z których obliczane są kody mieszania są oparte na danych wejściowych przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="7359a-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7359a-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="7359a-139">Example</span></span>  
 <span data-ttu-id="7359a-140">W poniższym przykładzie zdefiniowano `DisplayString` klasę zawierającą prywatną stałą typu ciąg, `s`, którego wartość jest "Jest ciąg".</span><span class="sxs-lookup"><span data-stu-id="7359a-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="7359a-141">Obejmuje również `ShowStringHashCode` metoda, która wyświetla wartości ciągu i jego kod skrótu wraz z nazwą domeny aplikacji, w którym metoda jest wykonywaay.</span><span class="sxs-lookup"><span data-stu-id="7359a-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="7359a-142">Po uruchomieniu przykładu bez podawania pliku konfiguracji, wyświetla dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="7359a-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="7359a-143">Należy zauważyć, że kody mieszania dla ciągu są identyczne w dwóch domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7359a-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="7359a-144">Jeśli dodasz następujący plik konfiguracji do katalogu w tym przykładzie, a następnie uruchomisz przykład, kody skrótów dla tego samego ciągu będą różne według domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7359a-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="7359a-145">Gdy plik konfiguracji jest obecny, przykładzie są wyświetlane następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7359a-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="7359a-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7359a-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
