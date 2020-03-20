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
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153780"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="7d65b-102">\<UseRandomizedStringHashAlgorithm> Element</span><span class="sxs-lookup"><span data-stu-id="7d65b-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="7d65b-103">Określa, czy środowisko uruchomieniowe języka wspólnego oblicza kody mieszania dla ciągów na podstawie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65b-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="7d65b-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d65b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7d65b-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d65b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7d65b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span><span class="sxs-lookup"><span data-stu-id="7d65b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d65b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d65b-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d65b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d65b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7d65b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d65b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d65b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d65b-110">Attributes</span></span>  
  
|<span data-ttu-id="7d65b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7d65b-111">Attribute</span></span>|<span data-ttu-id="7d65b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7d65b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7d65b-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7d65b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7d65b-114">Określa, czy kody skrótów dla ciągów są obliczane dla domeny dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65b-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7d65b-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="7d65b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7d65b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="7d65b-116">Value</span></span>|<span data-ttu-id="7d65b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="7d65b-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="7d65b-118">Środowisko wykonawcze języka wspólnego nie oblicza kodów skrótów dla ciągów na podstawie domeny aplikacji; pojedynczy algorytm jest używany do obliczania kodów skrótów ciągów.</span><span class="sxs-lookup"><span data-stu-id="7d65b-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="7d65b-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="7d65b-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="7d65b-120">Środowisko wykonawcze języka wspólnego oblicza kody mieszania dla ciągów na podstawie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65b-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="7d65b-121">Identyczne ciągi w różnych domenach aplikacji i w różnych procesach będą miały różne kody skrótów.</span><span class="sxs-lookup"><span data-stu-id="7d65b-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d65b-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d65b-122">Child Elements</span></span>  
 <span data-ttu-id="7d65b-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d65b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d65b-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d65b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7d65b-125">Element</span><span class="sxs-lookup"><span data-stu-id="7d65b-125">Element</span></span>|<span data-ttu-id="7d65b-126">Opis</span><span class="sxs-lookup"><span data-stu-id="7d65b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7d65b-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d65b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7d65b-128">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7d65b-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d65b-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d65b-129">Remarks</span></span>  
 <span data-ttu-id="7d65b-130">Domyślnie <xref:System.StringComparer> klasa i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda używają algorytmu mieszania pojedynczego, który tworzy spójny kod mieszania w domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65b-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="7d65b-131">Jest to równoważne `enabled` ustawieniu `<UseRandomizedStringHashAlgorithm>` atrybutu `0`elementu na .</span><span class="sxs-lookup"><span data-stu-id="7d65b-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="7d65b-132">Jest to algorytm mieszania używany w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7d65b-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="7d65b-133">Klasa <xref:System.StringComparer> i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda można również użyć innego algorytmu mieszania, który oblicza kody mieszania na podstawie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65b-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="7d65b-134">W rezultacie kody mieszania dla równoważnych ciągów będą się różnić w domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65b-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="7d65b-135">Jest to funkcja opt-in; aby z niego skorzystać, należy `enabled` ustawić atrybut `<UseRandomizedStringHashAlgorithm>` elementu `1`na .</span><span class="sxs-lookup"><span data-stu-id="7d65b-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="7d65b-136">Wyszukiwanie ciągów w tabeli mieszania jest zazwyczaj operacją O(1).</span><span class="sxs-lookup"><span data-stu-id="7d65b-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="7d65b-137">Jednak gdy wystąpi duża liczba kolizji, wyszukiwanie może stać się operacją O(n<sup>2).</sup></span><span class="sxs-lookup"><span data-stu-id="7d65b-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="7d65b-138">Za pomocą `<UseRandomizedStringHashAlgorithm>` elementu konfiguracji można wygenerować algorytm mieszania losowego dla domeny aplikacji, co z kolei ogranicza liczbę potencjalnych kolizji, szczególnie gdy klucze, z których są obliczane kody skrótów, są oparte na danych wprowadzanych przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="7d65b-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d65b-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d65b-139">Example</span></span>  
 <span data-ttu-id="7d65b-140">Poniższy przykład definiuje `DisplayString` klasę, która zawiera `s`stałą prywatnego ciągu, której wartość jest "To jest ciąg".</span><span class="sxs-lookup"><span data-stu-id="7d65b-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="7d65b-141">Zawiera również `ShowStringHashCode` metodę, która wyświetla wartość ciągu i jego kod skrótu wraz z nazwą domeny aplikacji, w której metoda jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="7d65b-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="7d65b-142">Po uruchomieniu przykład bez podaniu pliku konfiguracji, wyświetla dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="7d65b-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="7d65b-143">Należy zauważyć, że kody skrótów dla ciągu są identyczne w dwóch domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65b-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="7d65b-144">Jeśli jednak dodasz następujący plik konfiguracyjny do katalogu przykładu, a następnie uruchomisz przykład, kody skrótów dla tego samego ciągu będą się różnić w zależności od domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65b-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="7d65b-145">Gdy plik konfiguracyjny jest obecny, w przykładzie są wyświetlane następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7d65b-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d65b-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d65b-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
