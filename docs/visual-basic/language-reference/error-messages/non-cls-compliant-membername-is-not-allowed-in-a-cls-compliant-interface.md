---
title: Non zgodne ze specyfikacją CLS &lt;membername&gt; jest niedozwolone w interfejsie zgodnym ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: c837065d2d448fc2523cfbd18efac962445f8bf0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627700"
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="73058-102">Non zgodne ze specyfikacją CLS &lt;membername&gt; jest niedozwolone w interfejsie zgodnym ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="73058-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="73058-103">Właściwość, procedura lub zdarzenie w interfejsie jest oznaczony jako `<CLSCompliant(True)>` po interfejsie, sama jest oznaczony jako `<CLSCompliant(False)>` lub nie jest oznaczona.</span><span class="sxs-lookup"><span data-stu-id="73058-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="73058-104">Dla interfejsu zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), wszystkich jej członków muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="73058-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="73058-105">Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności.</span><span class="sxs-lookup"><span data-stu-id="73058-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="73058-106">Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="73058-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="73058-107">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="73058-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="73058-108">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="73058-108">By default, this message is a warning.</span></span> <span data-ttu-id="73058-109">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="73058-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="73058-110">**Identyfikator błędu:** BC40033</span><span class="sxs-lookup"><span data-stu-id="73058-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73058-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="73058-111">To correct this error</span></span>  
  
-   <span data-ttu-id="73058-112">Wymagaj zgodności ze specyfikacją CLS i mają kontrolę nad interfejsu kodu źródłowego, oznaczyć interfejsu `<CLSCompliant(True)>` Jeśli wszystkie jej składowe są zgodne.</span><span class="sxs-lookup"><span data-stu-id="73058-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="73058-113">Jeśli wymagają zgodności ze specyfikacją CLS i nie mają kontrolę nad interfejsu kodu źródłowego lub nie kwalifikuje się jako zgodne, należy zdefiniować tego elementu członkowskiego, w ramach innego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="73058-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="73058-114">Jeśli wymagana jest pozostawienie tego elementu członkowskiego w interfejsie bieżącej, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub oznaczyć go jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="73058-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73058-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73058-115">See also</span></span>
- [<span data-ttu-id="73058-116">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="73058-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

