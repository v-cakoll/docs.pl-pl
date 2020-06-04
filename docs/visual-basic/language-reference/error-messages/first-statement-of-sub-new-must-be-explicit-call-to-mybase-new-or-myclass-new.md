---
title: 'Pierwsza instrukcja tego elementu „Sub New” musi być jawnym wywołaniem elementu „MyBase.New” lub „MyClass.New”, ponieważ element „<constructorname>” w klasie bazowej „<baseclassname>” elementu „<derivedclassname>” jest oznaczony jako przestarzały: „<errormessage>"'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 33dd15e3f5f5538963597f2b00f4214895e1f47a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403008"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a><span data-ttu-id="43c42-102">Pierwsza instrukcja tego elementu „Sub New” musi być jawnym wywołaniem elementu „MyBase.New” lub „MyClass.New”, ponieważ element „\<constructorname>” w klasie bazowej „\<baseclassname>” elementu „\<derivedclassname>” jest oznaczony jako przestarzały: „\<errormessage>"</span><span class="sxs-lookup"><span data-stu-id="43c42-102">First statement of this 'Sub New' must be an explicit call to 'MyBase.New' or 'MyClass.New' because the '\<constructorname>' in the base class '\<baseclassname>' of '\<derivedclassname>' is marked obsolete: '\<errormessage>'</span></span>
<span data-ttu-id="43c42-103">Konstruktor klasy nie wywołuje jawnie konstruktora klasy bazowej, a niejawny Konstruktor klasy bazowej jest oznaczony <xref:System.ObsoleteAttribute> atrybutem i dyrektywą, aby traktować go jako błąd.</span><span class="sxs-lookup"><span data-stu-id="43c42-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="43c42-104">Gdy Konstruktor klasy pochodnej nie wywołuje konstruktora klasy bazowej, Visual Basic próbuje wygenerować niejawnego wywołania konstruktora klasy bazowej bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="43c42-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="43c42-105">Jeśli w klasie bazowej nie ma dostępnego konstruktora, który można wywołać bez argumentów, Visual Basic nie może wygenerować wywołania niejawnego.</span><span class="sxs-lookup"><span data-stu-id="43c42-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="43c42-106">W takim przypadku wymagany Konstruktor jest oznaczony <xref:System.ObsoleteAttribute> atrybutem, więc Visual Basic nie może go wywołać.</span><span class="sxs-lookup"><span data-stu-id="43c42-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="43c42-107">Można oznaczyć dowolny element programistyczny jako nieużywany przez zastosowanie <xref:System.ObsoleteAttribute> do niego.</span><span class="sxs-lookup"><span data-stu-id="43c42-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="43c42-108">W takim przypadku można ustawić <xref:System.ObsoleteAttribute.IsError%2A> właściwość atrybutu na `True` lub `False` .</span><span class="sxs-lookup"><span data-stu-id="43c42-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="43c42-109">Jeśli ustawisz ją na `True` , kompilator traktuje próbę użycia elementu jako błąd.</span><span class="sxs-lookup"><span data-stu-id="43c42-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="43c42-110">Jeśli ustawisz ją na `False` lub Zezwól na ustawienie domyślne `False` , kompilator generuje ostrzeżenie w przypadku próby użycia elementu.</span><span class="sxs-lookup"><span data-stu-id="43c42-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="43c42-111">**Identyfikator błędu:** BC30920</span><span class="sxs-lookup"><span data-stu-id="43c42-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="43c42-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="43c42-112">To correct this error</span></span>  
  
1. <span data-ttu-id="43c42-113">Przejrzyj cytowany komunikat o błędzie i podejmij odpowiednie działanie.</span><span class="sxs-lookup"><span data-stu-id="43c42-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2. <span data-ttu-id="43c42-114">Dołącz wywołanie do `MyBase.New()` lub `MyClass.New()` jako pierwszą instrukcję `Sub New` w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="43c42-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c42-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43c42-115">See also</span></span>

- [<span data-ttu-id="43c42-116">Przegląd atrybutów</span><span class="sxs-lookup"><span data-stu-id="43c42-116">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
