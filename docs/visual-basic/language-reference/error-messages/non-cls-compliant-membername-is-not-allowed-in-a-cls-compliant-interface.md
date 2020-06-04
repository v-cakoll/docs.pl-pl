---
title: Element <membername> niezgodny ze specyfikacją CLS jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: e572189b958612bf9527c82ce702df3ab929a23f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409403"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="bbbc0-102">Element \<membername> niezgodny ze specyfikacją CLS jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="bbbc0-102">Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="bbbc0-103">Właściwość, procedura lub zdarzenie w interfejsie jest oznaczone jako, `<CLSCompliant(True)>` gdy sam interfejs jest oznaczony jako `<CLSCompliant(False)>` lub nie jest oznaczony.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="bbbc0-104">Aby interfejs był zgodny z [niezależnymi od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), wszystkie jego elementy członkowskie muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="bbbc0-105">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, należy ustawić `isCompliant` parametr atrybutu na wartość `True` lub `False` w celu wskazania zgodności lub niezgodności.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="bbbc0-106">Dla tego parametru nie ma wartości domyślnej i należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="bbbc0-107">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> do elementu, jest on uznawany za niezgodny.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="bbbc0-108">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-108">By default, this message is a warning.</span></span> <span data-ttu-id="bbbc0-109">Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bbbc0-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bbbc0-110">**Identyfikator błędu:** BC40033</span><span class="sxs-lookup"><span data-stu-id="bbbc0-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bbbc0-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="bbbc0-111">To correct this error</span></span>  
  
- <span data-ttu-id="bbbc0-112">Jeśli wymagasz zgodności ze specyfikacją CLS i masz kontrolę nad kodem źródłowym interfejsu, Oznacz interfejs tak, jakby `<CLSCompliant(True)>` wszystkie jego elementy członkowskie były zgodne.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
- <span data-ttu-id="bbbc0-113">Jeśli jest wymagana zgodność ze specyfikacją CLS i nie ma kontroli nad kodem źródłowym interfejsu lub jeśli nie kwalifikuje się do zgodności, zdefiniuj tego elementu członkowskiego w innym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
- <span data-ttu-id="bbbc0-114">Jeśli potrzebujesz, aby ten element członkowski pozostawał w bieżącym interfejsie, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub Oznacz go jako `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="bbbc0-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbc0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbbc0-115">See also</span></span>

- [<span data-ttu-id="bbbc0-116">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bbbc0-116">Interface Statement</span></span>](../statements/interface-statement.md)
