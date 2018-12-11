---
title: wartość — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: f0b9e2927eb288a27f926a740a967742b8cdaa9e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236469"
---
# <a name="value-c-reference"></a><span data-ttu-id="feb7c-102">value (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="feb7c-102">value (C# Reference)</span></span>
<span data-ttu-id="feb7c-103">Kontekstowe słowo kluczowe `value` jest używany w metodzie dostępu set w deklaracji właściwości zwykłych.</span><span class="sxs-lookup"><span data-stu-id="feb7c-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="feb7c-104">Jest on podobny do parametru wejściowego metody.</span><span class="sxs-lookup"><span data-stu-id="feb7c-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="feb7c-105">Wyraz `value` odwołuje się do wartości, które podejmuje próbę przypisania do właściwości kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="feb7c-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="feb7c-106">W poniższym przykładzie `MyDerivedClass` ma właściwość o nazwie `Name` , który używa `value` parametru, aby przypisać nowy ciąg do pola pomocniczego `name`.</span><span class="sxs-lookup"><span data-stu-id="feb7c-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="feb7c-107">Z punktu widzenia kodu klienta operacji jest zapisywany jako przypisanie proste.</span><span class="sxs-lookup"><span data-stu-id="feb7c-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="feb7c-108">Aby uzyskać więcej informacji na temat użytkowania `value`, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="feb7c-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="feb7c-109">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="feb7c-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="feb7c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="feb7c-110">See Also</span></span>

- [<span data-ttu-id="feb7c-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="feb7c-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="feb7c-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="feb7c-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="feb7c-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="feb7c-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
