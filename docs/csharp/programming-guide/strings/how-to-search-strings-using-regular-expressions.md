---
title: "Porady: wyszukiwanie ciągów za pomocą wyrażeń regularnych (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c851c57b44f1343816b905db002e530121fb6c0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a><span data-ttu-id="01f01-102">Porady: wyszukiwanie ciągów za pomocą wyrażeń regularnych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="01f01-102">How to: Search Strings Using Regular Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="01f01-103"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Klasa może być używana do wyszukiwania ciągów.</span><span class="sxs-lookup"><span data-stu-id="01f01-103">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="01f01-104">Te wyszukiwania można dostosować w zakresie w złożoności pełnego wykorzystania wyrażeń regularnych z bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="01f01-104">These searches can range in complexity from very simple to making full use of regular expressions.</span></span> <span data-ttu-id="01f01-105">Poniżej przedstawiono dwa przykłady ciąg wyszukiwania przy użyciu <xref:System.Text.RegularExpressions.Regex> klasy.</span><span class="sxs-lookup"><span data-stu-id="01f01-105">The following are two examples of string searching by using the <xref:System.Text.RegularExpressions.Regex> class.</span></span> <span data-ttu-id="01f01-106">Aby uzyskać więcej informacji, zobacz [wyrażeń regularnych programu .NET Framework](https://msdn.microsoft.com/library/hs600312).</span><span class="sxs-lookup"><span data-stu-id="01f01-106">For more information, see [.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01f01-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="01f01-107">Example</span></span>  
 <span data-ttu-id="01f01-108">Następujący kod jest aplikacja konsolowa, która wykonuje proste wyszukiwanie bez uwzględniania wielkości liter ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="01f01-108">The following code is a console application that performs a simple case-insensitive search of the strings in an array.</span></span> <span data-ttu-id="01f01-109">Statyczna metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> wykonuje wyszukiwanie podany ciąg do wyszukania i ciąg, który zawiera wzorzec wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="01f01-109">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search given the string to search and a string that contains the search pattern.</span></span> <span data-ttu-id="01f01-110">W takim przypadku trzeci argument jest służy do wskazania, wielkość liter powinna być ignorowana.</span><span class="sxs-lookup"><span data-stu-id="01f01-110">In this case, a third argument is used to indicate that case should be ignored.</span></span> <span data-ttu-id="01f01-111">Aby uzyskać więcej informacji, zobacz <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01f01-111">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="01f01-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="01f01-112">Example</span></span>  
 <span data-ttu-id="01f01-113">Następujący kod jest aplikacja konsolowa, która używa wyrażeń regularnych do walidacji format każdego ciągu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="01f01-113">The following code is a console application that uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="01f01-114">Wymaga weryfikacji każdy ciąg formę numeru telefonu, w którym trzech grup cyfr są oddzielone kreskami, najpierw dwie grupy zawiera trzy cyfry i trzecia grupa zawiera cztery cyfry.</span><span class="sxs-lookup"><span data-stu-id="01f01-114">The validation requires that each string take the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="01f01-115">Jest to zrobić za pomocą wyrażenia regularnego `^\\d{3}-\\d{3}-\\d{4}$`.</span><span class="sxs-lookup"><span data-stu-id="01f01-115">This is done by using the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="01f01-116">Aby uzyskać więcej informacji, zobacz [język wyrażeń regularnych — podręczny wykaz](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span><span class="sxs-lookup"><span data-stu-id="01f01-116">For more information, see [Regular Expression Language - Quick Reference](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span></span>  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="01f01-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01f01-117">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [<span data-ttu-id="01f01-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="01f01-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="01f01-119">Ciągi</span><span class="sxs-lookup"><span data-stu-id="01f01-119">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="01f01-120">.NET framework — nieprawidłowe wyrażenia</span><span class="sxs-lookup"><span data-stu-id="01f01-120">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)  
 [<span data-ttu-id="01f01-121">Język wyrażeń regularnych — podręczny wykaz</span><span class="sxs-lookup"><span data-stu-id="01f01-121">Regular Expression Language - Quick Reference</span></span>](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
