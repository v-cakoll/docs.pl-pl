---
title: Typ członka „<membername>” nie jest zgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: f6f66617774dccff4450cce42904126acf5c3769
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590685"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="a58e0-102">Typ elementu członkowskiego "\<membername >' nie jest zgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="a58e0-102">Type of member '\<membername>' is not CLS-compliant</span></span>
<span data-ttu-id="a58e0-103">Typ danych określony dla tego elementu członkowskiego nie jest częścią [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="a58e0-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="a58e0-104">Nie jest błąd wewnątrz składnika, ponieważ .NET Framework i Visual Basic obsługuje ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="a58e0-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="a58e0-105">Jednak inny składnik, napisany w ściśle zgodna ze specyfikacją CLS kod nie może obsługiwać tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="a58e0-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="a58e0-106">Takiego składnika nie może być możliwość interakcji pomyślnie z danego składnika.</span><span class="sxs-lookup"><span data-stu-id="a58e0-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="a58e0-107">Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="a58e0-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="a58e0-108">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="a58e0-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="a58e0-109">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="a58e0-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="a58e0-110">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="a58e0-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="a58e0-111">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="a58e0-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="a58e0-112">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="a58e0-112">By default, this message is a warning.</span></span> <span data-ttu-id="a58e0-113">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a58e0-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a58e0-114">**Identyfikator błędu:** BC40025</span><span class="sxs-lookup"><span data-stu-id="a58e0-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a58e0-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a58e0-115">To correct this error</span></span>  
  
- <span data-ttu-id="a58e0-116">Jeśli składnik interfejsy tylko z innymi składnikami systemu .NET Framework lub nie współpracować z innymi składnikami, nie musisz wprowadzić zmiany.</span><span class="sxs-lookup"><span data-stu-id="a58e0-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="a58e0-117">Jeśli są komunikowanie się za pomocą składnika nie jest przeznaczony dla .NET Framework, można ustalić, za pomocą odbicia lub dokumentacji, czy obsługuje ona tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="a58e0-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="a58e0-118">Jeśli tak jest, nie musisz wprowadzić zmiany.</span><span class="sxs-lookup"><span data-stu-id="a58e0-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="a58e0-119">Jeśli są komunikowanie się ze składnikiem, który nie obsługuje tego typu danych, można zastąpić go z najbliższego typem zgodnym ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="a58e0-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="a58e0-120">Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="a58e0-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="a58e0-121">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="a58e0-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="a58e0-122">Czy komunikowanie się z obiektami automatyzacji lub COM, pamiętać, że niektóre typy mają różnych szerokościach danych niż na platformie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a58e0-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="a58e0-123">Na przykład `uint` często jest 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="a58e0-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="a58e0-124">Jeśli przekazujesz 16-bitowy argument do takiego składnika, Zadeklaruj go jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a58e0-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a58e0-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a58e0-125">See also</span></span>

- [<span data-ttu-id="a58e0-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="a58e0-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
