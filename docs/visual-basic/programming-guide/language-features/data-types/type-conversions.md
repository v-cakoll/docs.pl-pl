---
title: "Konwersje plików w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b46d813b4fcadd975d87b235e9f3350a365949fa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="1f9a0-102">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1f9a0-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="1f9a0-103">Proces zmiany wartości z jednego typu danych do innego typu, jest nazywany *konwersji*.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="1f9a0-104">Konwersje są albo *rozszerzanie* lub *zawężanie*, w zależności od możliwości typy danych.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="1f9a0-105">Są one również *niejawne* lub *jawne*w oparciu o składni w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f9a0-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1f9a0-106">In This Section</span></span>  
 [<span data-ttu-id="1f9a0-107">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="1f9a0-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="1f9a0-108">W tym artykule wyjaśniono konwersje sklasyfikowanych według tego, czy typ docelowy może przechowywać dane.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="1f9a0-109">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="1f9a0-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="1f9a0-110">W tym artykule omówiono konwersje sklasyfikowane przez czy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wykonuje je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-110">Discusses conversions classified by whether [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] performs them automatically.</span></span>  
  
 [<span data-ttu-id="1f9a0-111">Konwertowanie pomiędzy ciągami a innymi typami</span><span class="sxs-lookup"><span data-stu-id="1f9a0-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="1f9a0-112">Przedstawia Konwertowanie pomiędzy ciągami a liczbowe, `Boolean`, lub wartości daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="1f9a0-113">Porady: konwertowanie obiektu do innego typu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1f9a0-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="1f9a0-114">Pokazuje sposób konwertowania `Object` zmienną do innego typu danych.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="1f9a0-115">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="1f9a0-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="1f9a0-116">Przeprowadza użytkownika przez proces konwersji między macierzami z różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1f9a0-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1f9a0-117">Related Sections</span></span>  
 [<span data-ttu-id="1f9a0-118">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1f9a0-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="1f9a0-119">Wprowadza [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typów danych, a w tym artykule opisano sposób ich użycia.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-119">Introduces the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="1f9a0-120">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1f9a0-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="1f9a0-121">Wyświetla listę typów podstawowych danych dostarczonych przez [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f9a0-121">Lists the elementary data types supplied by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [<span data-ttu-id="1f9a0-122">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="1f9a0-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="1f9a0-123">W tym artykule omówiono niektóre typowe problemy, które mogą wystąpić podczas pracy z typów danych.</span><span class="sxs-lookup"><span data-stu-id="1f9a0-123">Discusses some common problems that can arise when working with data types.</span></span>
