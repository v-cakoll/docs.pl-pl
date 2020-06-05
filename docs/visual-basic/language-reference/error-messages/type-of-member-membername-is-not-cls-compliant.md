---
title: Typ członka „<membername>” nie jest zgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 030cb31b8f1ba0e8eaa82eeb8e37153411a53404
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400308"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="d39bb-102">Typ członka „\<membername>” nie jest zgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="d39bb-102">Type of member '\<membername>' is not CLS-compliant</span></span>
<span data-ttu-id="d39bb-103">Typ danych określony dla tego elementu członkowskiego nie jest częścią [niezależną od języka i składników niezależnych od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="d39bb-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="d39bb-104">Nie jest to błąd w składniku, ponieważ .NET Framework i Visual Basic obsługują ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="d39bb-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="d39bb-105">Jednak inny składnik zapisany w kodzie zgodnym ze specyfikacją CLS może nie obsługiwać tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="d39bb-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="d39bb-106">Taki składnik może nie być w stanie pomyślnie korzystać z składnika.</span><span class="sxs-lookup"><span data-stu-id="d39bb-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="d39bb-107">Następujące Visual Basic typy danych nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="d39bb-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="d39bb-108">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="d39bb-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="d39bb-109">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="d39bb-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="d39bb-110">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="d39bb-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="d39bb-111">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="d39bb-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="d39bb-112">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="d39bb-112">By default, this message is a warning.</span></span> <span data-ttu-id="d39bb-113">Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d39bb-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d39bb-114">**Identyfikator błędu:** BC40025</span><span class="sxs-lookup"><span data-stu-id="d39bb-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d39bb-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d39bb-115">To correct this error</span></span>  
  
- <span data-ttu-id="d39bb-116">Jeśli składnik obsługuje tylko inne składniki .NET Framework lub nie ma interfejsu z innymi składnikami, nie trzeba zmieniać żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="d39bb-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="d39bb-117">Jeśli korzystasz z składnika, który nie został zapisany dla .NET Framework, możesz określić, poprzez odbicie lub z dokumentacji, czy obsługuje ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="d39bb-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="d39bb-118">W przeciwnym razie nie trzeba zmieniać żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="d39bb-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="d39bb-119">W przypadku współdziałania ze składnikiem, który nie obsługuje tego typu danych, należy zamienić go na najbliższy typ zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d39bb-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="d39bb-120">Na przykład, zamiast `UInteger` można użyć, `Integer` Jeśli nie potrzebujesz zakresu wartości powyżej 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="d39bb-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="d39bb-121">Jeśli potrzebujesz rozszerzonego zakresu, możesz zamienić `UInteger` na `Long` .</span><span class="sxs-lookup"><span data-stu-id="d39bb-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="d39bb-122">Jeśli masz połączenie z obiektami automatyzacji lub COM, pamiętaj, że niektóre typy mają różne szerokości danych niż w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d39bb-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="d39bb-123">Na przykład `uint` często jest 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="d39bb-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="d39bb-124">Jeśli przekazujesz argument 16-bitowy do takiego składnika, zadeklaruj go jako `UShort` zamiast `UInteger` w kodzie zarządzanym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d39bb-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39bb-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d39bb-125">See also</span></span>

- [<span data-ttu-id="d39bb-126">Odbicie</span><span class="sxs-lookup"><span data-stu-id="d39bb-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
