---
title: Jak jawnie zaimplementować członków interfejsu — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627788"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="27c4e-102">Jak jawnie zaimplementować członków interfejsu (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="27c4e-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="27c4e-103">Ten przykład deklaruje [interfejs](../../language-reference/keywords/interface.md), `IDimensions`i klasę `Box`, która jawnie implementuje elementy członkowskie interfejsu `GetLength` i `GetWidth`.</span><span class="sxs-lookup"><span data-stu-id="27c4e-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="27c4e-104">Dostęp do członków uzyskuje się za pomocą wystąpienia interfejsu `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="27c4e-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27c4e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="27c4e-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="27c4e-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="27c4e-106">Robust Programming</span></span>  
  
- <span data-ttu-id="27c4e-107">Zwróć uwagę, że następujące wiersze w metodzie `Main` są oznaczane jako komentarze, ponieważ spowodują błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="27c4e-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="27c4e-108">Nie można uzyskać dostępu do elementu członkowskiego interfejsu, który jest jawnie zaimplementowany z wystąpienia [klasy](../../language-reference/keywords/class.md) :</span><span class="sxs-lookup"><span data-stu-id="27c4e-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="27c4e-109">Zwróć również uwagę, że następujące wiersze w metodzie `Main` pomyślnie wydrukowały Wymiary pola, ponieważ metody są wywoływane z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="27c4e-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="27c4e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27c4e-110">See also</span></span>

- [<span data-ttu-id="27c4e-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="27c4e-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="27c4e-112">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="27c4e-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="27c4e-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="27c4e-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="27c4e-114">Jak jawnie zaimplementować członków dwóch interfejsów</span><span class="sxs-lookup"><span data-stu-id="27c4e-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
