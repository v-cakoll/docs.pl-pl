---
title: Typ podstawowy &lt;typename&gt; Enum nie jest zgodne ze specyfikacją CLS
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44727a60f99e0d00cde7d569e2017928551b1812
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="b7502-102">Typ podstawowy &lt;typename&gt; Enum nie jest zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="b7502-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="b7502-103">Typ danych określony dla tego wyliczenia nie jest częścią [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="b7502-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="b7502-104">Nie jest to błąd w ramach składnika, ponieważ [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] i Visual Basic obsługuje tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="b7502-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and Visual Basic support this data type.</span></span> <span data-ttu-id="b7502-105">Jednak inny składnik napisana ściśle kodu zgodne ze specyfikacją CLS nie może obsługiwać ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="b7502-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="b7502-106">Takie składnika nie można pomyślnie interakcyjnie składnika.</span><span class="sxs-lookup"><span data-stu-id="b7502-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="b7502-107">Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="b7502-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="b7502-108">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="b7502-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="b7502-109">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="b7502-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="b7502-110">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="b7502-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="b7502-111">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="b7502-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="b7502-112">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="b7502-112">By default, this message is a warning.</span></span> <span data-ttu-id="b7502-113">Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b7502-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b7502-114">**Identyfikator błędu:** BC40032</span><span class="sxs-lookup"><span data-stu-id="b7502-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b7502-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b7502-115">To correct this error</span></span>  
  
-   <span data-ttu-id="b7502-116">Jeśli składnik interfejsy tylko z innymi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] składniki lub nie nie interfejsu z innymi składnikami, jest konieczne wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="b7502-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="b7502-117">Jeśli są relacje ze składnikiem nie napisane dla [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], może być możliwe ustalenie, albo za pomocą odbicia lub z dokumentacji, czy ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="b7502-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="b7502-118">Jeśli tak, nie jest konieczne wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="b7502-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="b7502-119">Jeśli użytkownik są relacje ze składnikiem, który nie obsługuje tego typu danych, należy ją zastąpić najbliższego CLS typu.</span><span class="sxs-lookup"><span data-stu-id="b7502-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="b7502-120">Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="b7502-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="b7502-121">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="b7502-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="b7502-122">Jeśli użytkownik są relacje z obiektami automatyzacji lub COM, należy pamiętać, że niektóre typy szerokości danych innego niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7502-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="b7502-123">Na przykład `uint` jest często 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="b7502-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="b7502-124">Jeśli argument 16-bitowych jest przekazywany do takich składników, Zadeklaruj ją jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b7502-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7502-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7502-125">See Also</span></span>  
 [<span data-ttu-id="b7502-126">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7502-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="b7502-127">Odbicie</span><span class="sxs-lookup"><span data-stu-id="b7502-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 
