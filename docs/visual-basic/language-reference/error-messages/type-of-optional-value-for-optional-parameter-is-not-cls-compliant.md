---
title: Typ wartości opcjonalnej dla parametru opcjonalnego &lt;parametername&gt; nie jest zgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: dd77cd8cbd36f7681e2597d908dd8e55bf249392
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960352"
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a><span data-ttu-id="b5dc2-102">Typ wartości opcjonalnej dla parametru opcjonalnego &lt;parametername&gt; nie jest zgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="b5dc2-102">Type of optional value for optional parameter &lt;parametername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="b5dc2-103">Procedura jest oznaczona jako `<CLSCompliant(True)>` , ale deklaruje [opcjonalnie](../../../visual-basic/language-reference/modifiers/optional.md) parametru z wartością domyślną niezgodnego typu.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="b5dc2-104">Procedury zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), jej używać tylko typów zgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="b5dc2-105">Dotyczy to typy parametrów, typ zwracany i typy jego zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="b5dc2-106">Ma również zastosowanie do wartościami domyślnymi parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="b5dc2-107">Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="b5dc2-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="b5dc2-108">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="b5dc2-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="b5dc2-109">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="b5dc2-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="b5dc2-110">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="b5dc2-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="b5dc2-111">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="b5dc2-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="b5dc2-112">Po zastosowaniu <xref:System.CLSCompliantAttribute> atrybut elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="b5dc2-113">Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="b5dc2-114">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="b5dc2-115">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-115">By default, this message is a warning.</span></span> <span data-ttu-id="b5dc2-116">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b5dc2-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b5dc2-117">**Identyfikator błędu:** BC40042</span><span class="sxs-lookup"><span data-stu-id="b5dc2-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5dc2-118">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b5dc2-118">To correct this error</span></span>  
  
-   <span data-ttu-id="b5dc2-119">Jeśli parametr opcjonalny musi mieć wartość domyślną dla tego konkretnego typu, Usuń <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="b5dc2-120">Procedura nie może być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-120">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="b5dc2-121">Jeśli procedura musi być zgodny ze specyfikacją CLS, należy zmienić typ tę wartość domyślną, do najbliższej typu zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="b5dc2-122">Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="b5dc2-123">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="b5dc2-124">Jeśli są komunikowanie się z obiektami automatyzacji lub COM, należy pamiętać o tym, że niektóre typy mają różnych szerokościach danych niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5dc2-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="b5dc2-125">Na przykład `int` często jest 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="b5dc2-126">Jeśli akceptujesz 16-bitową liczbę całkowitą z takiego składnika, Zadeklaruj go jako `Short` zamiast `Integer` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b5dc2-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>