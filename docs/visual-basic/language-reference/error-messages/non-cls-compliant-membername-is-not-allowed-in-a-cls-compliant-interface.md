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
ms.openlocfilehash: 358abd338d3ce780c2f0aae7aa8efb53e57b477c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="97b02-102">Zgodne z non-CLS &lt;membername&gt; jest niedozwolony w interfejsie zgodnym ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="97b02-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="97b02-103">Właściwość, procedura lub zdarzenie w interfejsie jest oznaczony jako `<CLSCompliant(True)>` gdy sam interfejs jest oznaczony jako `<CLSCompliant(False)>` lub nie jest oznaczony jako.</span><span class="sxs-lookup"><span data-stu-id="97b02-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="97b02-104">Dla interfejsu było zgodne z [niezależność od języka i elementy niezależne od języka](https://msdn.microsoft.com/library/12a7a7h3) (ze specyfikacją CLS), wszystkie jego elementy członkowskie muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="97b02-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="97b02-105">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności.</span><span class="sxs-lookup"><span data-stu-id="97b02-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="97b02-106">Nie jest domyślnie dla tego parametru, a należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="97b02-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="97b02-107">Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="97b02-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="97b02-108">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="97b02-108">By default, this message is a warning.</span></span> <span data-ttu-id="97b02-109">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="97b02-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="97b02-110">**Identyfikator błędu:** BC40033</span><span class="sxs-lookup"><span data-stu-id="97b02-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97b02-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="97b02-111">To correct this error</span></span>  
  
-   <span data-ttu-id="97b02-112">Wymagaj zgodności ze specyfikacją CLS, kontrolę kodu źródłowego interfejsu oznaczyć interfejsu `<CLSCompliant(True)>` Jeśli wszyscy jej członkowie będą zgodne.</span><span class="sxs-lookup"><span data-stu-id="97b02-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="97b02-113">Jeśli wymagają zgodności ze specyfikacją CLS i nie mają kontrolę nad interfejsu kodu źródłowego lub nie kwalifikuje się do zapewnienia zgodności, zdefiniuj tego elementu członkowskiego w ramach innego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="97b02-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="97b02-114">Jeśli potrzebna jest pozostawienie tego elementu członkowskiego w interfejsie bieżącej, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub Oznacz go jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="97b02-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b02-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97b02-115">See Also</span></span>  
 [<span data-ttu-id="97b02-116">Interface — instrukcja</span><span class="sxs-lookup"><span data-stu-id="97b02-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="97b02-117">\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="97b02-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
