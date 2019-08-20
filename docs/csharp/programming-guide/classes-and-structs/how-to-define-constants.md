---
title: 'Instrukcje: Definiowanie stałych w języku C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 5ef5e3622840e69175163461a06f6b0de31231f9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596888"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="e7e8f-102">Instrukcje: Definiowanie stałych w języku C\#</span><span class="sxs-lookup"><span data-stu-id="e7e8f-102">How to: Define Constants in C\#</span></span>
<span data-ttu-id="e7e8f-103">Stałe są polami, których wartości są ustawiane w czasie kompilacji i nigdy nie mogą być zmieniane.</span><span class="sxs-lookup"><span data-stu-id="e7e8f-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="e7e8f-104">Użyj stałych, aby podać znaczące nazwy zamiast literałów liczbowych ("liczby magiczne") dla specjalnych wartości.</span><span class="sxs-lookup"><span data-stu-id="e7e8f-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7e8f-105">W C# dyrektywie preprocesora [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) nie można używać do definiowania stałych w sposób, który jest zazwyczaj używany w C i C++.</span><span class="sxs-lookup"><span data-stu-id="e7e8f-105">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="e7e8f-106">Aby zdefiniować stałe wartości typów całkowitych (`int`, `byte`, i tak dalej), użyj typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="e7e8f-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="e7e8f-107">Aby uzyskać więcej informacji, zobacz [Wyliczenie](../../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="e7e8f-107">For more information, see [enum](../../language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="e7e8f-108">Aby zdefiniować niecałkowite stałe, jedno podejście polega na pogrupowania ich w pojedynczej klasie statycznej o nazwie `Constants`.</span><span class="sxs-lookup"><span data-stu-id="e7e8f-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="e7e8f-109">To wymaga, aby wszystkie odwołania do stałych były poprzedzone nazwą klasy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e7e8f-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7e8f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7e8f-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="e7e8f-111">Użycie kwalifikatora nazwy klasy pomaga upewnić się, że i inne osoby, które używają stałej, wiedzą, że jest stała i nie mogą być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="e7e8f-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e8f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7e8f-112">See also</span></span>

- [<span data-ttu-id="e7e8f-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="e7e8f-113">Classes and Structs</span></span>](./index.md)
