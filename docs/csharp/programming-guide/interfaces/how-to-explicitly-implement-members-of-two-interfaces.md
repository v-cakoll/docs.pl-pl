---
title: 'Instrukcje: Jawne implementowanie elementów członkowskich dwóch interfejsów C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 1d4dd0485be1d859e3e9594ab1558a907b8f1f7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589193"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="4a684-102">Instrukcje: Jawne implementowanie elementów członkowskich dwóch interfejsówC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="4a684-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="4a684-103">Implementacja [interfejsu](../../language-reference/keywords/interface.md) jawnego pozwala programistom zaimplementować dwa interfejsy, które mają te same nazwy elementów członkowskich i nadać każdemu elementowi członkowskiemu interfejsu oddzielną implementację.</span><span class="sxs-lookup"><span data-stu-id="4a684-103">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="4a684-104">W tym przykładzie wyświetlane są wymiary pola zarówno w jednostkach metrycznych, jak i w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="4a684-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="4a684-105">[Klasa](../../language-reference/keywords/class.md) Box implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, które reprezentują różne systemy pomiarowe.</span><span class="sxs-lookup"><span data-stu-id="4a684-105">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="4a684-106">Oba interfejsy mają identyczne nazwy składowych, długość i szerokość.</span><span class="sxs-lookup"><span data-stu-id="4a684-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a684-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a684-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4a684-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="4a684-108">Robust Programming</span></span>  
 <span data-ttu-id="4a684-109">Jeśli chcesz wprowadzić wartości domyślne w jednostkach w języku angielskim, zaimplementuj normalne wartości długości i szerokości, a następnie jawnie Zaimplementuj metody długości i szerokości z interfejsu IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="4a684-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="4a684-110">W takim przypadku można uzyskać dostęp do jednostek w języku angielskim z wystąpienia klasy i uzyskać dostęp do jednostek metryk z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="4a684-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="4a684-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a684-111">See also</span></span>

- [<span data-ttu-id="4a684-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4a684-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4a684-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="4a684-113">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="4a684-114">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="4a684-114">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="4a684-115">Instrukcje: Jawnie Implementuj składowe interfejsu</span><span class="sxs-lookup"><span data-stu-id="4a684-115">How to: Explicitly Implement Interface Members</span></span>](./how-to-explicitly-implement-interface-members.md)
