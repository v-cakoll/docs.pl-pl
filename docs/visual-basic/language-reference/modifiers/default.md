---
title: Domyślny
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
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351581"
---
# <a name="default-visual-basic"></a><span data-ttu-id="c265e-102">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c265e-102">Default (Visual Basic)</span></span>
<span data-ttu-id="c265e-103">Identyfikuje właściwość jako domyślną właściwość klasy, struktury lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c265e-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c265e-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c265e-104">Remarks</span></span>  
 <span data-ttu-id="c265e-105">Klasa, struktura lub interfejs może wyznaczyć najwyżej jedną z właściwości jako *Właściwość domyślną*, pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="c265e-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="c265e-106">Jeśli kod tworzy odwołanie do klasy lub struktury bez określania elementu członkowskiego, Visual Basic rozpoznaje to odwołanie do właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="c265e-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="c265e-107">Właściwości domyślne mogą spowodować niewielkie zmniejszenie kodu źródłowego, ale może to utrudnić odczytywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="c265e-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="c265e-108">Jeśli kod wywołujący nie jest zaznajomiony z klasą lub strukturą, gdy tworzy odwołanie do nazwy klasy lub struktury, nie można określić, czy odwołanie uzyskuje dostęp do samej klasy lub struktury, czy też do właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="c265e-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="c265e-109">Może to prowadzić do błędów kompilatora lub niewielkich błędów logiki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c265e-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="c265e-110">Możesz nieco skrócić ryzyko błędów właściwości domyślnych, zawsze używając [instrukcji Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) , aby ustawić sprawdzanie typu kompilatora do `On`.</span><span class="sxs-lookup"><span data-stu-id="c265e-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="c265e-111">Jeśli planujesz użycie wstępnie zdefiniowanej klasy lub struktury w kodzie, musisz określić, czy ma ona właściwość domyślną, a jeśli tak, to jaki jest jej nazwa.</span><span class="sxs-lookup"><span data-stu-id="c265e-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="c265e-112">Ze względu na te wady należy rozważyć niedefiniowanie właściwości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="c265e-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="c265e-113">Aby uzyskać czytelność kodu, należy również rozważyć zawsze odwołanie do wszystkich właściwości jawnie, nawet właściwości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="c265e-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="c265e-114">Modyfikator `Default` może być używany w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="c265e-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="c265e-115">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c265e-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c265e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c265e-116">See also</span></span>

- [<span data-ttu-id="c265e-117">Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c265e-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="c265e-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c265e-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
