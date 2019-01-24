---
title: 'Pierwsza instrukcja tego &#39;Sub New&#39; musi być jawnym wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; ponieważ &#39; &lt;constructorname&gt; &#39; w klasie bazowej &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; jest oznaczony jako przestarzały: &#39; &lt;komunikat o błędzie&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 9d07a68fd8d9790178427c512375323f23f46772
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566782"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="aecee-102">Pierwsza instrukcja tego &#39;Sub New&#39; musi być jawnym wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; ponieważ &#39; &lt;constructorname&gt; &#39; w klasie bazowej &#39; &lt;baseclassname&gt; &#39; z &#39; &lt;derivedclassname&gt; &#39; jest oznaczony jako przestarzały: &#39; &lt;komunikat o błędzie&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="aecee-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="aecee-103">Konstruktor klasy nie jawnie wywołać konstruktora klasy bazowej i Konstruktor niejawne klasy bazowej jest oznaczona za pomocą <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktowanie jej jako błąd.</span><span class="sxs-lookup"><span data-stu-id="aecee-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="aecee-104">Jeśli konstruktor klasy pochodnej nie wywołać konstruktora klasy bazowej, Visual Basic spróbuje go wygenerować wywołanie niejawne konstruktor bez parametrów klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="aecee-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="aecee-105">Jeśli jest dostępny żaden konstruktor nie w klasie bazowej, który można wywołać bez argumentów, Visual Basic nie można wygenerować wywołanie niejawne.</span><span class="sxs-lookup"><span data-stu-id="aecee-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="aecee-106">W tym przypadku wymaganego konstruktora jest oznaczona za pomocą <xref:System.ObsoleteAttribute> atrybutu, więc języka Visual Basic nie można wywołać go.</span><span class="sxs-lookup"><span data-stu-id="aecee-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="aecee-107">Możesz oznaczyć dowolnego elementu programistycznego jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego.</span><span class="sxs-lookup"><span data-stu-id="aecee-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="aecee-108">Jeśli to zrobisz, możesz ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="aecee-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="aecee-109">Jeśli ustawisz na `True`, kompilator traktuje próba użycia elementu jako błąd.</span><span class="sxs-lookup"><span data-stu-id="aecee-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="aecee-110">Jeśli ustawisz na `False`, lub pozwól, aby go domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.</span><span class="sxs-lookup"><span data-stu-id="aecee-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="aecee-111">**Identyfikator błędu:** BC30920</span><span class="sxs-lookup"><span data-stu-id="aecee-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aecee-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="aecee-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="aecee-113">Sprawdź komunikat o błędzie w cudzysłowach i podjąć odpowiednie działania.</span><span class="sxs-lookup"><span data-stu-id="aecee-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="aecee-114">Obejmują wywołania `MyBase.New()` lub `MyClass.New()` jako pierwsza instrukcja `Sub New` w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="aecee-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aecee-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aecee-115">See also</span></span>
- [<span data-ttu-id="aecee-116">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="aecee-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

