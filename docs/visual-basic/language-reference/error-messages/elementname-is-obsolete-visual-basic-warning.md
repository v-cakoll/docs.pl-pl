---
title: Element „<elementname>" jest przestarzały (ostrzeżenie w języku Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 545f0f4a56e72e32d2225217225d441a10f0e52e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836366"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="b9bf4-102">"\<elementname >" jest przestarzały (ostrzeżenie Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9bf4-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="b9bf4-103">Instrukcja próbuje uzyskać dostęp elementu programistycznego, które zostały oznaczone do <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktowanie jej jako ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="b9bf4-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="b9bf4-104">Możesz oznaczyć dowolnego elementu programistycznego jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego.</span><span class="sxs-lookup"><span data-stu-id="b9bf4-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="b9bf4-105">Jeśli to zrobisz, możesz ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="b9bf4-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="b9bf4-106">Jeśli ustawisz na `True`, kompilator traktuje próba użycia elementu jako błąd.</span><span class="sxs-lookup"><span data-stu-id="b9bf4-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="b9bf4-107">Jeśli ustawisz na `False`, lub pozwól, aby go domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.</span><span class="sxs-lookup"><span data-stu-id="b9bf4-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="b9bf4-108">Domyślnie ten komunikat jest to ostrzeżenie, ponieważ <xref:System.ObsoleteAttribute.IsError%2A> właściwość <xref:System.ObsoleteAttribute> jest `False`.</span><span class="sxs-lookup"><span data-stu-id="b9bf4-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="b9bf4-109">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b9bf4-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b9bf4-110">**Identyfikator błędu:** BC40008</span><span class="sxs-lookup"><span data-stu-id="b9bf4-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b9bf4-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b9bf4-111">To correct this error</span></span>  
  
-   <span data-ttu-id="b9bf4-112">Upewnij się, że odwołanie do kodu źródłowego jest poprawnie pisownia nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="b9bf4-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9bf4-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9bf4-113">See also</span></span>

- [<span data-ttu-id="b9bf4-114">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="b9bf4-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
