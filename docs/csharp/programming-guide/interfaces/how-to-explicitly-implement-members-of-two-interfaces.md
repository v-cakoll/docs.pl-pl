---
title: 'Porady: jawne implementowanie elementów dwóch interfejsów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c73089fdbf1350c1aff68ac3e8e78be00e21b931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339043"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="1dc7b-102">Porady: jawne implementowanie elementów dwóch interfejsów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1dc7b-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="1dc7b-103">Jawne [interfejsu](../../../csharp/language-reference/keywords/interface.md) implementacji umożliwia również programisty do zaimplementowania dwa interfejsy tej samej nazwy elementów członkowskich, które zapewniają każdy element członkowski interfejsu oddzielne implementacji.</span><span class="sxs-lookup"><span data-stu-id="1dc7b-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="1dc7b-104">W tym przykładzie wyświetla rozmiary pola w metryki i jednostki w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="1dc7b-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="1dc7b-105">Pole [klasy](../../../csharp/language-reference/keywords/class.md) implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, reprezentujące różne systemy miary.</span><span class="sxs-lookup"><span data-stu-id="1dc7b-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="1dc7b-106">Oba interfejsy mają nazwy identyczne elementu członkowskiego, długość i szerokość.</span><span class="sxs-lookup"><span data-stu-id="1dc7b-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dc7b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1dc7b-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1dc7b-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1dc7b-108">Robust Programming</span></span>  
 <span data-ttu-id="1dc7b-109">Jeśli mają być pomiarów domyślne w angielskiej wersji językowej jednostki, zwykle implementuje metody długości i szerokości i jawnie implementować metody długości i szerokości przy użyciu interfejsu IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="1dc7b-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 <span data-ttu-id="1dc7b-110">W takim przypadku angielskiej wersji językowej jednostki z wystąpienia klasy i dostępne uzyskiwać dostęp do jednostki metryki z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="1dc7b-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1dc7b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1dc7b-111">See Also</span></span>  
 [<span data-ttu-id="1dc7b-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1dc7b-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1dc7b-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="1dc7b-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="1dc7b-114">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1dc7b-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="1dc7b-115">Instrukcje: jawne implementowanie elementów interfejsu</span><span class="sxs-lookup"><span data-stu-id="1dc7b-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
