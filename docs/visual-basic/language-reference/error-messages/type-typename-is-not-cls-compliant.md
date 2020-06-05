---
title: Typ „<typename>” jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: eacf5036ebc6fc31dfa0e8de39c4fb574c9072b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386961"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="eda99-102">Typ „\<typename>” jest niezgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="eda99-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="eda99-103">Zmienna, właściwość lub return funkcji jest zadeklarowana z typem danych, który jest niezgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="eda99-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="eda99-104">Aby aplikacja była zgodna z [niezależnością od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), musi używać tylko typów zgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="eda99-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="eda99-105">Następujące Visual Basic typy danych nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="eda99-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="eda99-106">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="eda99-106">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="eda99-107">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="eda99-107">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="eda99-108">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="eda99-108">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="eda99-109">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="eda99-109">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="eda99-110">**Identyfikator błędu:** BC40041</span><span class="sxs-lookup"><span data-stu-id="eda99-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eda99-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="eda99-111">To correct this error</span></span>  
  
- <span data-ttu-id="eda99-112">Jeśli aplikacja musi być zgodna ze specyfikacją CLS, Zmień typ danych tego elementu na najbliższy typ zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="eda99-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="eda99-113">Na przykład, zamiast `UInteger` można użyć, `Integer` Jeśli nie potrzebujesz zakresu wartości powyżej 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="eda99-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="eda99-114">Jeśli potrzebujesz rozszerzonego zakresu, możesz zamienić `UInteger` na `Long` .</span><span class="sxs-lookup"><span data-stu-id="eda99-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="eda99-115">Jeśli aplikacja nie musi być zgodna ze specyfikacją CLS, nie trzeba nic zmieniać.</span><span class="sxs-lookup"><span data-stu-id="eda99-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="eda99-116">Należy jednak pamiętać o jego niezgodności.</span><span class="sxs-lookup"><span data-stu-id="eda99-116">You should be aware of its noncompliance, however.</span></span>
