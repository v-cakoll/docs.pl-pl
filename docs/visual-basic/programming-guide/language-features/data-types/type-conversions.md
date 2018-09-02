---
title: Konwersje plików w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
ms.openlocfilehash: 026b2a250abfac0782feb0946bc50a94f504f7ed
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404060"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="fcef5-102">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcef5-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="fcef5-103">Proces zmiany wartości z jednego typu danych na inny typ jest nazywany *konwersji*.</span><span class="sxs-lookup"><span data-stu-id="fcef5-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="fcef5-104">Konwersje są albo *rozszerzanie* lub *zawężanie*, w zależności od pojemności danych typów, które są zaangażowani.</span><span class="sxs-lookup"><span data-stu-id="fcef5-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="fcef5-105">Są one również *niejawne* lub *jawne*, w zależności od składni w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="fcef5-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fcef5-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fcef5-106">In This Section</span></span>  
 [<span data-ttu-id="fcef5-107">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="fcef5-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="fcef5-108">W tym artykule wyjaśniono konwersji niejawnych, czy typ docelowy może przechowywać dane.</span><span class="sxs-lookup"><span data-stu-id="fcef5-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="fcef5-109">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="fcef5-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="fcef5-110">W tym artykule omówiono konwersji niejawnych, czy Visual Basic wykonuje je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="fcef5-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="fcef5-111">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="fcef5-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="fcef5-112">Ilustruje Konwertowanie pomiędzy ciągami a numeryczne, `Boolean`, lub wartości daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="fcef5-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="fcef5-113">Porady: konwertowanie obiektu na inny typ w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcef5-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="fcef5-114">Pokazuje sposób konwertowania `Object` zmiennej do jakichkolwiek innych typów danych.</span><span class="sxs-lookup"><span data-stu-id="fcef5-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="fcef5-115">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="fcef5-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="fcef5-116">Przeprowadzi Cię przez proces konwersji między macierzami z różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="fcef5-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fcef5-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fcef5-117">Related Sections</span></span>  
 [<span data-ttu-id="fcef5-118">Typy danych</span><span class="sxs-lookup"><span data-stu-id="fcef5-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="fcef5-119">Wprowadza typy danych Visual Basic i zawiera opis sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="fcef5-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="fcef5-120">Typy danych</span><span class="sxs-lookup"><span data-stu-id="fcef5-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="fcef5-121">Wyświetla listę typów podstawowych danych pochodzącego z języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fcef5-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="fcef5-122">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="fcef5-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="fcef5-123">W tym artykule omówiono niektóre typowe problemy, które mogą wystąpić podczas pracy z typami danych.</span><span class="sxs-lookup"><span data-stu-id="fcef5-123">Discusses some common problems that can arise when working with data types.</span></span>
