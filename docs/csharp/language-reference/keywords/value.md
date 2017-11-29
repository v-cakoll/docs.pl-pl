---
title: "value (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: value_CSharpKeyword
helpviewer_keywords: value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2501bc8964ed76534dba6c7cc519e095c57cb898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="value-c-reference"></a><span data-ttu-id="1b0f9-102">value (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1b0f9-102">value (C# Reference)</span></span>
<span data-ttu-id="1b0f9-103">Kontekstowe słowo kluczowe `value` jest używany w metodzie dostępu set w deklaracjach zwykłej właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b0f9-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="1b0f9-104">Jest on podobny do parametru wejściowego dla metody.</span><span class="sxs-lookup"><span data-stu-id="1b0f9-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="1b0f9-105">Wyraz `value` odwołuje się do wartości, który próbuje kod klienta można przypisać do właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b0f9-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="1b0f9-106">W poniższym przykładzie `MyDerivedClass` ma właściwość o nazwie `Name` używającą `value` parametr, aby przypisać nowe parametry do pola zapasowy `name`.</span><span class="sxs-lookup"><span data-stu-id="1b0f9-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="1b0f9-107">Z punktu widzenia kodu klienta operacji są zapisywane jako przypisanie proste.</span><span class="sxs-lookup"><span data-stu-id="1b0f9-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="1b0f9-108">Aby uzyskać więcej informacji o wykorzystaniu `value`, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="1b0f9-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1b0f9-109">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1b0f9-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1b0f9-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b0f9-110">See Also</span></span>  
 [<span data-ttu-id="1b0f9-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="1b0f9-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1b0f9-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1b0f9-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1b0f9-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1b0f9-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
