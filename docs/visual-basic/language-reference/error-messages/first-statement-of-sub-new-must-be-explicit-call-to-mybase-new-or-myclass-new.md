---
title: 'Pierwsza instrukcja tego &#39;Sub New&#39; musi być jawnym wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; ponieważ &#39; &lt;constructorname&gt; &#39; w klasie podstawowej &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; jest oznaczony jako przestarzały: &#39; &lt;komunikat o błędzie&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: dbce2a9edcc38ff137cb7ec0c97e5c259c0a0979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="0d0b4-102">Pierwsza instrukcja tego &#39;Sub New&#39; musi być jawnym wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; ponieważ &#39; &lt;constructorname&gt; &#39; w klasie podstawowej &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; jest oznaczony jako przestarzały: &#39; &lt;komunikat o błędzie&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="0d0b4-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="0d0b4-103">Konstruktor klasy nie wywołuje jawnie konstruktora klasy podstawowej i konstruktora klasy podstawowej niejawne jest oznaczony atrybutem <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktować go jako błąd.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="0d0b4-104">Gdy konstruktora klasy pochodnej nie wywołuje konstruktor klasy podstawowej, Visual Basic próbuje wygenerować niejawne wywołanie konstruktora bez parametrów klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="0d0b4-105">Jeśli nie będzie dostępny żaden konstruktor nie w klasie podstawowej, który można wywołać bez argumentów, Visual Basic nie można wygenerować niejawne wywołania.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="0d0b4-106">W takim przypadku wymagany Konstruktor jest oznaczony atrybutem <xref:System.ObsoleteAttribute> atrybutu, Visual Basic nie można jej wywołać.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="0d0b4-107">Można zaznaczyć dowolny element programowania jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="0d0b4-108">Jeśli to zrobisz, można ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="0d0b4-109">Jeśli zostanie ustawiona `True`, kompilator traktuje próba użycia elementu jako błąd.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="0d0b4-110">Jeśli zostanie ustawiona `False`, lub pozwól mu domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="0d0b4-111">**Identyfikator błędu:** BC30920</span><span class="sxs-lookup"><span data-stu-id="0d0b4-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0d0b4-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0d0b4-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="0d0b4-113">Sprawdź komunikat błędu w cudzysłowie i podejmij odpowiednią akcję.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="0d0b4-114">Obejmują wywołania `MyBase.New()` lub `MyClass.New()` jako pierwsza instrukcja `Sub New` w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d0b4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d0b4-115">See Also</span></span>  
 [<span data-ttu-id="0d0b4-116">Atrybuty — omówienie</span><span class="sxs-lookup"><span data-stu-id="0d0b4-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
