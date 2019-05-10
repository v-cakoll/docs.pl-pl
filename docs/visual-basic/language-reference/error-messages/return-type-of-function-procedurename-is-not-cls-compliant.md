---
title: Zwracany typ funkcji „<procedurename>” jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 797dbf7f6203b7f85846dc6596751c4298e96481
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593302"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="06f2c-102">Zwracany typ funkcji "\<nazwaprocedury >' nie jest zgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="06f2c-102">Return type of function '\<procedurename>' is not CLS-compliant</span></span>
<span data-ttu-id="06f2c-103">A `Function` procedura jest oznaczona jako `<CLSCompliant(True)>` , ale zwraca typ, który jest oznaczony jako `<CLSCompliant(False)>`, nie jest oznaczony jako lub nie kwalifikują się, ponieważ jest to typ niezgodne.</span><span class="sxs-lookup"><span data-stu-id="06f2c-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="06f2c-104">Procedury zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), jej używać tylko typów zgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="06f2c-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="06f2c-105">Dotyczy to typy parametrów, typ zwracany i typy jego zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="06f2c-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="06f2c-106">Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="06f2c-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="06f2c-107">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="06f2c-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="06f2c-108">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="06f2c-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="06f2c-109">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="06f2c-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="06f2c-110">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="06f2c-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="06f2c-111">Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności.</span><span class="sxs-lookup"><span data-stu-id="06f2c-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="06f2c-112">Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="06f2c-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="06f2c-113">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="06f2c-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="06f2c-114">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="06f2c-114">By default, this message is a warning.</span></span> <span data-ttu-id="06f2c-115">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="06f2c-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="06f2c-116">**Identyfikator błędu:** BC40027</span><span class="sxs-lookup"><span data-stu-id="06f2c-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="06f2c-117">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="06f2c-117">To correct this error</span></span>  
  
- <span data-ttu-id="06f2c-118">Jeśli `Function` procedury musi zwracać tego konkretnego typu, Usuń <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="06f2c-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="06f2c-119">Procedura nie może być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="06f2c-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="06f2c-120">Jeśli `Function` procedury musi być zgodny ze specyfikacją CLS, Zmień typ zwracany do najbliższego typu zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="06f2c-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="06f2c-121">Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="06f2c-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="06f2c-122">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="06f2c-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="06f2c-123">Jeśli są komunikowanie się z obiektami automatyzacji lub COM, należy pamiętać o tym, że niektóre typy mają różnych szerokościach danych niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06f2c-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="06f2c-124">Na przykład `int` często jest 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="06f2c-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="06f2c-125">Jeśli są Zwraca 16-bitową liczbę całkowitą do takiego składnika, Zadeklaruj go jako `Short` zamiast `Integer` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="06f2c-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>