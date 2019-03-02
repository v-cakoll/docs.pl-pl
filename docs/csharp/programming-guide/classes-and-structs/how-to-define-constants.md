---
title: 'Instrukcje: Definiowanie stałych wC#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: a85e7728512922be38658c07314229c26b2461fd
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201472"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="4a21f-102">Instrukcje: Definiowanie stałych w C\#</span><span class="sxs-lookup"><span data-stu-id="4a21f-102">How to: Define Constants in C\#</span></span>
<span data-ttu-id="4a21f-103">Stałe są pola, których wartości są ustawione na czas kompilacji i nie można go zmienić.</span><span class="sxs-lookup"><span data-stu-id="4a21f-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="4a21f-104">Użyj stałych zapewnienie nazw opisowych, zamiast literałów numerycznych ("numery magic") dla specjalnych wartości.</span><span class="sxs-lookup"><span data-stu-id="4a21f-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a21f-105">W języku C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora, nie może służyć do definiowania stałych w taki sposób, który jest zazwyczaj używany w językach C i C++.</span><span class="sxs-lookup"><span data-stu-id="4a21f-105">In C# the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="4a21f-106">Do definiowania wartości stałych typów całkowitych (`int`, `byte`i tak dalej) Użyj typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="4a21f-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="4a21f-107">Aby uzyskać więcej informacji, zobacz [wyliczenia](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="4a21f-107">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="4a21f-108">Aby określić stałe całkowite inne niż, jednym z podejść jest aby je pogrupować w jednej klasie statycznej o nazwie `Constants`.</span><span class="sxs-lookup"><span data-stu-id="4a21f-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="4a21f-109">Wymaga to czy wszystkie odwołania do stałych być poprzedzona nazwą klasy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4a21f-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a21f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a21f-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="4a21f-111">Użycie kwalifikatora Nazwa klasy pomaga upewnić się, że Ty i inni korzystającymi z stała zna jest stała i nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="4a21f-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a21f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a21f-112">See also</span></span>

- [<span data-ttu-id="4a21f-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="4a21f-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
