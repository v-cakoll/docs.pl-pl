---
title: 'Pierwsza instrukcja tego elementu „Sub New” musi być jawnym wywołaniem elementu „MyBase.New” lub „MyClass.New”, ponieważ element „<constructorname>” w klasie bazowej „<baseclassname>” elementu „<derivedclassname>” jest oznaczony jako przestarzały: „<errormessage>"'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 89b6c241bb637f2efc6014c4640b3b463c4facfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801884"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a><span data-ttu-id="9ed8a-102">Pierwsza instrukcja tego elementu "Sub New" musi być jawnym wywołaniem elementu "MyBase.New" lub "MyClass.New", ponieważ "\<constructorname >" w klasie bazowej\<baseclassname > "z"\<derivedclassname > "jest oznaczony jako przestarzały:"\< komunikat o błędzie > "</span><span class="sxs-lookup"><span data-stu-id="9ed8a-102">First statement of this 'Sub New' must be an explicit call to 'MyBase.New' or 'MyClass.New' because the '\<constructorname>' in the base class '\<baseclassname>' of '\<derivedclassname>' is marked obsolete: '\<errormessage>'</span></span>
<span data-ttu-id="9ed8a-103">Konstruktor klasy nie jawnie wywołać konstruktora klasy bazowej i Konstruktor niejawne klasy bazowej jest oznaczona za pomocą <xref:System.ObsoleteAttribute> atrybut i dyrektywy traktowanie jej jako błąd.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="9ed8a-104">Jeśli konstruktor klasy pochodnej nie wywołać konstruktora klasy bazowej, Visual Basic spróbuje go wygenerować wywołanie niejawne konstruktor bez parametrów klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="9ed8a-105">Jeśli jest dostępny żaden konstruktor nie w klasie bazowej, który można wywołać bez argumentów, Visual Basic nie można wygenerować wywołanie niejawne.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="9ed8a-106">W tym przypadku wymaganego konstruktora jest oznaczona za pomocą <xref:System.ObsoleteAttribute> atrybutu, więc języka Visual Basic nie można wywołać go.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="9ed8a-107">Możesz oznaczyć dowolnego elementu programistycznego jako nie jest już używana przez zastosowanie <xref:System.ObsoleteAttribute> do niego.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="9ed8a-108">Jeśli to zrobisz, możesz ustawić atrybutu <xref:System.ObsoleteAttribute.IsError%2A> właściwości albo `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="9ed8a-109">Jeśli ustawisz na `True`, kompilator traktuje próba użycia elementu jako błąd.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="9ed8a-110">Jeśli ustawisz na `False`, lub pozwól, aby go domyślnie `False`, kompilator generuje ostrzeżenie, jeśli próba użycia elementu.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="9ed8a-111">**Identyfikator błędu:** BC30920</span><span class="sxs-lookup"><span data-stu-id="9ed8a-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9ed8a-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9ed8a-112">To correct this error</span></span>  
  
1. <span data-ttu-id="9ed8a-113">Sprawdź komunikat o błędzie w cudzysłowach i podjąć odpowiednie działania.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2. <span data-ttu-id="9ed8a-114">Obejmują wywołania `MyBase.New()` lub `MyClass.New()` jako pierwsza instrukcja `Sub New` w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="9ed8a-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed8a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ed8a-115">See also</span></span>

- [<span data-ttu-id="9ed8a-116">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="9ed8a-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
