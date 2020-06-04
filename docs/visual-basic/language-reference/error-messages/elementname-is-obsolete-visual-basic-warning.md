---
title: Element „<elementname>" jest przestarzały (ostrzeżenie w języku Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 7914bc859966e17f3da41c9a13a01573b31baf91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409676"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="219d9-102">Element „\<elementname>" jest przestarzały (ostrzeżenie w języku Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="219d9-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="219d9-103">Instrukcja próbuje uzyskać dostęp do elementu programistycznego, który został oznaczony <xref:System.ObsoleteAttribute> atrybutem i dyrektywą, aby traktować go jako ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="219d9-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="219d9-104">Można oznaczyć dowolny element programistyczny jako nieużywany przez zastosowanie <xref:System.ObsoleteAttribute> do niego.</span><span class="sxs-lookup"><span data-stu-id="219d9-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="219d9-105">W takim przypadku można ustawić <xref:System.ObsoleteAttribute.IsError%2A> właściwość atrybutu na `True` lub `False` .</span><span class="sxs-lookup"><span data-stu-id="219d9-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="219d9-106">Jeśli ustawisz ją na `True` , kompilator traktuje próbę użycia elementu jako błąd.</span><span class="sxs-lookup"><span data-stu-id="219d9-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="219d9-107">Jeśli ustawisz ją na `False` lub Zezwól na ustawienie domyślne `False` , kompilator generuje ostrzeżenie w przypadku próby użycia elementu.</span><span class="sxs-lookup"><span data-stu-id="219d9-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="219d9-108">Domyślnie ten komunikat jest ostrzeżeniem, ponieważ <xref:System.ObsoleteAttribute.IsError%2A> Właściwość <xref:System.ObsoleteAttribute> jest `False` .</span><span class="sxs-lookup"><span data-stu-id="219d9-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="219d9-109">Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="219d9-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="219d9-110">**Identyfikator błędu:** BC40008</span><span class="sxs-lookup"><span data-stu-id="219d9-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="219d9-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="219d9-111">To correct this error</span></span>  
  
- <span data-ttu-id="219d9-112">Upewnij się, że odwołanie do kodu źródłowego jest poprawnie sprawdzane jako nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="219d9-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219d9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="219d9-113">See also</span></span>

- [<span data-ttu-id="219d9-114">Przegląd atrybutów</span><span class="sxs-lookup"><span data-stu-id="219d9-114">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
