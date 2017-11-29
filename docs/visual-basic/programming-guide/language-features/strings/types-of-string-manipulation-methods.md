---
title: "Typy metod manipulowania ciągami w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b437be4a6f4a0cc9d5a4d21291a80c9cb8fffcd3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="10332-102">Typy metod manipulowania ciągami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10332-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="10332-103">Istnieje kilka różnych sposobów do analizowania i manipulowania z ciągów.</span><span class="sxs-lookup"><span data-stu-id="10332-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="10332-104">Niektóre metody są częścią [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] język, a inne są związane z `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="10332-104">Some of the methods are a part of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="10332-105">Język Visual Basic i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="10332-105">Visual Basic Language and the .NET Framework</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="10332-106">metody są używane jako funkcje związanego z używaniem języka.</span><span class="sxs-lookup"><span data-stu-id="10332-106"> methods are used as inherent functions of the language.</span></span> <span data-ttu-id="10332-107">Mogą one używane, bez kwalifikacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="10332-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="10332-108">W poniższym przykładzie przedstawiono typowy sposób użycia protokołu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] manipulowanie ciągami polecenia:</span><span class="sxs-lookup"><span data-stu-id="10332-108">The following example shows typical use of a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 <span data-ttu-id="10332-109">W tym przykładzie `Mid` funkcja wykonuje operację bezpośrednio na `aString` i przypisuje wartość do `bString`.</span><span class="sxs-lookup"><span data-stu-id="10332-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="10332-110">Aby uzyskać listę metod manipulowania ciągami w Visual Basic, zobacz [manipulowanie ciągami — Podsumowanie](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="10332-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="10332-111">Metody udostępnionego i wystąpienie metody</span><span class="sxs-lookup"><span data-stu-id="10332-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="10332-112">Można również manipulować ciągów z metody `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="10332-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="10332-113">Istnieją dwa typy metod w `String`: *udostępnionego* metod i *wystąpienia* metody.</span><span class="sxs-lookup"><span data-stu-id="10332-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="10332-114">Metody udostępnionego</span><span class="sxs-lookup"><span data-stu-id="10332-114">Shared Methods</span></span>  
 <span data-ttu-id="10332-115">Udostępnionej metody to metoda, która wynika ze `String` samej klasy i nie wymaga wystąpienia tej klasy do pracy.</span><span class="sxs-lookup"><span data-stu-id="10332-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="10332-116">Te metody mogą być kwalifikowany za pomocą nazwy klasy (`String`), a nie z wystąpieniem `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="10332-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="10332-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="10332-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 <span data-ttu-id="10332-118">W powyższym przykładzie <xref:System.String.Copy%2A?displayProperty=nameWithType> metoda jest metodą statyczną, który działa na wyrażeniu go otrzymuje i przypisuje wynikowej wartości do `bString`.</span><span class="sxs-lookup"><span data-stu-id="10332-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="10332-119">Wystąpienie metody</span><span class="sxs-lookup"><span data-stu-id="10332-119">Instance Methods</span></span>  
 <span data-ttu-id="10332-120">Wystąpienie metody, natomiast wynika z konkretnego wystąpienia `String` i musi być kwalifikowany za pomocą nazwy obiektu.</span><span class="sxs-lookup"><span data-stu-id="10332-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="10332-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="10332-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 <span data-ttu-id="10332-122">W tym przykładzie <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda jest metodą wystąpienia `String` (czyli `aString`).</span><span class="sxs-lookup"><span data-stu-id="10332-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="10332-123">Wykonuje operację na `aString` i przypisuje wartość tego `bString`.</span><span class="sxs-lookup"><span data-stu-id="10332-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="10332-124">Aby uzyskać więcej informacji, zobacz dokumentację <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="10332-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10332-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10332-125">See Also</span></span>  
 [<span data-ttu-id="10332-126">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10332-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
