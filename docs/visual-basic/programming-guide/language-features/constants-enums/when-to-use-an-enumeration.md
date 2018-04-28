---
title: Kiedy stosować wyliczanie (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ab152687f4f9e4ba6bd032ae7c1352f65af715f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="33802-102">Kiedy stosować wyliczanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33802-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="33802-103">Wyliczenia oferują prosty sposób pracy z zestawów powiązanych stałe.</span><span class="sxs-lookup"><span data-stu-id="33802-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="33802-104">Jako wyliczenia lub `Enum`, jest nazwa symboliczna dla zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="33802-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="33802-105">Wyliczenia są traktowane jako typy danych i można je utworzyć zestawy stałych do użycia z zmiennych i właściwości.</span><span class="sxs-lookup"><span data-stu-id="33802-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="33802-106">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="33802-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="33802-107">Zawsze, gdy procedura akceptuje ograniczony zestaw zmiennych, należy wziąć pod uwagę przy użyciu wyliczania.</span><span class="sxs-lookup"><span data-stu-id="33802-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="33802-108">Wyliczenia upewnij się jaśniejszy i czytelność kodu, szczególnie w przypadku, gdy są używane łatwy do rozpoznania nazwy.</span><span class="sxs-lookup"><span data-stu-id="33802-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="33802-109">Korzyści wynikające ze stosowania wyliczenia obejmują:</span><span class="sxs-lookup"><span data-stu-id="33802-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="33802-110">Zmniejsza liczbę błędów spowodowanych przez Transponowanie lub błędne liczby.</span><span class="sxs-lookup"><span data-stu-id="33802-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="33802-111">Można łatwo zmienić wartości w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="33802-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="33802-112">Powoduje, że kod czytelności, co oznacza, że jest mniej prawdopodobne, że błędy będą pełzanie do niego.</span><span class="sxs-lookup"><span data-stu-id="33802-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="33802-113">Zapewnia zgodność z nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="33802-113">Ensures forward compatibility.</span></span> <span data-ttu-id="33802-114">Z wyliczenia kod jest mniej prawdopodobne się niepowodzeniem, jeśli w przyszłości użytkownik wprowadza zmiany wartości odpowiadających nazwy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="33802-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="33802-115">Wyliczenia nazw</span><span class="sxs-lookup"><span data-stu-id="33802-115">Naming Enumerations</span></span>  
 <span data-ttu-id="33802-116">Elementy członkowskie wyliczenia używać konwencji nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="33802-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="33802-117">Gdy Visual Basic napotka nazwę elementu członkowskiego wyliczenia, wyjątek może zostać zgłoszony, jeśli inne biblioteki typu występującego w odwołaniu nie ma takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="33802-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="33802-118">Użyj unikatowy prefiks, który identyfikuje wartości z aplikacją lub składnikiem albo.</span><span class="sxs-lookup"><span data-stu-id="33802-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="33802-119">Podczas odwoływania się do elementu członkowskiego wyliczenia, musisz nazwy elementu członkowskiego o nazwie wyliczenia, czyli użyj `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="33802-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="33802-120">Aby uzyskać więcej informacji, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="33802-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="33802-121">Wstępnie zdefiniowane wyliczenia</span><span class="sxs-lookup"><span data-stu-id="33802-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="33802-122">Visual Basic zapewnia szereg wstępnie zdefiniowanych wyliczenia `FirstDayOfWeek` i `MsgBoxResult`, aby ułatwić kodu.</span><span class="sxs-lookup"><span data-stu-id="33802-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="33802-123">Lista tych [stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="33802-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33802-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33802-124">See Also</span></span>  
 [<span data-ttu-id="33802-125">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="33802-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="33802-126">Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="33802-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="33802-127">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="33802-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="33802-128">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="33802-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="33802-129">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="33802-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="33802-130">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="33802-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="33802-131">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="33802-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
