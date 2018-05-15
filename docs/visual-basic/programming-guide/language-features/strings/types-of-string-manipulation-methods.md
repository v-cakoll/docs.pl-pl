---
title: Typy metod manipulowania ciągami w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 11903e067c064f129ecd2df80244edb6741c73be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="32fef-102">Typy metod manipulowania ciągami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32fef-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="32fef-103">Istnieje kilka różnych sposobów do analizowania i manipulowania z ciągów.</span><span class="sxs-lookup"><span data-stu-id="32fef-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="32fef-104">Niektóre metody są częścią języka Visual Basic, a inne są związane z `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="32fef-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="32fef-105">Język Visual Basic i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32fef-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="32fef-106">Metody języka Visual Basic są używane jako funkcje związanego z używaniem języka.</span><span class="sxs-lookup"><span data-stu-id="32fef-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="32fef-107">Mogą one używane, bez kwalifikacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="32fef-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="32fef-108">W poniższym przykładzie przedstawiono typowy sposób użycia polecenia manipulowanie ciągami Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="32fef-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 <span data-ttu-id="32fef-109">W tym przykładzie `Mid` funkcja wykonuje operację bezpośrednio na `aString` i przypisuje wartość do `bString`.</span><span class="sxs-lookup"><span data-stu-id="32fef-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="32fef-110">Aby uzyskać listę metod manipulowania ciągami w Visual Basic, zobacz [manipulowanie ciągami — Podsumowanie](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="32fef-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="32fef-111">Metody udostępnionego i wystąpienie metody</span><span class="sxs-lookup"><span data-stu-id="32fef-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="32fef-112">Można również manipulować ciągów z metody `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="32fef-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="32fef-113">Istnieją dwa typy metod w `String`: *udostępnionego* metod i *wystąpienia* metody.</span><span class="sxs-lookup"><span data-stu-id="32fef-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="32fef-114">Metody udostępnionego</span><span class="sxs-lookup"><span data-stu-id="32fef-114">Shared Methods</span></span>  
 <span data-ttu-id="32fef-115">Udostępnionej metody to metoda, która wynika ze `String` samej klasy i nie wymaga wystąpienia tej klasy do pracy.</span><span class="sxs-lookup"><span data-stu-id="32fef-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="32fef-116">Te metody mogą być kwalifikowany za pomocą nazwy klasy (`String`), a nie z wystąpieniem `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="32fef-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="32fef-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="32fef-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 <span data-ttu-id="32fef-118">W powyższym przykładzie <xref:System.String.Copy%2A?displayProperty=nameWithType> metoda jest metodą statyczną, który działa na wyrażeniu go otrzymuje i przypisuje wynikowej wartości do `bString`.</span><span class="sxs-lookup"><span data-stu-id="32fef-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="32fef-119">Wystąpienie metody</span><span class="sxs-lookup"><span data-stu-id="32fef-119">Instance Methods</span></span>  
 <span data-ttu-id="32fef-120">Wystąpienie metody, natomiast wynika z konkretnego wystąpienia `String` i musi być kwalifikowany za pomocą nazwy obiektu.</span><span class="sxs-lookup"><span data-stu-id="32fef-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="32fef-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="32fef-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 <span data-ttu-id="32fef-122">W tym przykładzie <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda jest metodą wystąpienia `String` (czyli `aString`).</span><span class="sxs-lookup"><span data-stu-id="32fef-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="32fef-123">Wykonuje operację na `aString` i przypisuje wartość tego `bString`.</span><span class="sxs-lookup"><span data-stu-id="32fef-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="32fef-124">Aby uzyskać więcej informacji, zobacz dokumentację <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="32fef-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fef-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32fef-125">See Also</span></span>  
 [<span data-ttu-id="32fef-126">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32fef-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
