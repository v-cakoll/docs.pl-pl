---
title: "Typ &lt;typename&gt; nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36a49ccf7d2185c26ef8d23eebea216cc193d951
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="eb9b3-102">Typ &lt;typename&gt; nie jest zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="eb9b3-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="eb9b3-103">Zmienną, właściwością lub funkcji, zwracany jest zadeklarowana z typem danych, który nie jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="eb9b3-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="eb9b3-104">Dla aplikacji, aby było zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), należy użyć tylko typów zgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="eb9b3-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="eb9b3-105">Następujące [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typy danych nie są zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="eb9b3-105">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="eb9b3-106">SByte, typ danych</span><span class="sxs-lookup"><span data-stu-id="eb9b3-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="eb9b3-107">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="eb9b3-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="eb9b3-108">ULong, typ danych</span><span class="sxs-lookup"><span data-stu-id="eb9b3-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="eb9b3-109">UShort, typ danych</span><span class="sxs-lookup"><span data-stu-id="eb9b3-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="eb9b3-110">**Identyfikator błędu:** BC40041</span><span class="sxs-lookup"><span data-stu-id="eb9b3-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb9b3-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="eb9b3-111">To correct this error</span></span>  
  
-   <span data-ttu-id="eb9b3-112">Jeśli aplikacja musi być zgodne ze specyfikacją CLS, Zmień typ danych tego elementu do najbliższego typu zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="eb9b3-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="eb9b3-113">Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="eb9b3-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="eb9b3-114">Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.</span><span class="sxs-lookup"><span data-stu-id="eb9b3-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="eb9b3-115">Jeśli aplikacja nie musi być zgodne ze specyfikacją CLS, jest konieczne wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="eb9b3-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="eb9b3-116">Należy pamiętać o jego niezgodności jednak.</span><span class="sxs-lookup"><span data-stu-id="eb9b3-116">You should be aware of its noncompliance, however.</span></span>