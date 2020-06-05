---
title: Typ źródłowy <typename> wyliczenia jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 79faf0038b2b313bdc21e12c8ae76854bcd6957f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406576"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a><span data-ttu-id="432e7-102">Typ źródłowy \<typename> wyliczenia jest niezgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="432e7-102">Underlying type \<typename> of Enum is not CLS-compliant</span></span>
<span data-ttu-id="432e7-103">Typ danych określony dla tego wyliczenia nie jest częścią [niezależności od języka i składników niezależnych od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="432e7-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="432e7-104">Nie jest to błąd w składniku, ponieważ .NET Framework i Visual Basic obsługują ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="432e7-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="432e7-105">Jednak inny składnik zapisany w kodzie zgodnym ze specyfikacją CLS może nie obsługiwać tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="432e7-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="432e7-106">Taki składnik może nie być w stanie pomyślnie korzystać z składnika.</span><span class="sxs-lookup"><span data-stu-id="432e7-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="432e7-107">Następujące Visual Basic typy danych nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="432e7-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="432e7-108">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="432e7-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="432e7-109">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="432e7-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="432e7-110">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="432e7-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="432e7-111">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="432e7-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="432e7-112">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="432e7-112">By default, this message is a warning.</span></span> <span data-ttu-id="432e7-113">Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="432e7-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="432e7-114">**Identyfikator błędu:** BC40032</span><span class="sxs-lookup"><span data-stu-id="432e7-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="432e7-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="432e7-115">To correct this error</span></span>  
  
- <span data-ttu-id="432e7-116">Jeśli składnik obsługuje tylko inne składniki .NET Framework lub nie ma interfejsu z innymi składnikami, nie trzeba zmieniać żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="432e7-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="432e7-117">Jeśli korzystasz z składnika, który nie został zapisany dla .NET Framework, możesz określić, poprzez odbicie lub z dokumentacji, czy obsługuje ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="432e7-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="432e7-118">W przeciwnym razie nie trzeba zmieniać żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="432e7-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="432e7-119">W przypadku współdziałania ze składnikiem, który nie obsługuje tego typu danych, należy zamienić go na najbliższy typ zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="432e7-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="432e7-120">Na przykład, zamiast `UInteger` można użyć, `Integer` Jeśli nie potrzebujesz zakresu wartości powyżej 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="432e7-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="432e7-121">Jeśli potrzebujesz rozszerzonego zakresu, możesz zamienić `UInteger` na `Long` .</span><span class="sxs-lookup"><span data-stu-id="432e7-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="432e7-122">Jeśli masz połączenie z obiektami automatyzacji lub COM, pamiętaj, że niektóre typy mają różne szerokości danych niż w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="432e7-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="432e7-123">Na przykład `uint` często jest 16 bitów w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="432e7-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="432e7-124">Jeśli przekazujesz argument 16-bitowy do takiego składnika, zadeklaruj go jako `UShort` zamiast `UInteger` w kodzie zarządzanym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="432e7-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="432e7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="432e7-125">See also</span></span>

- [<span data-ttu-id="432e7-126">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="432e7-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="432e7-127">Odbicie</span><span class="sxs-lookup"><span data-stu-id="432e7-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
