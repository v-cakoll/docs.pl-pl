---
title: "&#39; &lt;elementname&gt;&#39; jest przestarzałe (ostrzeżenie Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd6580da794255a3324021a284816ef9700beee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="93f05-102">&#39; &lt;elementname&gt;&#39; jest przestarzałe (ostrzeżenie Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93f05-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="93f05-103">Instrukcja próbuje uzyskać dostęp elementu programistycznego, które zostały oznaczone <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktować go jako ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="93f05-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="93f05-104">Można zaznaczyć dowolny element programowania jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego.</span><span class="sxs-lookup"><span data-stu-id="93f05-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="93f05-105">Jeśli to zrobisz, można ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="93f05-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="93f05-106">Jeśli zostanie ustawiona `True`, kompilator traktuje próba użycia elementu jako błąd.</span><span class="sxs-lookup"><span data-stu-id="93f05-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="93f05-107">Jeśli zostanie ustawiona `False`, lub pozwól mu domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.</span><span class="sxs-lookup"><span data-stu-id="93f05-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="93f05-108">Domyślnie ten komunikat jest ostrzeżenie, ponieważ <xref:System.ObsoleteAttribute.IsError%2A> właściwość <xref:System.ObsoleteAttribute> jest `False`.</span><span class="sxs-lookup"><span data-stu-id="93f05-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="93f05-109">Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="93f05-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="93f05-110">**Identyfikator błędu:** BC40008</span><span class="sxs-lookup"><span data-stu-id="93f05-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="93f05-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="93f05-111">To correct this error</span></span>  
  
-   <span data-ttu-id="93f05-112">Upewnij się, że odwołanie do kodu źródłowego jest poprawnie pisownię nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="93f05-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f05-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93f05-113">See Also</span></span>  
 [<span data-ttu-id="93f05-114">Atrybuty — omówienie</span><span class="sxs-lookup"><span data-stu-id="93f05-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
