---
title: Kiedy stosować wyliczanie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ff2d8c324aee8bbccef050c020e5392368b05b1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825108"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="afa24-102">Kiedy stosować wyliczanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa24-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="afa24-103">Wyliczenia oferują prosty sposób pracy z zestawami pokrewnych stałych.</span><span class="sxs-lookup"><span data-stu-id="afa24-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="afa24-104">Moduł wyliczenia lub `Enum`, to Symboliczna nazwa zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="afa24-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="afa24-105">Wyliczenia są traktowane jako typy danych i umożliwia im tworzenie zestawów stałych do użycia z zmienne i ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="afa24-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="afa24-106">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="afa24-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="afa24-107">Zawsze, gdy procedura akceptuje ograniczony zestaw zmiennych, należy wziąć pod uwagę przy użyciu funkcji wyliczania.</span><span class="sxs-lookup"><span data-stu-id="afa24-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="afa24-108">Wyliczenia powodują przejrzyste i bardziej czytelny kod, szczególnie w przypadku, gdy używane są znaczące nazwy.</span><span class="sxs-lookup"><span data-stu-id="afa24-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="afa24-109">Korzyści wynikające ze stosowania wyliczeń:</span><span class="sxs-lookup"><span data-stu-id="afa24-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="afa24-110">Zmniejsza błędy spowodowane Transponowanie lub błędne liczby.</span><span class="sxs-lookup"><span data-stu-id="afa24-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="afa24-111">Można łatwo zmienić wartości w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="afa24-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="afa24-112">Sprawia, że kod łatwiejsza do odczytania, co oznacza, że jest mniej prawdopodobne, że błędy będą pełzanie tę sytuację.</span><span class="sxs-lookup"><span data-stu-id="afa24-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="afa24-113">Zapewnia zgodność z nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="afa24-113">Ensures forward compatibility.</span></span> <span data-ttu-id="afa24-114">Z wyliczeniami kod jest mniej prawdopodobne zakończyć się niepowodzeniem, jeśli w przyszłości ktoś zmienia wartości odpowiadające nazwy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="afa24-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="afa24-115">Nazwy wyliczeń</span><span class="sxs-lookup"><span data-stu-id="afa24-115">Naming Enumerations</span></span>  
 <span data-ttu-id="afa24-116">Używa konwencji nazewnictwa dla elementów członkowskich wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="afa24-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="afa24-117">Gdy Visual Basic napotyka nazwa składowej wyliczenia, może zgłoszony wyjątek, jeśli inne biblioteki typów w przywoływanych zawierać taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="afa24-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="afa24-118">Użyj unikatowy prefiks, który identyfikuje wartości z aplikacji lub składnika.</span><span class="sxs-lookup"><span data-stu-id="afa24-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="afa24-119">Przy odwoływaniu się do elementu członkowskiego wyliczenia, musisz kwalifikowania nazwy elementu członkowskiego o nazwie wyliczenie, czyli użyj `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="afa24-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="afa24-120">Aby uzyskać więcej informacji, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="afa24-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="afa24-121">Wstępnie zdefiniowane wyliczenia</span><span class="sxs-lookup"><span data-stu-id="afa24-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="afa24-122">Visual Basic zawiera szereg wstępnie zdefiniowanych wyliczenia, takich jak `FirstDayOfWeek` i `MsgBoxResult`, aby ułatwić swój kod.</span><span class="sxs-lookup"><span data-stu-id="afa24-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="afa24-123">Aby uzyskać listę tych zobacz [stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="afa24-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa24-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afa24-124">See also</span></span>

- [<span data-ttu-id="afa24-125">Instrukcje: Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="afa24-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="afa24-126">Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="afa24-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="afa24-127">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="afa24-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="afa24-128">Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="afa24-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="afa24-129">Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="afa24-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="afa24-130">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="afa24-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="afa24-131">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="afa24-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
