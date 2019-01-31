---
title: Typ parametru „<parametername>” jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: e0852536a86dd415334f95a47ceb800ed2c591ad
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265925"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="cce59-102">Typ parametru "\<parametername >' nie jest zgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="cce59-102">Type of parameter '\<parametername>' is not CLS-compliant</span></span>
<span data-ttu-id="cce59-103">Procedura jest oznaczona jako `<CLSCompliant(True)>` , ale deklaruje parametr o typie, który jest oznaczony jako `<CLSCompliant(False)>`, nie jest oznaczony jako lub nie kwalifikują się, ponieważ jest to typ niezgodne.</span><span class="sxs-lookup"><span data-stu-id="cce59-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="cce59-104">Procedury zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), jej używać tylko typów zgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="cce59-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="cce59-105">Dotyczy to typy parametrów, typ zwracany i typy jego zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="cce59-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="cce59-106">Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="cce59-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="cce59-107">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="cce59-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="cce59-108">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="cce59-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="cce59-109">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="cce59-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="cce59-110">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="cce59-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="cce59-111">Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności.</span><span class="sxs-lookup"><span data-stu-id="cce59-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="cce59-112">Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="cce59-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="cce59-113">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="cce59-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="cce59-114">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="cce59-114">By default, this message is a warning.</span></span> <span data-ttu-id="cce59-115">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cce59-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="cce59-116">**Identyfikator błędu:** BC40028</span><span class="sxs-lookup"><span data-stu-id="cce59-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cce59-117">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cce59-117">To correct this error</span></span>  
  
-   <span data-ttu-id="cce59-118">Jeśli procedura musi przyjmować parametr tego określonego typu, Usuń <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cce59-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="cce59-119">Procedura nie może być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="cce59-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="cce59-120">Jeśli procedury muszą być zgodne ze specyfikacją CLS, należy zmienić typ tohoto parametru do najbliższego typu zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="cce59-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="cce59-121">Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="cce59-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="cce59-122">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="cce59-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="cce59-123">Jeśli są komunikowanie się z obiektami automatyzacji lub COM, należy pamiętać o tym, że niektóre typy mają różnych szerokościach danych niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cce59-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="cce59-124">Na przykład `int` często jest 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="cce59-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="cce59-125">Jeśli akceptujesz 16-bitową liczbę całkowitą z takiego składnika, Zadeklaruj go jako `Short` zamiast `Integer` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cce59-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>