---
title: Ograniczenia Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97a2e162b9f1a673fbe805a5d2ef1421cd423a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="2d714-102">Ograniczenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d714-102">Visual Basic Limitations</span></span>
<span data-ttu-id="2d714-103">Starsze niż [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wymuszane granic w kodzie, takie jak długość nazwy zmiennych dozwolona liczba zmienne w modułach i rozmiar modułu.</span><span class="sxs-lookup"><span data-stu-id="2d714-103">Earlier versions of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="2d714-104">W języku Visual Basic .NET te ograniczenia mają zostały rozluźnić, zapewniając większą swobodę w pisania i organizowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="2d714-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="2d714-105">Limity fizycznych są zależne więcej czasu wykonywania pamięci niż na zagadnienia dotyczące kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2d714-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="2d714-106">Jeśli zastosowanie ostrożnego rozwiązań w zakresie programowania i dzielenia dużych aplikacji na wiele klas i modułów, a następnie jest bardzo mało prawdopodobieństwo napotkania wewnętrznego [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="2d714-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] limitation.</span></span>  
  
 <span data-ttu-id="2d714-107">Poniżej przedstawiono pewne ograniczenia, które mogą wystąpić w ekstremalnych przypadkach:</span><span class="sxs-lookup"><span data-stu-id="2d714-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="2d714-108">**Długość nazwy.**</span><span class="sxs-lookup"><span data-stu-id="2d714-108">**Name Length.**</span></span> <span data-ttu-id="2d714-109">Istnieje maksymalna liczba znaków w nazwie co zadeklarowany element.</span><span class="sxs-lookup"><span data-stu-id="2d714-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="2d714-110">Maksymalna dotyczą ciągu całego kwalifikacji jest kwalifikowana nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="2d714-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="2d714-111">Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="2d714-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="2d714-112">**Długość wiersza.**</span><span class="sxs-lookup"><span data-stu-id="2d714-112">**Line Length.**</span></span> <span data-ttu-id="2d714-113">Brak maksimum 65535 znaków w fizycznego wiersza kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="2d714-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="2d714-114">Wiersz kodu źródłowego logicznej może być dłużej, jeśli używasz znaki kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="2d714-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="2d714-115">Zobacz [porady: przerywanie i łączenie instrukcji w Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="2d714-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="2d714-116">**Wymiary tablicy.**</span><span class="sxs-lookup"><span data-stu-id="2d714-116">**Array Dimensions.**</span></span> <span data-ttu-id="2d714-117">Istnieje maksymalna liczba wymiarów, które można zadeklarować tablicy.</span><span class="sxs-lookup"><span data-stu-id="2d714-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="2d714-118">Ogranicza liczbę indeksów, można użyć do określenia elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="2d714-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="2d714-119">Zobacz [tablicy wymiarów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="2d714-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="2d714-120">**Długość ciągu.**</span><span class="sxs-lookup"><span data-stu-id="2d714-120">**String Length.**</span></span> <span data-ttu-id="2d714-121">Istnieje maksymalna liczba znaków Unicode, których można przechowywać w jednym ciągu.</span><span class="sxs-lookup"><span data-stu-id="2d714-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="2d714-122">Zobacz [dane typu ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="2d714-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="2d714-123">**Długość ciągu środowiska.**</span><span class="sxs-lookup"><span data-stu-id="2d714-123">**Environment String Length.**</span></span> <span data-ttu-id="2d714-124">Brak znaków 32768 do dowolnego ciągu środowiska używany jako argument wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2d714-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="2d714-125">Jest to ograniczenie na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="2d714-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d714-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d714-126">See Also</span></span>  
 [<span data-ttu-id="2d714-127">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="2d714-127">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="2d714-128">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="2d714-128">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
