---
title: "Typ parametru &#39; &lt;parametername&gt;&#39; nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c017e5e6791f6a41ab8137c549a30b76713cb7c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a><span data-ttu-id="fa544-102">Typ parametru &#39; &lt;parametername&gt;&#39; nie jest zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="fa544-102">Type of parameter &#39;&lt;parametername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="fa544-103">Procedura jest oznaczony jako `<CLSCompliant(True)>` , ale deklaruje parametr typu, który jest oznaczony jako `<CLSCompliant(False)>`, nie jest oznaczony jako lub nie kwalifikuje się, ponieważ jest to typ niezgodne.</span><span class="sxs-lookup"><span data-stu-id="fa544-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="fa544-104">Procedury było zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), należy użyć tylko typów zgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="fa544-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="fa544-105">Dotyczy to typy parametrów, typ zwracany i typy jego zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="fa544-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="fa544-106">Następujące [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typy danych nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="fa544-106">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="fa544-107">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="fa544-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="fa544-108">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="fa544-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="fa544-109">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="fa544-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="fa544-110">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="fa544-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="fa544-111">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności.</span><span class="sxs-lookup"><span data-stu-id="fa544-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="fa544-112">Nie jest domyślnie dla tego parametru, a należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="fa544-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="fa544-113">Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="fa544-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="fa544-114">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="fa544-114">By default, this message is a warning.</span></span> <span data-ttu-id="fa544-115">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fa544-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="fa544-116">**Identyfikator błędu:** BC40028</span><span class="sxs-lookup"><span data-stu-id="fa544-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa544-117">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="fa544-117">To correct this error</span></span>  
  
-   <span data-ttu-id="fa544-118">Jeśli procedury należy wykonać parametr tego typu konkretnego, usunąć <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fa544-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="fa544-119">Procedura nie może być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="fa544-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="fa544-120">Jeśli procedura musi być zgodne ze specyfikacją CLS, należy zmienić typ tego parametru do najbliższego typu zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="fa544-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="fa544-121">Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="fa544-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="fa544-122">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="fa544-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="fa544-123">Jeśli użytkownik są relacje z obiektami automatyzacji lub COM, należy pamiętać, że niektóre typy szerokości danych innego niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa544-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="fa544-124">Na przykład `int` jest często 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="fa544-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="fa544-125">Jeśli akceptujesz 16-bitową liczbę całkowitą z takich składników, Zadeklaruj ją jako `Short` zamiast `Integer` w sieci zarządzanej [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="fa544-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>