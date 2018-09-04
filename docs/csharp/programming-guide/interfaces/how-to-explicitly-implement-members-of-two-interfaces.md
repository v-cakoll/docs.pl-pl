---
title: 'Porady: jawne implementowanie elementów dwóch interfejsów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 6c02585b57acef654c6613bef1a276a433763af6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514676"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="1bd76-102">Porady: jawne implementowanie elementów dwóch interfejsów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1bd76-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="1bd76-103">Jawne [interfejsu](../../../csharp/language-reference/keywords/interface.md) implementacji umożliwia także programisty należy zaimplementować dwa interfejsy, które mają te same nazwy składników i nadaj każdej składowej interfejsu oddzielne implementacji.</span><span class="sxs-lookup"><span data-stu-id="1bd76-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="1bd76-104">Ten przykład wyświetla rozmiary pola w metryki i jednostek w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="1bd76-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="1bd76-105">Pole [klasy](../../../csharp/language-reference/keywords/class.md) implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, którą reprezentują różne systemy miary.</span><span class="sxs-lookup"><span data-stu-id="1bd76-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="1bd76-106">Oba interfejsy mają identyczne nazwy elementów członkowskich, długość i szerokość.</span><span class="sxs-lookup"><span data-stu-id="1bd76-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bd76-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bd76-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1bd76-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1bd76-108">Robust Programming</span></span>  
 <span data-ttu-id="1bd76-109">Jeśli chcesz wprowadzić odpowiednie wartości domyślne w języku angielskim jednostkach, zwykle implementują metody długości i szerokości i jawnie implementować metody długości i szerokości przy użyciu interfejsu IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="1bd76-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 <span data-ttu-id="1bd76-110">W takim przypadku można uzyskiwać dostęp do jednostki angielskiego z wystąpienia klasy i uzyskać dostęp do metryk jednostki z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="1bd76-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1bd76-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bd76-111">See Also</span></span>

- [<span data-ttu-id="1bd76-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1bd76-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1bd76-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="1bd76-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="1bd76-114">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1bd76-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
- [<span data-ttu-id="1bd76-115">Instrukcje: jawne implementowanie elementów interfejsu</span><span class="sxs-lookup"><span data-stu-id="1bd76-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
