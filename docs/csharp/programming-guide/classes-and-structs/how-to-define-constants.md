---
title: "Porady: definiowanie stałych w C#"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ff12d0b6882289da9ed924f1c7de00edc5dc1e2e
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="6b218-102">Porady: definiowanie stałych w C#</span><span class="sxs-lookup"><span data-stu-id="6b218-102">How to: Define Constants in C#</span></span>
<span data-ttu-id="6b218-103">Stałe są pól, których wartości są ustawione na czas kompilacji i nie można go zmienić.</span><span class="sxs-lookup"><span data-stu-id="6b218-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="6b218-104">Stałe umożliwia uzyskanie łatwy do rozpoznania nazwy zamiast literałach numerycznych ("numery magic") dla specjalnych wartości.</span><span class="sxs-lookup"><span data-stu-id="6b218-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b218-105">W języku C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora nie może służyć do definiowania stałe w taki sposób, który jest zwykle używany w C i C++.</span><span class="sxs-lookup"><span data-stu-id="6b218-105">In C# the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="6b218-106">Aby zdefiniować wartości stałych typów całkowitych (`int`, `byte`i tak dalej) Użyj typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="6b218-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="6b218-107">Aby uzyskać więcej informacji, zobacz [wyliczenia](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="6b218-107">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="6b218-108">Aby zdefiniować niecałkowity stałe, jednym z podejść jest do grupowania ich w jednej klasy statycznej o nazwie `Constants`.</span><span class="sxs-lookup"><span data-stu-id="6b218-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="6b218-109">Wymaga to czy wszystkie odwołania do stałe być poprzedzona nazwą klasy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6b218-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b218-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b218-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 <span data-ttu-id="6b218-111">Użycie Kwalifikator nazwy klasy pomaga, upewnij się, że użytkowników zastosować stałą rozumiesz jest stała i nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="6b218-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b218-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b218-112">See Also</span></span>  
 [<span data-ttu-id="6b218-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="6b218-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
