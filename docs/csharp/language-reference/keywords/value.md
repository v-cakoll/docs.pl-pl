---
title: value (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: c8f808540385552f6222566f23251f6cbd6e86df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265275"
---
# <a name="value-c-reference"></a><span data-ttu-id="5b5ad-102">value (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5b5ad-102">value (C# Reference)</span></span>
<span data-ttu-id="5b5ad-103">Kontekstowe słowo kluczowe `value` jest używany w metodzie dostępu set w deklaracjach zwykłej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b5ad-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="5b5ad-104">Jest on podobny do parametru wejściowego dla metody.</span><span class="sxs-lookup"><span data-stu-id="5b5ad-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="5b5ad-105">Wyraz `value` odwołuje się do wartości, który próbuje kod klienta można przypisać do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b5ad-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="5b5ad-106">W poniższym przykładzie `MyDerivedClass` ma właściwość o nazwie `Name` używającą `value` parametr, aby przypisać nowe parametry do pola zapasowy `name`.</span><span class="sxs-lookup"><span data-stu-id="5b5ad-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="5b5ad-107">Z punktu widzenia kodu klienta operacji są zapisywane jako przypisanie proste.</span><span class="sxs-lookup"><span data-stu-id="5b5ad-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="5b5ad-108">Aby uzyskać więcej informacji o wykorzystaniu `value`, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="5b5ad-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5b5ad-109">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5b5ad-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b5ad-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b5ad-110">See Also</span></span>  
 [<span data-ttu-id="5b5ad-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="5b5ad-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5b5ad-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5b5ad-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5b5ad-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5b5ad-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
