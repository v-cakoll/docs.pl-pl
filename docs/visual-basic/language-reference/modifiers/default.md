---
title: Default (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: f78ffe42a9d618d44da2a50c0de831396576430c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836730"
---
# <a name="default-visual-basic"></a><span data-ttu-id="17161-102">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17161-102">Default (Visual Basic)</span></span>
<span data-ttu-id="17161-103">Identyfikuje właściwość jako domyślną właściwość klasy, struktury lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="17161-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17161-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17161-104">Remarks</span></span>  
 <span data-ttu-id="17161-105">Klasy, struktury lub interfejsu można wyznaczyć co najwyżej jeden z jego właściwości jako *właściwość domyślna*pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="17161-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="17161-106">Jeśli kod sprawia, że odwołanie do klasy lub struktury bez podania członek, Visual Basic rozpoznaje tego odwołania do właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="17161-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="17161-107">Właściwości domyślnych może spowodować zmniejszenie małe znaki kodu źródłowego, ale mogą robić więjsze kodu czytelność.</span><span class="sxs-lookup"><span data-stu-id="17161-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="17161-108">Jeśli kod wywołujący nie są zaznajomieni z klasy lub struktury, jeśli go nawiązuje odwołanie do nazwy klasy lub struktury nie może być określone czy tego odwołania uzyskuje dostęp do, klasa lub struktura lub domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="17161-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="17161-109">Może to prowadzić do błędów kompilatora lub błędy subtelne logiki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="17161-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="17161-110">Trochę zmniejsza ryzyko wystąpienia błędów właściwości domyślne przy użyciu zawsze [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawienie typu kompilatora sprawdzanie `On`.</span><span class="sxs-lookup"><span data-stu-id="17161-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="17161-111">Jeśli planujesz użyć wstępnie zdefiniowanych klasy lub struktury w kodzie, należy określić, czy ma ona właściwości domyślnej, a jeśli tak, jakie jego nazwa jest.</span><span class="sxs-lookup"><span data-stu-id="17161-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="17161-112">Z powodu niedogodności należy rozważyć nie definiuje właściwości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="17161-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="17161-113">Aby zwiększyć czytelność kodu należy również wziąć pod uwagę zawsze odwołujące się do wszystkich właściwości jawnie, nawet domyślne właściwości.</span><span class="sxs-lookup"><span data-stu-id="17161-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="17161-114">`Default` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="17161-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="17161-115">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="17161-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="17161-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17161-116">See also</span></span>

- [<span data-ttu-id="17161-117">Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17161-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="17161-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="17161-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
