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
ms.openlocfilehash: 7b2dee03619e24c5a2845699a06e88abab0c594b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160134"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="5b084-102">Wykonywanie niezależnych od kultury zmian wielkości liter</span><span class="sxs-lookup"><span data-stu-id="5b084-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="5b084-103">, <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>i <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody zapewniają przeciążenia, które nie akceptują żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="5b084-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="5b084-104">Domyślnie te przeciążenia bez parametrów wykonują zmiany przypadków <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>na podstawie wartości .</span><span class="sxs-lookup"><span data-stu-id="5b084-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5b084-105">Daje to wyniki z uwzględnieniem wielkości liter, które mogą się różnić w zależności od kultury.</span><span class="sxs-lookup"><span data-stu-id="5b084-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="5b084-106">Aby było jasne, czy zmiany wielkości liter mają być zależne od kultury lub kultury niewrażliwe, należy użyć przeciążenia tych metod, które wymagają jawnie określić `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="5b084-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="5b084-107">W przypadku zmian wielkości `CultureInfo.CurrentCulture` liter `culture` uwzględniających kulturę określ parametr.</span><span class="sxs-lookup"><span data-stu-id="5b084-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="5b084-108">W przypadku zmian wielkości liter `CultureInfo.InvariantCulture` nieuwzględniających kulturę określ parametr. `culture`</span><span class="sxs-lookup"><span data-stu-id="5b084-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="5b084-109">Często ciągi są konwertowane na standardowy przypadek, aby umożliwić łatwiejsze późniejsze odszukanie.</span><span class="sxs-lookup"><span data-stu-id="5b084-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="5b084-110">Gdy ciągi są używane w ten `CultureInfo.InvariantCulture` sposób, należy określić dla parametru, `culture` ponieważ wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> może ulec zmianie między czasem, że sprawa jest zmieniana i czas, w którym występuje odciąganie.</span><span class="sxs-lookup"><span data-stu-id="5b084-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="5b084-111">Jeśli decyzja o zabezpieczeniach jest oparta na operacji zmiany przypadku, operacja powinna być niewrażliwa `CultureInfo.CurrentCulture`na kulturę, aby upewnić się, że wartość wyniku nie ma wpływu na wynik .</span><span class="sxs-lookup"><span data-stu-id="5b084-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="5b084-112">Zobacz "Porównania ciągów, które używają bieżącej kultury" sekcji [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md) artykułu na przykład, który pokazuje, jak operacje ciągów zależnych od kultury może powodować niespójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="5b084-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="5b084-113">Korzystając z metod String.ToUpper i String.ToLower</span><span class="sxs-lookup"><span data-stu-id="5b084-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="5b084-114">Dla jasności kodu zaleca się, aby zawsze używać `String.ToUpper` `String.ToLower` przeciążenia i metody, `culture` które umożliwiają jawnie określić parametr.</span><span class="sxs-lookup"><span data-stu-id="5b084-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="5b084-115">Na przykład poniższy kod wykonuje wyszukiwania identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5b084-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="5b084-116">Operacja `key.ToLower` jest domyślnie zależne od kultury, ale to zachowanie nie jest jasne z czytania kodu.</span><span class="sxs-lookup"><span data-stu-id="5b084-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="5b084-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b084-117">Example</span></span>  
  
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
  
 <span data-ttu-id="5b084-118">Jeśli `key.ToLower` chcesz, aby operacja była niewrażliwa na kulturę, należy zmienić poprzedni `CultureInfo.InvariantCulture` przykład w następujący sposób, aby jawnie użyć podczas zmiany sprawy.</span><span class="sxs-lookup"><span data-stu-id="5b084-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="5b084-119">Korzystając z metod Char.ToUpper i Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="5b084-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="5b084-120">Chociaż `Char.ToUpper` i `Char.ToLower` metody mają takie same `String.ToUpper` cechy `String.ToLower` jak i metody, jedynymi kulturami, których to dotyczy, są tureckie (Turcja) i Azerbejdżan (łaciński, Azerbejdżan).</span><span class="sxs-lookup"><span data-stu-id="5b084-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="5b084-121">Są to jedyne dwie kultury z jednopostaciowymi różnicami w obudowie.</span><span class="sxs-lookup"><span data-stu-id="5b084-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="5b084-122">Aby uzyskać więcej informacji na temat tego unikatowego <xref:System.String> mapowania wielkości liter, zobacz sekcję "Obudowa" w temacie klasy.</span><span class="sxs-lookup"><span data-stu-id="5b084-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="5b084-123">Dla jasności kodu i zapewnienia spójnych wyników zaleca się, aby zawsze używać przeciążenia tych `culture` metod, które umożliwiają jawnie określić parametr.</span><span class="sxs-lookup"><span data-stu-id="5b084-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b084-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b084-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5b084-125">Wykonywanie niezależnych od kultury operacji na ciągach</span><span class="sxs-lookup"><span data-stu-id="5b084-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
