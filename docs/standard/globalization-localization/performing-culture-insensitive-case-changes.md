---
title: Wykonywanie niezależnych od kultury zmian wielkości liter
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
ms.openlocfilehash: b5289074724e3afd7356599738eeba648f25ca06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120846"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="5d3f5-102">Wykonywanie niezależnych od kultury zmian wielkości liter</span><span class="sxs-lookup"><span data-stu-id="5d3f5-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="5d3f5-103">Metody <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>i <xref:System.Char.ToLower%2A?displayProperty=nameWithType> zapewniają przeciążenia, które nie akceptują żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="5d3f5-104">Domyślnie te przeciążenia bez parametrów wykonują zmiany wielkości liter na podstawie wartości <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5d3f5-105">Powoduje to generowanie wyników z uwzględnieniem wielkości liter, które mogą się różnić w zależności od kultury.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="5d3f5-106">Aby określić, czy chcesz, aby zmiany wielkości liter były zależne od kultury lub niewrażliwe na kulturę, należy użyć przeciążenia tych metod, które wymagają jawnego określenia parametru `culture`.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="5d3f5-107">W przypadku zmian wielkości liter z uwzględnieniem kultury należy określić `CultureInfo.CurrentCulture` dla parametru `culture`.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="5d3f5-108">W przypadku zmian wielkości liter bez uwzględniania kultur Określ `CultureInfo.InvariantCulture` dla parametru `culture`.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="5d3f5-109">Często ciągi są konwertowane do standardowej wielkości liter, aby ułatwić późniejsze wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="5d3f5-110">Gdy ciągi są używane w ten sposób, należy określić `CultureInfo.InvariantCulture` dla parametru `culture`, ponieważ wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> może ulec zmianie między czasem zmiany wielkości liter i czasem przeszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="5d3f5-111">Jeśli decyzja dotycząca zabezpieczeń jest oparta na operacji zmiany wielkości liter, operacja powinna być niezależna od kultury, aby upewnić się, że wartość `CultureInfo.CurrentCulture`nie wpłynie na wynik.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="5d3f5-112">Zapoznaj się z sekcją "porównania ciągów, które wykorzystują bieżącą kulturę" w artykule [najlepsze rozwiązania dotyczące korzystania z ciągów](../../../docs/standard/base-types/best-practices-strings.md) , aby zapoznać się z przykładem, w jaki sposób operacje na ciągach zależnych od kultury mogą generować niespójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="5d3f5-113">Korzystając z metod String.ToUpper i String.ToLower</span><span class="sxs-lookup"><span data-stu-id="5d3f5-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="5d3f5-114">W przypadku przejrzystości kodu zaleca się, aby zawsze używać przeciążeń `String.ToUpper` i `String.ToLower` metod, które umożliwiają jawne określenie parametru `culture`.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="5d3f5-115">Na przykład poniższy kod wykonuje wyszukiwanie identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="5d3f5-116">Operacja `key.ToLower` domyślnie jest zależna od kultury, ale to zachowanie nie jest jasne w przypadku odczytywania kodu.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="5d3f5-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d3f5-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="5d3f5-118">Jeśli chcesz, aby operacja `key.ToLower` była niezależna od kultury, należy zmienić poprzedni przykład w następujący sposób, aby jawnie użyć `CultureInfo.InvariantCulture` podczas zmieniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="5d3f5-119">Korzystając z metod Char.ToUpper i Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="5d3f5-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="5d3f5-120">Mimo że metody `Char.ToUpper` i `Char.ToLower` mają takie same charakterystyki jak metody `String.ToUpper` i `String.ToLower`, jedynymi kulturami, których dotyczy, są turecki (Turcja) i azerbejdżański (łaciński, Azerbejdżan).</span><span class="sxs-lookup"><span data-stu-id="5d3f5-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="5d3f5-121">Są to jedyne dwie kultury, w których występują różnice dotyczące wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="5d3f5-122">Aby uzyskać więcej informacji o tym unikatowym mapowaniu przypadku, zobacz sekcję "wielkość liter" w temacie klasy <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="5d3f5-123">W przypadku przejrzystości kodu i zapewnienia spójnych wyników zaleca się, aby zawsze używać przeciążeń tych metod, które pozwalają jawnie określić parametr `culture`.</span><span class="sxs-lookup"><span data-stu-id="5d3f5-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3f5-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d3f5-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5d3f5-125">Wykonywanie niezależnych od kultury operacji na ciągach</span><span class="sxs-lookup"><span data-stu-id="5d3f5-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
