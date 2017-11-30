---
title: Default (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18126a0a5b6254da0b43e806b3de1f5b2127e6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="default-visual-basic"></a><span data-ttu-id="d3b1d-102">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3b1d-102">Default (Visual Basic)</span></span>
<span data-ttu-id="d3b1d-103">Identyfikuje właściwość jako domyślną właściwość klasy, struktury lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3b1d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3b1d-104">Remarks</span></span>  
 <span data-ttu-id="d3b1d-105">Klasy, struktury lub interfejsu można wyznaczyć co najwyżej jednej z jego właściwości jako *domyślna właściwość*, pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="d3b1d-106">Jeśli kod sprawia, że odwołanie do klasy lub struktury bez określenia członka, Visual Basic rozpoznaje odwołujące się do właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="d3b1d-107">Właściwości domyślnych może spowodować zmniejszenie małych znaków kodu źródłowego, ale może wprowadzić czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="d3b1d-108">Jeśli kod wywołujący nie są zaznajomieni z klasy lub struktury, podczas wykonywania odwołanie do nazwy klasy lub struktury nie może być niektórych czy uzyskuje dostęp tego odwołania do klasy lub struktury, sam lub domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="d3b1d-109">Może to prowadzić do błędów kompilatora lub błędy niewielkie logiki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="d3b1d-110">Nieco zmniejsza ryzyko błędów właściwości domyślne przy użyciu zawsze [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md) można ustawić typ kompilatora sprawdzania `On`.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="d3b1d-111">Jeśli planujesz użyć wstępnie zdefiniowanych klasy lub struktury w kodzie, należy określić, czy ma ona domyślnej właściwości, a jeśli tak, jakie jego nazwa jest.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="d3b1d-112">Z powodu niedogodności należy rozważyć nie definiuje właściwości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="d3b1d-113">Aby zwiększyć czytelność kodu należy również wziąć pod uwagę zawsze odwołujących się do wszystkich właściwości jawnie, nawet domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d3b1d-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="d3b1d-114">`Default` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="d3b1d-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="d3b1d-115">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="d3b1d-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d3b1d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3b1d-116">See Also</span></span>  
 [<span data-ttu-id="d3b1d-117">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3b1d-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="d3b1d-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d3b1d-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
