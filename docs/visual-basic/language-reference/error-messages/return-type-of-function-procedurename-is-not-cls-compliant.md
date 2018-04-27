---
title: Zwracany typ funkcji &#39; &lt;nazwaprocedury&gt; &#39; nie jest zgodne ze specyfikacją CLS
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b3aa178ec3a33d7edb64190d7c83d3b51483feb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="e12fd-102">Zwracany typ funkcji &#39; &lt;nazwaprocedury&gt; &#39; nie jest zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="e12fd-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="e12fd-103">A `Function` procedura jest oznaczony jako `<CLSCompliant(True)>` , ale zwraca typ, który jest oznaczony jako `<CLSCompliant(False)>`, nie jest oznaczony jako lub nie kwalifikuje się, ponieważ jest to typ niezgodne.</span><span class="sxs-lookup"><span data-stu-id="e12fd-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="e12fd-104">Procedury było zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), należy użyć tylko typów zgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="e12fd-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="e12fd-105">Dotyczy to typy parametrów, typ zwracany i typy jego zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e12fd-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="e12fd-106">Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="e12fd-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="e12fd-107">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="e12fd-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="e12fd-108">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="e12fd-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="e12fd-109">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="e12fd-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="e12fd-110">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="e12fd-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="e12fd-111">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności.</span><span class="sxs-lookup"><span data-stu-id="e12fd-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="e12fd-112">Nie jest domyślnie dla tego parametru, a należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="e12fd-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="e12fd-113">Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="e12fd-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="e12fd-114">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="e12fd-114">By default, this message is a warning.</span></span> <span data-ttu-id="e12fd-115">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e12fd-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e12fd-116">**Identyfikator błędu:** BC40027</span><span class="sxs-lookup"><span data-stu-id="e12fd-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e12fd-117">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e12fd-117">To correct this error</span></span>  
  
-   <span data-ttu-id="e12fd-118">Jeśli `Function` procedury musi zwracać tego typu, Usuń <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e12fd-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="e12fd-119">Procedura nie może być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="e12fd-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="e12fd-120">Jeśli `Function` procedury musi być zgodne ze specyfikacją CLS, Zmień typ zwracany do najbliższego typu zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="e12fd-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="e12fd-121">Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="e12fd-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="e12fd-122">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="e12fd-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="e12fd-123">Jeśli użytkownik są relacje z obiektami automatyzacji lub COM, należy pamiętać, że niektóre typy szerokości danych innego niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e12fd-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="e12fd-124">Na przykład `int` jest często 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="e12fd-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="e12fd-125">Jeśli 16-bitową liczbę całkowitą są wracając do tych składników, Zadeklaruj ją jako `Short` zamiast `Integer` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e12fd-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>