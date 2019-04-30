---
title: Typ „<typename>” jest niezgodny ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 243f51b3e6c798c82fdbe7b28557c4f96c728bf2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764377"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="17de6-102">Typ \<typename > nie jest zgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="17de6-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="17de6-103">Zmienna, właściwość lub funkcji, zwracany jest zadeklarowany z typem danych, który nie jest zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="17de6-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="17de6-104">Dla aplikacji, aby zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), jej używać tylko typów zgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="17de6-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="17de6-105">Następujące typy danych Visual Basic nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="17de6-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="17de6-106">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="17de6-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="17de6-107">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="17de6-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="17de6-108">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="17de6-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="17de6-109">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="17de6-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="17de6-110">**Identyfikator błędu:** BC40041</span><span class="sxs-lookup"><span data-stu-id="17de6-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="17de6-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="17de6-111">To correct this error</span></span>  
  
- <span data-ttu-id="17de6-112">Jeśli aplikacja musi być zgodny ze specyfikacją CLS, należy zmienić typ danych tego elementu do najbliższego typu zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="17de6-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="17de6-113">Na przykład, zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości ponad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="17de6-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="17de6-114">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="17de6-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="17de6-115">Jeśli aplikacja nie musi być zgodne ze specyfikacją CLS, nie musisz wprowadzić zmiany.</span><span class="sxs-lookup"><span data-stu-id="17de6-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="17de6-116">Należy pamiętać o jego niezgodności, jednak.</span><span class="sxs-lookup"><span data-stu-id="17de6-116">You should be aware of its noncompliance, however.</span></span>