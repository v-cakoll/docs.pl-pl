---
title: Jak jawnie implementować elementy członkowskie interfejsu - Przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627788"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="ae1be-102">Jak jawnie implementować elementy członkowskie interfejsu (Przewodnik programowania Języka C#)</span><span class="sxs-lookup"><span data-stu-id="ae1be-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="ae1be-103">W tym przykładzie [interface](../../language-reference/keywords/interface.md)deklaruje `IDimensions`interfejs , `Box`i klasy , który jawnie implementuje elementy członkowskie `GetLength` interfejsu i `GetWidth`.</span><span class="sxs-lookup"><span data-stu-id="ae1be-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="ae1be-104">Elementy członkowskie są dostępne za `dimensions`pośrednictwem wystąpienia interfejsu .</span><span class="sxs-lookup"><span data-stu-id="ae1be-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae1be-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae1be-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ae1be-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ae1be-106">Robust Programming</span></span>  
  
- <span data-ttu-id="ae1be-107">Należy zauważyć, że następujące `Main` wiersze, w metodzie, są komentowane, ponieważ mogą one powodować błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ae1be-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="ae1be-108">Nie można uzyskać dostępu do elementu członkowskiego interfejsu, który jest jawnie zaimplementowany z wystąpienia [klasy:](../../language-reference/keywords/class.md)</span><span class="sxs-lookup"><span data-stu-id="ae1be-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="ae1be-109">Należy również zauważyć, że `Main` następujące wiersze w metodzie pomyślnie wydrukować wymiary pola, ponieważ metody są wywoływane z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="ae1be-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="ae1be-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae1be-110">See also</span></span>

- [<span data-ttu-id="ae1be-111">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ae1be-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ae1be-112">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="ae1be-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="ae1be-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ae1be-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="ae1be-114">Jawne implementowanie elementów dwóch interfejsów</span><span class="sxs-lookup"><span data-stu-id="ae1be-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
