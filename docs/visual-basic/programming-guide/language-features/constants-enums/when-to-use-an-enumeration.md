---
title: "Kiedy stosować wyliczanie (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3b2937cc71c0c31bd8dce3d77fb33f48e1b5750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="a4c11-102">Kiedy stosować wyliczanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4c11-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="a4c11-103">Wyliczenia oferują prosty sposób pracy z zestawów powiązanych stałe.</span><span class="sxs-lookup"><span data-stu-id="a4c11-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="a4c11-104">Jako wyliczenia lub `Enum`, jest nazwa symboliczna dla zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="a4c11-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="a4c11-105">Wyliczenia są traktowane jako typy danych i można je utworzyć zestawy stałych do użycia z zmiennych i właściwości.</span><span class="sxs-lookup"><span data-stu-id="a4c11-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="a4c11-106">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="a4c11-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="a4c11-107">Zawsze, gdy procedura akceptuje ograniczony zestaw zmiennych, należy wziąć pod uwagę przy użyciu wyliczania.</span><span class="sxs-lookup"><span data-stu-id="a4c11-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="a4c11-108">Wyliczenia upewnij się jaśniejszy i czytelność kodu, szczególnie w przypadku, gdy są używane łatwy do rozpoznania nazwy.</span><span class="sxs-lookup"><span data-stu-id="a4c11-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="a4c11-109">Korzyści wynikające ze stosowania wyliczenia obejmują:</span><span class="sxs-lookup"><span data-stu-id="a4c11-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="a4c11-110">Zmniejsza liczbę błędów spowodowanych przez Transponowanie lub błędne liczby.</span><span class="sxs-lookup"><span data-stu-id="a4c11-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="a4c11-111">Można łatwo zmienić wartości w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="a4c11-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="a4c11-112">Powoduje, że kod czytelności, co oznacza, że jest mniej prawdopodobne, że błędy będą pełzanie do niego.</span><span class="sxs-lookup"><span data-stu-id="a4c11-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="a4c11-113">Zapewnia zgodność z nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="a4c11-113">Ensures forward compatibility.</span></span> <span data-ttu-id="a4c11-114">Z wyliczenia kod jest mniej prawdopodobne się niepowodzeniem, jeśli w przyszłości użytkownik wprowadza zmiany wartości odpowiadających nazwy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="a4c11-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="a4c11-115">Wyliczenia nazw</span><span class="sxs-lookup"><span data-stu-id="a4c11-115">Naming Enumerations</span></span>  
 <span data-ttu-id="a4c11-116">Elementy członkowskie wyliczenia używać konwencji nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="a4c11-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="a4c11-117">Gdy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] napotka nazwę elementu członkowskiego wyliczenia może zostać zgłoszony wyjątek, jeśli inne biblioteki typu występującego w odwołaniu nie ma takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="a4c11-117">When [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="a4c11-118">Użyj unikatowy prefiks, który identyfikuje wartości z aplikacją lub składnikiem albo.</span><span class="sxs-lookup"><span data-stu-id="a4c11-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="a4c11-119">Podczas odwoływania się do elementu członkowskiego wyliczenia, musisz nazwy elementu członkowskiego o nazwie wyliczenia, czyli użyj `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a4c11-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="a4c11-120">Aby uzyskać więcej informacji, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="a4c11-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="a4c11-121">Wstępnie zdefiniowane wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a4c11-121">Predefined Enumerations</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a4c11-122">udostępnia wiele wstępnie zdefiniowanych wyliczenia, takich jak `FirstDayOfWeek` i `MsgBoxResult`, aby ułatwić kodu.</span><span class="sxs-lookup"><span data-stu-id="a4c11-122"> provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="a4c11-123">Lista tych [stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="a4c11-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c11-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4c11-124">See Also</span></span>  
 [<span data-ttu-id="a4c11-125">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="a4c11-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="a4c11-126">Porady: odwołuje się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a4c11-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="a4c11-127">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="a4c11-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="a4c11-128">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4c11-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="a4c11-129">Porady: Określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a4c11-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="a4c11-130">Enum — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a4c11-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="a4c11-131">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a4c11-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
