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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663287"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="42225-102">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42225-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="42225-103">Proces zmiany wartości z jednego typu danych na inny typ jest nazywany *konwersji*.</span><span class="sxs-lookup"><span data-stu-id="42225-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="42225-104">Konwersje są albo *rozszerzanie* lub *zawężanie*, w zależności od pojemności danych typów, które są zaangażowani.</span><span class="sxs-lookup"><span data-stu-id="42225-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="42225-105">Są one również *niejawne* lub *jawne*, w zależności od składni w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="42225-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42225-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="42225-106">In This Section</span></span>  
 [<span data-ttu-id="42225-107">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="42225-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="42225-108">W tym artykule wyjaśniono konwersji niejawnych, czy typ docelowy może przechowywać dane.</span><span class="sxs-lookup"><span data-stu-id="42225-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="42225-109">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="42225-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="42225-110">W tym artykule omówiono konwersji niejawnych, czy Visual Basic wykonuje je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="42225-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="42225-111">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="42225-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="42225-112">Ilustruje Konwertowanie pomiędzy ciągami a numeryczne, `Boolean`, lub wartości daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="42225-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="42225-113">Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42225-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="42225-114">Pokazuje sposób konwertowania `Object` zmiennej do jakichkolwiek innych typów danych.</span><span class="sxs-lookup"><span data-stu-id="42225-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="42225-115">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="42225-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="42225-116">Przeprowadzi Cię przez proces konwersji między macierzami z różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="42225-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42225-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="42225-117">Related Sections</span></span>  
 [<span data-ttu-id="42225-118">Typy danych</span><span class="sxs-lookup"><span data-stu-id="42225-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="42225-119">Wprowadza typy danych Visual Basic i zawiera opis sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="42225-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="42225-120">Typy danych</span><span class="sxs-lookup"><span data-stu-id="42225-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="42225-121">Wyświetla listę typów podstawowych danych pochodzącego z języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="42225-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="42225-122">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="42225-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="42225-123">W tym artykule omówiono niektóre typowe problemy, które mogą wystąpić podczas pracy z typami danych.</span><span class="sxs-lookup"><span data-stu-id="42225-123">Discusses some common problems that can arise when working with data types.</span></span>
