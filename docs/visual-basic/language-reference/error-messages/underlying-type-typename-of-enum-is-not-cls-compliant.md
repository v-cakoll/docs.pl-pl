---
title: Typ bazowy &lt;typename&gt; wyliczenia jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: ceda7e6ed6fc1744de14afcb0245ebabbd7fa733
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674797"
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="d9d30-102">Typ bazowy &lt;typename&gt; wyliczenia jest niezgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="d9d30-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="d9d30-103">Typ danych określony dla tego wyliczenia jest częścią [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="d9d30-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="d9d30-104">Nie jest to błąd w ramach składnika, ponieważ [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] i język Visual Basic obsługuje ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="d9d30-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and Visual Basic support this data type.</span></span> <span data-ttu-id="d9d30-105">Jednak inny składnik, napisany w ściśle zgodna ze specyfikacją CLS kod nie może obsługiwać tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="d9d30-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="d9d30-106">Takiego składnika nie może być możliwość interakcji pomyślnie z danego składnika.</span><span class="sxs-lookup"><span data-stu-id="d9d30-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="d9d30-107">Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="d9d30-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="d9d30-108">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="d9d30-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="d9d30-109">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="d9d30-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="d9d30-110">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="d9d30-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="d9d30-111">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="d9d30-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="d9d30-112">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="d9d30-112">By default, this message is a warning.</span></span> <span data-ttu-id="d9d30-113">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d9d30-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d9d30-114">**Identyfikator błędu:** BC40032</span><span class="sxs-lookup"><span data-stu-id="d9d30-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9d30-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d9d30-115">To correct this error</span></span>  
  
-   <span data-ttu-id="d9d30-116">Jeśli składnik interfejsy tylko z innymi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] składników lub czy nie współpracować z innymi składnikami, nie trzeba wprowadzić zmiany.</span><span class="sxs-lookup"><span data-stu-id="d9d30-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="d9d30-117">Jeśli są komunikowanie się za pomocą składnika nie jest przeznaczony dla [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], może być możliwe ustalenie, albo za pomocą odbicia lub dokumentacji, czy ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="d9d30-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="d9d30-118">Jeśli tak jest, nie musisz wprowadzić zmiany.</span><span class="sxs-lookup"><span data-stu-id="d9d30-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="d9d30-119">Jeśli są komunikowanie się ze składnikiem, który nie obsługuje tego typu danych, można zastąpić go z najbliższego typem zgodnym ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d9d30-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="d9d30-120">Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="d9d30-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="d9d30-121">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="d9d30-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="d9d30-122">Jeśli są komunikowanie się z obiektami automatyzacji lub COM, należy pamiętać o tym, że niektóre typy mają różnych szerokościach danych niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9d30-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="d9d30-123">Na przykład `uint` często jest 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="d9d30-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="d9d30-124">Jeśli przekazujesz 16-bitowy argument do takiego składnika, Zadeklaruj go jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d9d30-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d30-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9d30-125">See also</span></span>
- [<span data-ttu-id="d9d30-126">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9d30-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="d9d30-127">Odbicie</span><span class="sxs-lookup"><span data-stu-id="d9d30-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)

