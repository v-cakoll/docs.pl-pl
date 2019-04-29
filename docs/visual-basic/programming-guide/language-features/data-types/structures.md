---
title: Struktury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic]
- user-defined data types [Visual Basic], structures
- user-defined types [Visual Basic], about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
ms.openlocfilehash: ebfc82665bb18d96c83db8f29a6c206a9a71fd7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663365"
---
# <a name="structures-visual-basic"></a><span data-ttu-id="31758-102">Struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31758-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="31758-103">A *struktury* jest uogólnienie typu zdefiniowanego przez użytkownika (UDT) obsługiwane przez poprzednie wersje programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="31758-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of Visual Basic.</span></span> <span data-ttu-id="31758-104">Oprócz pól struktury można ujawnić właściwości, metody i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="31758-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="31758-105">Struktura można zaimplementować jeden lub więcej interfejsów i można zadeklarować poziomów dostępu poszczególnych dla każdego pola.</span><span class="sxs-lookup"><span data-stu-id="31758-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="31758-106">Można łączyć elementy danych różnych typów, aby utworzyć strukturę.</span><span class="sxs-lookup"><span data-stu-id="31758-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="31758-107">Struktura kojarzy co najmniej jeden *elementy* ze sobą oraz z samej strukturze.</span><span class="sxs-lookup"><span data-stu-id="31758-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="31758-108">Kiedy Deklarujesz struktury, staje się *złożonego typu danych*, i możesz deklarować zmienne tego typu.</span><span class="sxs-lookup"><span data-stu-id="31758-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="31758-109">Struktury są przydatne, gdy chcesz, aby pojedynczej zmiennej do przechowywania kilku powiązanych informacji.</span><span class="sxs-lookup"><span data-stu-id="31758-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="31758-110">Na przykład możesz chcieć Zachowaj nazwę, numer wewnętrzny i wynagrodzenia pracownika.</span><span class="sxs-lookup"><span data-stu-id="31758-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="31758-111">Te informacje można użyć kilku zmiennych lub można zdefiniować strukturę i użyć jej do zmiennej pojedynczego pracownika.</span><span class="sxs-lookup"><span data-stu-id="31758-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="31758-112">Zaletą struktury staje się jasne, jeśli masz wielu pracowników i w związku z tym wiele wystąpień zmiennej.</span><span class="sxs-lookup"><span data-stu-id="31758-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31758-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="31758-113">In This Section</span></span>  
 [<span data-ttu-id="31758-114">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="31758-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="31758-115">Pokazuje sposób deklarowania struktury i jej elementów.</span><span class="sxs-lookup"><span data-stu-id="31758-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="31758-116">Zmienne struktur</span><span class="sxs-lookup"><span data-stu-id="31758-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="31758-117">Obejmuje Przypisywanie strukturę do zmiennej i uzyskiwania dostępu do jego elementów.</span><span class="sxs-lookup"><span data-stu-id="31758-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="31758-118">Struktury oraz inne elementy programowania</span><span class="sxs-lookup"><span data-stu-id="31758-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="31758-119">Zawiera podsumowanie sposobu interakcji struktury z tablicami, obiekty, procedury i siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="31758-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="31758-120">Struktury i klasy</span><span class="sxs-lookup"><span data-stu-id="31758-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="31758-121">W tym artykule opisano podobieństwa i różnice między strukturami i klasami.</span><span class="sxs-lookup"><span data-stu-id="31758-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="31758-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="31758-122">Related Sections</span></span>  
 [<span data-ttu-id="31758-123">Typy danych</span><span class="sxs-lookup"><span data-stu-id="31758-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="31758-124">Wprowadza typy danych Visual Basic i zawiera opis sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="31758-124">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="31758-125">Typy danych</span><span class="sxs-lookup"><span data-stu-id="31758-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="31758-126">Wyświetla listę typów podstawowych danych pochodzącego z języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="31758-126">Lists the elementary data types supplied by Visual Basic.</span></span>
