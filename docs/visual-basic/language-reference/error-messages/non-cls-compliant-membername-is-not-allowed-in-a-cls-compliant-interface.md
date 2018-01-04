---
title: "Zgodne z non-CLS &lt;membername&gt; jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords: BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74744b89ad72b6fd051f83ba38354d0a277555c8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="9dfaf-102">Zgodne z non-CLS &lt;membername&gt; jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="9dfaf-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="9dfaf-103">Właściwość, procedura lub zdarzenie w interfejsie jest oznaczony jako `<CLSCompliant(True)>` gdy sam interfejs jest oznaczony jako `<CLSCompliant(False)>` lub nie jest oznaczony jako.</span><span class="sxs-lookup"><span data-stu-id="9dfaf-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="9dfaf-104">Dla interfejsu było zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), wszystkie jego elementy członkowskie muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="9dfaf-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="9dfaf-105">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności.</span><span class="sxs-lookup"><span data-stu-id="9dfaf-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="9dfaf-106">Nie jest domyślnie dla tego parametru, a należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="9dfaf-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="9dfaf-107">Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="9dfaf-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="9dfaf-108">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="9dfaf-108">By default, this message is a warning.</span></span> <span data-ttu-id="9dfaf-109">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9dfaf-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="9dfaf-110">**Identyfikator błędu:** BC40033</span><span class="sxs-lookup"><span data-stu-id="9dfaf-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9dfaf-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9dfaf-111">To correct this error</span></span>  
  
-   <span data-ttu-id="9dfaf-112">Wymagaj zgodności ze specyfikacją CLS, kontrolę kodu źródłowego interfejsu oznaczyć interfejsu `<CLSCompliant(True)>` Jeśli wszyscy jej członkowie będą zgodne.</span><span class="sxs-lookup"><span data-stu-id="9dfaf-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="9dfaf-113">Jeśli wymagają zgodności ze specyfikacją CLS i nie mają kontrolę nad interfejsu kodu źródłowego lub nie kwalifikuje się do zapewnienia zgodności, zdefiniuj tego elementu członkowskiego w ramach innego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9dfaf-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="9dfaf-114">Jeśli potrzebna jest pozostawienie tego elementu członkowskiego w interfejsie bieżącej, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub Oznacz go jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="9dfaf-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dfaf-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9dfaf-115">See Also</span></span>  
 [<span data-ttu-id="9dfaf-116">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9dfaf-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
