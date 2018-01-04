---
title: "Wykonywanie niezależnych od kultury zmian wielkości liter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e65eb85e1355d3aa98e04e7bd73f0194243dcdb1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="ac6d3-102">Wykonywanie niezależnych od kultury zmian wielkości liter</span><span class="sxs-lookup"><span data-stu-id="ac6d3-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="ac6d3-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, I <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody udostępniają przeciążeń, które nie akceptują parametrów.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="ac6d3-104">Domyślnie te przeciążenia bez parametrów wykonują zmiany wielkości liter na podstawie wartości z <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac6d3-105">Daje to wyniki z uwzględnieniem wielkości liter, które zależą od kultury.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="ac6d3-106">Aby umożliwić Wyczyść, czy wielkość zmiany, które mają być zależne od kultury lub niezależnych od kultury, należy używać przeciążeń tych metod, które wymagają jawnie określić `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="ac6d3-107">Zależne od kultury zmian wielkości liter, można określić `CultureInfo.CurrentCulture` dla `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="ac6d3-108">Niezależne od kultury zmian wielkości liter, można określić `CultureInfo.InvariantCulture` dla `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="ac6d3-109">Często ciągi są konwertowane na standardowe wielkości liter, aby włączyć wyszukiwanie łatwiejsze później.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="ac6d3-110">W przypadku używania ciągów w ten sposób można określić `CultureInfo.InvariantCulture` dla `culture` parametru, ponieważ wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> nie może zmienić od godziny, zmieniający wielkość liter podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="ac6d3-111">Jeśli decyzja zabezpieczeń jest oparta na operację zmiany wielkości, operacja powinna być niezależne od kultury aby upewnić się, że wynik nie ma wpływu na wartość `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="ac6d3-112">Zobacz sekcję "Ciąg porównania który Użyj bieżącej kultury" [najlepsze rozwiązania dotyczące ciągów za pomocą](../../../docs/standard/base-types/best-practices-strings.md) artykułu, na przykład, który demonstruje sposób zależne od kultury operacje na ciągach może spowodować niespójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="ac6d3-113">Korzystając z metod String.ToUpper i String.ToLower</span><span class="sxs-lookup"><span data-stu-id="ac6d3-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="ac6d3-114">Dla jasności kodu, zaleca się zawsze używaj przeciążeń `String.ToUpper` i `String.ToLower` metod, które umożliwiają określenie `culture` parametru jawnie.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="ac6d3-115">Na przykład następujący kod przeprowadza wyszukiwanie identyfikator.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="ac6d3-116">`key.ToLower` Operacja jest zależne od kultury domyślnej, ale to zachowanie nie jest jasne, na podstawie odczytu kodu.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ac6d3-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac6d3-117">Example</span></span>  
  
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
  
 <span data-ttu-id="ac6d3-118">Jeśli chcesz `key.ToLower` operacji, uzyskanie niezależnych od kultury, należy zmienić poprzednim przykładzie w następujący sposób, aby jawnie używać `CultureInfo.InvariantCulture` podczas zmiany w przypadku.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="ac6d3-119">Korzystając z metod Char.ToUpper i Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="ac6d3-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="ac6d3-120">Mimo że `Char.ToUpper` i `Char.ToLower` metody mają te same parametry jako `String.ToUpper` i `String.ToLower` metody, tylko kultury, których dotyczy to turecki (Turcja) i Azerbejdżański (łaciński, Azerbejdżan).</span><span class="sxs-lookup"><span data-stu-id="ac6d3-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="ac6d3-121">Są to tylko dwa kultur różnice jednoznakowym wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="ac6d3-122">Aby uzyskać więcej informacji na temat to unikatowy mapowanie przypadków, zobacz sekcję "Wielkości liter" w <xref:System.String> klasy tematu.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="ac6d3-123">Dla jasności kodu i zapewnić spójne wyniki, zaleca się zawsze używaj przeciążeń tych metod, które umożliwiają jawnie określić `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="ac6d3-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac6d3-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac6d3-124">See Also</span></span>  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="ac6d3-125">Wykonywanie niezależnych od kultury operacji na ciągach</span><span class="sxs-lookup"><span data-stu-id="ac6d3-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
