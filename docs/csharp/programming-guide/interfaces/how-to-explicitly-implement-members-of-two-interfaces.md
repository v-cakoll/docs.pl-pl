---
title: "Porady: jawne implementowanie elementów dwóch interfejsów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f0820328f037008c152b2e23071ae0ba8dba02bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="e3afb-102">Porady: jawne implementowanie elementów dwóch interfejsów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="e3afb-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="e3afb-103">Jawne [interfejsu](../../../csharp/language-reference/keywords/interface.md) implementacji umożliwia również programisty do zaimplementowania dwa interfejsy tej samej nazwy elementów członkowskich, które zapewniają każdy element członkowski interfejsu oddzielne implementacji.</span><span class="sxs-lookup"><span data-stu-id="e3afb-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="e3afb-104">W tym przykładzie wyświetla rozmiary pola w metryki i jednostki w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="e3afb-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="e3afb-105">Pole [klasy](../../../csharp/language-reference/keywords/class.md) implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, reprezentujące różne systemy miary.</span><span class="sxs-lookup"><span data-stu-id="e3afb-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="e3afb-106">Oba interfejsy mają nazwy identyczne elementu członkowskiego, długość i szerokość.</span><span class="sxs-lookup"><span data-stu-id="e3afb-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3afb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3afb-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e3afb-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="e3afb-108">Robust Programming</span></span>  
 <span data-ttu-id="e3afb-109">Jeśli mają być pomiarów domyślne w angielskiej wersji językowej jednostki, zwykle implementuje metody długości i szerokości i jawnie implementować metody długości i szerokości przy użyciu interfejsu IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="e3afb-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 <span data-ttu-id="e3afb-110">W takim przypadku angielskiej wersji językowej jednostki z wystąpienia klasy i dostępne uzyskiwać dostęp do jednostki metryki z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="e3afb-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e3afb-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3afb-111">See Also</span></span>  
 [<span data-ttu-id="e3afb-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e3afb-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e3afb-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="e3afb-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="e3afb-114">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e3afb-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="e3afb-115">Porady: jawne Implementowanie elementów interfejsu</span><span class="sxs-lookup"><span data-stu-id="e3afb-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
