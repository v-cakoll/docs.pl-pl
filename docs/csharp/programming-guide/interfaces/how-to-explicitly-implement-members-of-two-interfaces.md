---
title: Jak jawnie zaimplementować członków dwóch interfejsów — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c7adc08f62a7f8a14b8e10f8b5ecdd6e37db811d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75701241"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="f0026-102">Jak jawnie zaimplementować członków dwóch interfejsów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="f0026-102">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="f0026-103">Implementacja [interfejsu](../../language-reference/keywords/interface.md) jawnego pozwala programistom zaimplementować dwa interfejsy, które mają te same nazwy elementów członkowskich i nadać każdemu elementowi członkowskiemu interfejsu oddzielną implementację.</span><span class="sxs-lookup"><span data-stu-id="f0026-103">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="f0026-104">W tym przykładzie wyświetlane są wymiary pola zarówno w jednostkach metrycznych, jak i w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="f0026-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="f0026-105">[Klasa](../../language-reference/keywords/class.md) Box implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, które reprezentują różne systemy pomiarowe.</span><span class="sxs-lookup"><span data-stu-id="f0026-105">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="f0026-106">Oba interfejsy mają identyczne nazwy składowych, długość i szerokość.</span><span class="sxs-lookup"><span data-stu-id="f0026-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0026-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0026-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f0026-108">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="f0026-108">Robust Programming</span></span>  
 <span data-ttu-id="f0026-109">Jeśli chcesz wprowadzić wartości domyślne w jednostkach w języku angielskim, zaimplementuj normalne wartości długości i szerokości, a następnie jawnie Zaimplementuj metody długości i szerokości z interfejsu IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="f0026-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="f0026-110">W takim przypadku można uzyskać dostęp do jednostek w języku angielskim z wystąpienia klasy i uzyskać dostęp do jednostek metryk z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="f0026-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="f0026-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0026-111">See also</span></span>

- [<span data-ttu-id="f0026-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f0026-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f0026-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="f0026-113">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="f0026-114">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0026-114">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="f0026-115">Jak jawnie zaimplementować elementy członkowskie interfejsu</span><span class="sxs-lookup"><span data-stu-id="f0026-115">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
