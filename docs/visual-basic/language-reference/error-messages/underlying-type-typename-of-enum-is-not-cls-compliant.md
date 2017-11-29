---
title: "Typ podstawowy &lt;typename&gt; Enum nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords: BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68b57dc82737b72463b7fcf1a3e50934e1562c31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="082c8-102">Typ podstawowy &lt;typename&gt; Enum nie jest zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="082c8-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="082c8-103">Typ danych określony dla tego wyliczenia nie jest częścią [niezależność od języka i elementy niezależne od języka](https://msdn.microsoft.com/library/12a7a7h3) (ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="082c8-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span> <span data-ttu-id="082c8-104">Nie jest to błąd w ramach składnika, ponieważ [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] obsługuje tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="082c8-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] support this data type.</span></span> <span data-ttu-id="082c8-105">Jednak inny składnik napisana ściśle kodu zgodne ze specyfikacją CLS nie może obsługiwać ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="082c8-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="082c8-106">Takie składnika nie można pomyślnie interakcyjnie składnika.</span><span class="sxs-lookup"><span data-stu-id="082c8-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="082c8-107">Następujące [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typy danych nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="082c8-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="082c8-108">SByte — typ danych</span><span class="sxs-lookup"><span data-stu-id="082c8-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="082c8-109">Uinteger — typ danych</span><span class="sxs-lookup"><span data-stu-id="082c8-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="082c8-110">Ulong — typ danych</span><span class="sxs-lookup"><span data-stu-id="082c8-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="082c8-111">Ushort — typ danych</span><span class="sxs-lookup"><span data-stu-id="082c8-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="082c8-112">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="082c8-112">By default, this message is a warning.</span></span> <span data-ttu-id="082c8-113">Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="082c8-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="082c8-114">**Identyfikator błędu:** BC40032</span><span class="sxs-lookup"><span data-stu-id="082c8-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="082c8-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="082c8-115">To correct this error</span></span>  
  
-   <span data-ttu-id="082c8-116">Jeśli składnik interfejsy tylko z innymi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] składniki lub nie nie interfejsu z innymi składnikami, jest konieczne wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="082c8-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="082c8-117">Jeśli są relacje ze składnikiem nie napisane dla [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], może być możliwe ustalenie, albo za pomocą odbicia lub z dokumentacji, czy ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="082c8-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="082c8-118">Jeśli tak, nie jest konieczne wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="082c8-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="082c8-119">Jeśli użytkownik są relacje ze składnikiem, który nie obsługuje tego typu danych, należy ją zastąpić najbliższego CLS typu.</span><span class="sxs-lookup"><span data-stu-id="082c8-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="082c8-120">Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="082c8-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="082c8-121">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="082c8-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="082c8-122">Jeśli użytkownik są relacje z obiektami automatyzacji lub COM, należy pamiętać, że niektóre typy szerokości danych innego niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="082c8-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="082c8-123">Na przykład `uint` jest często 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="082c8-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="082c8-124">Jeśli argument 16-bitowych jest przekazywany do takich składników, Zadeklaruj ją jako `UShort` zamiast `UInteger` w sieci zarządzanej [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="082c8-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082c8-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="082c8-125">See Also</span></span>  
 [<span data-ttu-id="082c8-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="082c8-126">Reflection</span></span>](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
 [<span data-ttu-id="082c8-127">Odbicie</span><span class="sxs-lookup"><span data-stu-id="082c8-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="082c8-128">\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="082c8-128">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
