---
title: Element „<elementname>" jest przestarzały (ostrzeżenie w języku Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: d7d3d86f89ef3b76e958707dd0be2dce8a3e9bf2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659820"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="ac6e9-102">"\<elementname >" jest przestarzały (ostrzeżenie Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac6e9-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="ac6e9-103">Instrukcja próbuje uzyskać dostęp elementu programistycznego, które zostały oznaczone do <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktowanie jej jako ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="ac6e9-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="ac6e9-104">Możesz oznaczyć dowolnego elementu programistycznego jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego.</span><span class="sxs-lookup"><span data-stu-id="ac6e9-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="ac6e9-105">Jeśli to zrobisz, możesz ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="ac6e9-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="ac6e9-106">Jeśli ustawisz na `True`, kompilator traktuje próba użycia elementu jako błąd.</span><span class="sxs-lookup"><span data-stu-id="ac6e9-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="ac6e9-107">Jeśli ustawisz na `False`, lub pozwól, aby go domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.</span><span class="sxs-lookup"><span data-stu-id="ac6e9-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="ac6e9-108">Domyślnie ten komunikat jest to ostrzeżenie, ponieważ <xref:System.ObsoleteAttribute.IsError%2A> właściwość <xref:System.ObsoleteAttribute> jest `False`.</span><span class="sxs-lookup"><span data-stu-id="ac6e9-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="ac6e9-109">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ac6e9-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="ac6e9-110">**Identyfikator błędu:** BC40008</span><span class="sxs-lookup"><span data-stu-id="ac6e9-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ac6e9-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ac6e9-111">To correct this error</span></span>  
  
- <span data-ttu-id="ac6e9-112">Upewnij się, że odwołanie do kodu źródłowego jest poprawnie pisownia nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="ac6e9-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac6e9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac6e9-113">See also</span></span>

- [<span data-ttu-id="ac6e9-114">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="ac6e9-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
