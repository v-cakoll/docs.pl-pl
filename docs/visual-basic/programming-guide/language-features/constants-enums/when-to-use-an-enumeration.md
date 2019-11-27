---
title: Kiedy stosować wyliczanie
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 5daae8d487ddfe079a54e305e59e32e8ded8f65e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353959"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="d5d4f-102">Kiedy stosować wyliczanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5d4f-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="d5d4f-103">Wyliczenia oferują łatwy sposób pracy z zestawami powiązanych stałych.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="d5d4f-104">Wyliczenie lub `Enum`, jest nazwą symboliczną zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="d5d4f-105">Wyliczenia są traktowane jako typy danych i można ich używać do tworzenia zestawów stałych do użycia ze zmiennymi i właściwościami.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="d5d4f-106">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="d5d4f-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="d5d4f-107">Za każdym razem, gdy procedura akceptuje ograniczony zestaw zmiennych, należy rozważyć użycie wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="d5d4f-108">Wyliczenia mają na celu wyraźniejszy i bardziej czytelny kod, szczególnie w przypadku używania znaczących nazw.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="d5d4f-109">Zalety korzystania z wyliczeń obejmują:</span><span class="sxs-lookup"><span data-stu-id="d5d4f-109">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="d5d4f-110">Zmniejsza liczbę błędów spowodowanych przez transpozycję lub błędne wpisanie numerów.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="d5d4f-111">Ułatwia zmianę wartości w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-111">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="d5d4f-112">Sprawia, że kod jest łatwiejszy do odczytania, co oznacza, że błędy będą w nim wypadane.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="d5d4f-113">Zapewnia zgodność dalej.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-113">Ensures forward compatibility.</span></span> <span data-ttu-id="d5d4f-114">W przypadku wyliczeń kod jest mniej prawdopodobnie niepowodzeniem, jeśli w przyszłości ktoś zmieni wartości odpowiadające nazwom członków.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="d5d4f-115">Wyliczanie nazw</span><span class="sxs-lookup"><span data-stu-id="d5d4f-115">Naming Enumerations</span></span>  
 <span data-ttu-id="d5d4f-116">Użyj konwencji nazewnictwa dla elementów członkowskich wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="d5d4f-117">Gdy Visual Basic napotka nazwę elementu członkowskiego wyliczenia, wyjątek może być zgłaszany, jeśli inne przywoływane biblioteki typów zawierają tę samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="d5d4f-118">Użyj unikatowego prefiksu, który identyfikuje wartości z aplikacji lub składnika.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="d5d4f-119">W przypadku odwoływania się do elementu członkowskiego wyliczenia należy zakwalifikować nazwę elementu członkowskiego o nazwie wyliczenia lub użyć instrukcji `Imports`.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="d5d4f-120">Aby uzyskać więcej informacji, zobacz [wyliczenia i kwalifikowanie nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="d5d4f-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="d5d4f-121">Wstępnie zdefiniowane wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d5d4f-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="d5d4f-122">Visual Basic udostępnia wiele wstępnie zdefiniowanych wyliczeń, takich jak `FirstDayOfWeek` i `MsgBoxResult`, aby ułatwić wykonywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="d5d4f-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="d5d4f-123">Aby zapoznać się z listą tych elementów [, zobacz stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="d5d4f-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d4f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5d4f-124">See also</span></span>

- [<span data-ttu-id="d5d4f-125">Instrukcje: deklarowanie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d5d4f-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="d5d4f-126">Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d5d4f-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="d5d4f-127">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="d5d4f-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="d5d4f-128">Instrukcje: Iterowanie przez Wyliczenie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5d4f-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="d5d4f-129">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d5d4f-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="d5d4f-130">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d5d4f-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="d5d4f-131">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d5d4f-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
