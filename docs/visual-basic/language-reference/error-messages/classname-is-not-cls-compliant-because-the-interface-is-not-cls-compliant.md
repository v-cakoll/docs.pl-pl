---
title: Element „<classname>” jest niezgodny ze specyfikacją CLS, ponieważ interfejs „<interfacename>”, który implementuje, jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 063c42249abbfb506fd15311659599b4777d397f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649884"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a><span data-ttu-id="4cbb0-102">"\<nazwa_klasy >' nie jest zgodny ze specyfikacją CLS, ponieważ interfejs"\<interfacename > "go implementuje, jest niezgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="4cbb0-102">'\<classname>' is not CLS-compliant because the interface '\<interfacename>' it implements is not CLS-compliant</span></span>
<span data-ttu-id="4cbb0-103">Klasy lub interfejsu, jest oznaczana `<CLSCompliant(True)>` po pochodzi od klasy lub typu, który jest oznaczony jako implementuje `<CLSCompliant(False)>` lub nie jest oznaczona.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="4cbb0-104">Dla klasy lub interfejsu, aby zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), jej hierarchii dziedziczenia całego muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="4cbb0-105">Oznacza to, że każdy typ, po którym dziedziczy, bezpośrednio lub pośrednio, muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="4cbb0-106">Podobnie jeśli klasa implementuje jeden lub więcej interfejsów, ich wszystkie muszą być zgodne w całej swojej hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="4cbb0-107">Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="4cbb0-108">Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="4cbb0-109">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="4cbb0-110">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-110">By default, this message is a warning.</span></span> <span data-ttu-id="4cbb0-111">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4cbb0-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4cbb0-112">**Identyfikator błędu:** BC40029</span><span class="sxs-lookup"><span data-stu-id="4cbb0-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4cbb0-113">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4cbb0-113">To correct this error</span></span>  
  
- <span data-ttu-id="4cbb0-114">Jeśli wymagana jest zgodność ze specyfikacją CLS, należy zdefiniować tego typu w ramach różnych dziedziczenia hierarchii lub implementacji systemu.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
- <span data-ttu-id="4cbb0-115">Jeśli potrzebujesz, że tego typu pozostaną w jego bieżącej hierarchii lub implementacji schemat dziedziczenia, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub oznaczyć go jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="4cbb0-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
