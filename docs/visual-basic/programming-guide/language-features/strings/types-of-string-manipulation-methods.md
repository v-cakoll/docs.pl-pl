---
title: Typy metod manipulowania ciągami w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a75984d0eb64ef8c18def3ae59d5e1f4b6d20ce2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980350"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="08aaf-102">Typy metod manipulowania ciągami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08aaf-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="08aaf-103">Istnieją różne sposoby analizować ciągów i manipulowania nimi sieci.</span><span class="sxs-lookup"><span data-stu-id="08aaf-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="08aaf-104">Niektóre metody są częścią języka Visual Basic, a inne są integralną częścią `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="08aaf-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="08aaf-105">Język Visual Basic i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="08aaf-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="08aaf-106">Metody języka Visual Basic są używane jako związane funkcje języka.</span><span class="sxs-lookup"><span data-stu-id="08aaf-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="08aaf-107">Mogą one być używane bez kwalifikacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="08aaf-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="08aaf-108">Typowym zastosowaniem polecenia manipulowanie ciągami języka Visual Basic można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="08aaf-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="08aaf-109">W tym przykładzie `Mid` funkcja wykonuje operację bezpośrednie na `aString` i przypisuje wartość do `bString`.</span><span class="sxs-lookup"><span data-stu-id="08aaf-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="08aaf-110">Aby uzyskać listę metod manipulowania ciągami języka Visual Basic, zobacz [manipulowanie ciągami — Podsumowanie](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="08aaf-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="08aaf-111">Udostępnione metody i metody wystąpienia</span><span class="sxs-lookup"><span data-stu-id="08aaf-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="08aaf-112">Można również manipulowania ciągami za pomocą metody `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="08aaf-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="08aaf-113">Istnieją dwa typy metod w `String`: *udostępnionego* metod i *wystąpienia* metody.</span><span class="sxs-lookup"><span data-stu-id="08aaf-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="08aaf-114">Udostępnione metody</span><span class="sxs-lookup"><span data-stu-id="08aaf-114">Shared Methods</span></span>  
 <span data-ttu-id="08aaf-115">Udostępnione metoda jest metodą, która wynika z `String` samej klasy i nie wymaga wystąpienia tej klasy do pracy.</span><span class="sxs-lookup"><span data-stu-id="08aaf-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="08aaf-116">Te metody mogą być kwalifikowana nazwą klasy (`String`), a nie z wystąpieniem `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="08aaf-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="08aaf-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="08aaf-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="08aaf-118">W powyższym przykładzie <xref:System.String.Copy%2A?displayProperty=nameWithType> metoda jest metodą statyczną, który działa na wyrażenie go otrzymuje i przypisuje wartość wynikową do `bString`.</span><span class="sxs-lookup"><span data-stu-id="08aaf-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="08aaf-119">Metody wystąpienia</span><span class="sxs-lookup"><span data-stu-id="08aaf-119">Instance Methods</span></span>  
 <span data-ttu-id="08aaf-120">Metody wystąpienia, z kolei wynika z konkretnego wystąpienia `String` i musi być kwalifikowana nazwą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="08aaf-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="08aaf-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="08aaf-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="08aaf-122">W tym przykładzie <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda jest metodą wystąpienia `String` (czyli `aString`).</span><span class="sxs-lookup"><span data-stu-id="08aaf-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="08aaf-123">Wykonuje operację na `aString` i przypisuje wartość do `bString`.</span><span class="sxs-lookup"><span data-stu-id="08aaf-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="08aaf-124">Aby uzyskać więcej informacji, zobacz dokumentację dla <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="08aaf-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08aaf-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08aaf-125">See also</span></span>
- [<span data-ttu-id="08aaf-126">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08aaf-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
