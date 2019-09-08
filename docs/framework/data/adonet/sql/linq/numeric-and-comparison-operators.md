---
title: Operatory numeryczne i porównania
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 7e7af725864aa191f092055fa32b403093321aa5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781293"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="27b13-102">Operatory numeryczne i porównania</span><span class="sxs-lookup"><span data-stu-id="27b13-102">Numeric and Comparison Operators</span></span>

<span data-ttu-id="27b13-103">Operatory arytmetyczne i porównania działają zgodnie z oczekiwaniami w środowisku uruchomieniowym języka wspólnego (CLR), z wyjątkiem następujących:</span><span class="sxs-lookup"><span data-stu-id="27b13-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>

- <span data-ttu-id="27b13-104">SQL nie obsługuje operatora modulo w liczbie zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="27b13-104">SQL does not support the modulus operator on floating-point numbers.</span></span>

- <span data-ttu-id="27b13-105">SQL nie obsługuje niesprawdzonej arytmetycznej.</span><span class="sxs-lookup"><span data-stu-id="27b13-105">SQL does not support unchecked arithmetic.</span></span>

- <span data-ttu-id="27b13-106">Operatory zwiększania i zmniejszania powodują skutki uboczne, gdy są używane w wyrażeniach, które nie mogą być replikowane w języku SQL, dlatego nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="27b13-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>

## <a name="supported-operators"></a><span data-ttu-id="27b13-107">Obsługiwane operatory</span><span class="sxs-lookup"><span data-stu-id="27b13-107">Supported Operators</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="27b13-108">obsługuje następujące operatory.</span><span class="sxs-lookup"><span data-stu-id="27b13-108">supports the following operators.</span></span>

- <span data-ttu-id="27b13-109">Operatory arytmetyczne w warstwie Podstawowa:</span><span class="sxs-lookup"><span data-stu-id="27b13-109">Basic arithmetic operators:</span></span>

  - `+`

  - <span data-ttu-id="27b13-110">`-`odejmowania</span><span class="sxs-lookup"><span data-stu-id="27b13-110">`-` (subtraction)</span></span>

  - `*`

  - `/`

  - <span data-ttu-id="27b13-111">Visual Basic dzielenia liczb całkowitych (`\`)</span><span class="sxs-lookup"><span data-stu-id="27b13-111">Visual Basic integer division (`\`)</span></span>

  - <span data-ttu-id="27b13-112">`%`(Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="27b13-112">`%` (Visual Basic `Mod`)</span></span>

  - `<<`

  - `>>`

  - <span data-ttu-id="27b13-113">`-`(Negacja Jednoargumentowa)</span><span class="sxs-lookup"><span data-stu-id="27b13-113">`-` (unary negation)</span></span>

- <span data-ttu-id="27b13-114">Podstawowe operatory porównania:</span><span class="sxs-lookup"><span data-stu-id="27b13-114">Basic comparison operators:</span></span>

  - <span data-ttu-id="27b13-115">Visual Basic `=` i C#`==`</span><span class="sxs-lookup"><span data-stu-id="27b13-115">Visual Basic `=` and C# `==`</span></span>

  - <span data-ttu-id="27b13-116">Visual Basic `<>` i C#`!=`</span><span class="sxs-lookup"><span data-stu-id="27b13-116">Visual Basic `<>` and C# `!=`</span></span>

  - <span data-ttu-id="27b13-117">Visual Basic`Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="27b13-117">Visual Basic `Is/IsNot`</span></span>

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a><span data-ttu-id="27b13-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27b13-118">See also</span></span>

- [<span data-ttu-id="27b13-119">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="27b13-119">Data Types and Functions</span></span>](data-types-and-functions.md)
- [<span data-ttu-id="27b13-120">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="27b13-120">C# Operators</span></span>](../../../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="27b13-121">Operatory</span><span class="sxs-lookup"><span data-stu-id="27b13-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
