---
title: "&#39; &lt;classname&gt;&#39; nie jest zgodne ze specyfikacją CLS, ponieważ interfejs &#39;&lt; InterfaceName&gt;&#39; implementuje nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7bad6aa4c8fa9979824766e83aba75697d6e98d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a><span data-ttu-id="49c40-102">&#39; &lt;classname&gt;&#39; nie jest zgodne ze specyfikacją CLS, ponieważ interfejs &#39;&lt; InterfaceName&gt;&#39; implementuje nie jest zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="49c40-102">&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant</span></span>
<span data-ttu-id="49c40-103">Klasy lub interfejsu jest oznaczony jako `<CLSCompliant(True)>` po pochodną lub implementuje typu, który jest oznaczony jako `<CLSCompliant(False)>` lub nie jest oznaczony jako.</span><span class="sxs-lookup"><span data-stu-id="49c40-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="49c40-104">Dla klasy lub interfejsu, aby było zgodne z [niezależność od języka i elementy niezależne od języka](https://msdn.microsoft.com/library/12a7a7h3) (ze specyfikacją CLS), jej hierarchii dziedziczenia całego muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="49c40-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="49c40-105">Oznacza to, że każdy typ, po którym dziedziczy, bezpośrednio lub pośrednio, muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="49c40-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="49c40-106">Podobnie jeśli klasa implementuje jeden lub więcej interfejsów, ich wszystkie muszą być zgodne w całym ich hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="49c40-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="49c40-107">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności.</span><span class="sxs-lookup"><span data-stu-id="49c40-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="49c40-108">Nie jest domyślnie dla tego parametru, a należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="49c40-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="49c40-109">Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="49c40-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="49c40-110">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="49c40-110">By default, this message is a warning.</span></span> <span data-ttu-id="49c40-111">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="49c40-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="49c40-112">**Identyfikator błędu:** BC40029</span><span class="sxs-lookup"><span data-stu-id="49c40-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="49c40-113">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="49c40-113">To correct this error</span></span>  
  
-   <span data-ttu-id="49c40-114">Jeśli potrzebujesz zgodności ze specyfikacją CLS, należy zdefiniować tego typu w ramach systemu hierarchii lub wykonania innego dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="49c40-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="49c40-115">Jeśli wymagasz, że ten typ pozostają w jego bieżącej hierarchii lub implementacji schemat dziedziczenia, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub Oznacz go jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="49c40-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c40-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49c40-116">See Also</span></span>  
 [<span data-ttu-id="49c40-117">\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="49c40-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
