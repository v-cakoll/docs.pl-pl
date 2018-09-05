---
title: 'Porady: definiowanie stałych w C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 09d19f708570b55509a3ec2a41e439cb9c9de973
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540235"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="e0abf-102">Porady: definiowanie stałych w C#</span><span class="sxs-lookup"><span data-stu-id="e0abf-102">How to: Define Constants in C#</span></span>
<span data-ttu-id="e0abf-103">Stałe są pola, których wartości są ustawione na czas kompilacji i nie można go zmienić.</span><span class="sxs-lookup"><span data-stu-id="e0abf-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="e0abf-104">Użyj stałych zapewnienie nazw opisowych, zamiast literałów numerycznych ("numery magic") dla specjalnych wartości.</span><span class="sxs-lookup"><span data-stu-id="e0abf-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0abf-105">W języku C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora, nie może służyć do definiowania stałych w taki sposób, który jest zazwyczaj używany w językach C i C++.</span><span class="sxs-lookup"><span data-stu-id="e0abf-105">In C# the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="e0abf-106">Do definiowania wartości stałych typów całkowitych (`int`, `byte`i tak dalej) Użyj typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="e0abf-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="e0abf-107">Aby uzyskać więcej informacji, zobacz [wyliczenia](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="e0abf-107">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="e0abf-108">Aby określić stałe całkowite inne niż, jednym z podejść jest aby je pogrupować w jednej klasie statycznej o nazwie `Constants`.</span><span class="sxs-lookup"><span data-stu-id="e0abf-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="e0abf-109">Wymaga to czy wszystkie odwołania do stałych być poprzedzona nazwą klasy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e0abf-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0abf-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0abf-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 <span data-ttu-id="e0abf-111">Użycie kwalifikatora Nazwa klasy pomaga upewnić się, że Ty i inni korzystającymi z stała zna jest stała i nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="e0abf-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0abf-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0abf-112">See Also</span></span>

- [<span data-ttu-id="e0abf-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="e0abf-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
