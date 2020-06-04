---
title: Nazwa <membername> jest niezgodna ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 45c9332237dffc7311daeedaf36035d9e9958415
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397184"
---
# <a name="name-membername-is-not-cls-compliant"></a><span data-ttu-id="e9450-102">Nazwa \<membername> jest niezgodna ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="e9450-102">Name \<membername> is not CLS-compliant</span></span>
<span data-ttu-id="e9450-103">Zestaw jest oznaczony jako, `<CLSCompliant(True)>` ale uwidacznia element członkowski o nazwie rozpoczynającej się od znaku podkreślenia ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="e9450-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="e9450-104">Element programowania może zawierać jeden lub więcej podkreśleń, ale w celu uzyskania zgodności z [niezależnymi od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS) nie może zaczynać się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="e9450-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="e9450-105">Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="e9450-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="e9450-106">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, należy ustawić `isCompliant` parametr atrybutu na wartość `True` lub `False` w celu wskazania zgodności lub niezgodności.</span><span class="sxs-lookup"><span data-stu-id="e9450-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="e9450-107">Dla tego parametru nie ma wartości domyślnej i należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="e9450-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="e9450-108">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> do elementu, jest on uznawany za niezgodny.</span><span class="sxs-lookup"><span data-stu-id="e9450-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="e9450-109">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="e9450-109">By default, this message is a warning.</span></span> <span data-ttu-id="e9450-110">Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e9450-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e9450-111">**Identyfikator błędu:** BC40031</span><span class="sxs-lookup"><span data-stu-id="e9450-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9450-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e9450-112">To correct this error</span></span>  
  
- <span data-ttu-id="e9450-113">Jeśli masz kontrolę nad kodem źródłowym, Zmień nazwę elementu członkowskiego tak, aby nie zaczynała się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="e9450-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
- <span data-ttu-id="e9450-114">Jeśli wymagasz, aby nazwa elementu członkowskiego pozostała niezmieniona, Usuń <xref:System.CLSCompliantAttribute> z jej definicji lub oznacz ją jako `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="e9450-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="e9450-115">Można nadal oznaczyć zestaw jako `<CLSCompliant(True)>` .</span><span class="sxs-lookup"><span data-stu-id="e9450-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9450-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9450-116">See also</span></span>

- [<span data-ttu-id="e9450-117">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="e9450-117">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="e9450-118">Visual Basic — Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="e9450-118">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
