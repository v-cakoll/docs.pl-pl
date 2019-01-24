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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04601ac0e6b1bc3289be36ce3e1a144ce57ccefb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550516"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="fa13e-102">Wykonywanie niezależnych od kultury zmian wielkości liter</span><span class="sxs-lookup"><span data-stu-id="fa13e-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="fa13e-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, I <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metod, zapewnienia przeciążenia, które nie akceptują parametrów.</span><span class="sxs-lookup"><span data-stu-id="fa13e-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="fa13e-104">Domyślnie te przeciążenia bez parametrów wykonywania przypadków zmienia się zależnie od wartości <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa13e-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fa13e-105">To daje wyniki uwzględniana wielkość liter, które mogą się różnić od kultury.</span><span class="sxs-lookup"><span data-stu-id="fa13e-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="fa13e-106">Aby umożliwić jednoznacznie wskazuje, czy chcesz, aby zmiany wielkości liter kultury lub niewrażliwość na ustawienia kulturowe, należy używać przeciążenia tych metod, które wymagają jawnie określić `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="fa13e-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="fa13e-107">Zależne od kultury zmian wielkości liter, określ `CultureInfo.CurrentCulture` dla `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="fa13e-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="fa13e-108">W przypadku niezależnych od kultury zmian wielkości liter, określić `CultureInfo.InvariantCulture` dla `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="fa13e-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="fa13e-109">Często ciągi są konwertowane na standardowym przypadku można włączyć później ułatwić wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="fa13e-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="fa13e-110">Jeśli ciągi są używane w ten sposób, należy określić `CultureInfo.InvariantCulture` dla `culture` parametru, ponieważ wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> potencjalnie może się zmieniać między zostanie zmieniony tak czas i czas, który występuje wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="fa13e-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="fa13e-111">Jeśli decyzja dot. zabezpieczeń opiera się na operację zmiany sprawy, operacja nie powinna zależeć od kultury upewnij się, że wynik nie wpływa wartość `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="fa13e-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="fa13e-112">Zobacz sekcję "Ciągów porównań, użyj bieżącej kultury" [najlepsze rozwiązania dotyczące Using Strings](../../../docs/standard/base-types/best-practices-strings.md) artykuł dla przykładu, który demonstruje sposób zależne od kultury operacje na ciągach mogą generować niespójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="fa13e-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="fa13e-113">Korzystając z metod String.ToUpper i String.ToLower</span><span class="sxs-lookup"><span data-stu-id="fa13e-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="fa13e-114">Czystości kodu zaleca się używanie przeciążenia `String.ToUpper` i `String.ToLower` metod, które pozwalają na określenie `culture` parametru jawnie.</span><span class="sxs-lookup"><span data-stu-id="fa13e-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="fa13e-115">Na przykład poniższy kod przeprowadza wyszukiwanie identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="fa13e-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="fa13e-116">`key.ToLower` Operacja jest zależne od kultury domyślnej, ale to zachowanie nie jest jasne, z kodu.</span><span class="sxs-lookup"><span data-stu-id="fa13e-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="fa13e-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa13e-117">Example</span></span>  
  
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
  
 <span data-ttu-id="fa13e-118">Jeśli chcesz `key.ToLower` operację, aby być uwzględniana kultura, należy zmienić poprzedni przykład, w następujący sposób, aby jawnie użyć `CultureInfo.InvariantCulture` podczas zmiany sprawy.</span><span class="sxs-lookup"><span data-stu-id="fa13e-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="fa13e-119">Korzystając z metod Char.ToUpper i Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="fa13e-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="fa13e-120">Mimo że `Char.ToUpper` i `Char.ToLower` metody mają takie same charakterystyki jak `String.ToUpper` i `String.ToLower` metod, tylko kultur, które wpływają na to, turecki (Turcja) i Azerbejdżański (łaciński, Azerbejdżan).</span><span class="sxs-lookup"><span data-stu-id="fa13e-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="fa13e-121">Są to tylko dwie kultury z różnicami wielkość liter w wyrazie pojedynczych znaków.</span><span class="sxs-lookup"><span data-stu-id="fa13e-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="fa13e-122">Aby uzyskać więcej informacji na temat to unikatowy mapowanie przypadków, zobacz sekcję "Wielkość liter w wyrazie" w <xref:System.String> temat poświęcony klasie.</span><span class="sxs-lookup"><span data-stu-id="fa13e-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="fa13e-123">Czystości kodu i zapewnić spójne wyniki, zaleca się zawsze używaj przeciążenia tych metod, które pozwalają na określenie jawnie `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="fa13e-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa13e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa13e-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fa13e-125">Wykonywanie niezależnych od kultury operacji na ciągach</span><span class="sxs-lookup"><span data-stu-id="fa13e-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
