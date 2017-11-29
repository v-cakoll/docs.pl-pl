---
title: "Tworzenie i wdrażanie interfejsów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08bf6dc7344d4f83c8ab1908fdeb29eb4a53e142
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="33410-102">Wskazówki: tworzenie i wdrażanie interfejsów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33410-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>
<span data-ttu-id="33410-103">Interfejsy opisują cechy właściwości, metod i zdarzeń, ale pozostawić szczegóły implementacji do struktury lub klasy.</span><span class="sxs-lookup"><span data-stu-id="33410-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="33410-104">W tym przewodniku pokazano, jak deklarowanie i implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="33410-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33410-105">Ten przewodnik nie dostarcza informacji na temat sposobu tworzenia interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="33410-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-an-interface"></a><span data-ttu-id="33410-106">Aby zdefiniować — interfejs</span><span class="sxs-lookup"><span data-stu-id="33410-106">To define an interface</span></span>  
  
1.  <span data-ttu-id="33410-107">Otwórz nowe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projekt aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="33410-107">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="33410-108">Dodaj nowy moduł do projektu, klikając **Dodawanie modułu** na **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="33410-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="33410-109">Nazwa nowego modułu `Module1.vb` i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="33410-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="33410-110">Zostanie wyświetlony kod nowy moduł.</span><span class="sxs-lookup"><span data-stu-id="33410-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="33410-111">Zdefiniuj interfejs o nazwie `TestInterface` w `Module1` , wpisując `Interface TestInterface` między `Module` i `End Module` instrukcje, a następnie naciskając klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="33410-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="33410-112">**Edytora kodu** wcięć `Interface` — słowo kluczowe i dodaje `End Interface` instrukcji do utworzenia bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="33410-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="33410-113">Definiowanie właściwości, metody i zdarzenia dla interfejsu przez umieszczenie następujący kod między `Interface` i `End Interface` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="33410-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a><span data-ttu-id="33410-114">Implementacja</span><span class="sxs-lookup"><span data-stu-id="33410-114">Implementation</span></span>  
 <span data-ttu-id="33410-115">Można zauważyć, że składnia użyć do zadeklarowania elementy członkowskie interfejsu różni się od składnię wykorzystywaną do zadeklarować elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="33410-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="33410-116">Ta różnica odzwierciedla fakt, że interfejsy nie mogą zawierać kod implementacji.</span><span class="sxs-lookup"><span data-stu-id="33410-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
#### <a name="to-implement-the-interface"></a><span data-ttu-id="33410-117">Aby zaimplementować interfejs</span><span class="sxs-lookup"><span data-stu-id="33410-117">To implement the interface</span></span>  
  
1.  <span data-ttu-id="33410-118">Dodaj klasę o nazwie `ImplementationClass` przez dodanie następujących instrukcji `Module1`, po `End Interface` instrukcji ale przed wysłaniem `End Module` instrukcji, a następnie naciskając klawisz ENTER:</span><span class="sxs-lookup"><span data-stu-id="33410-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     <span data-ttu-id="33410-119">Jeśli pracujesz w zintegrowane środowisko programistyczne, **edytora kodu** dostarcza odpowiadającego mu `End Class` instrukcji po naciśnięciu klawisza ENTER.</span><span class="sxs-lookup"><span data-stu-id="33410-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="33410-120">Dodaj następujące `Implements` instrukcji `ImplementationClass`, które nazwy interfejsu klasy implementuje:</span><span class="sxs-lookup"><span data-stu-id="33410-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     <span data-ttu-id="33410-121">Gdy przedstawione oddzielnie od innych elementów u góry klasy lub struktury, `Implements` instrukcji wskazuje, że klasy lub struktury implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="33410-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="33410-122">Jeśli pracujesz w zintegrowane środowisko programistyczne, **edytora kodu** implementuje wymagane przez członków klasy `TestInterface` po naciśnięciu klawisza ENTER i następny krok można pominąć.</span><span class="sxs-lookup"><span data-stu-id="33410-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="33410-123">Jeśli nie działają w ramach zintegrowane środowisko programistyczne, musi implementować członków interfejsu `MyInterface`.</span><span class="sxs-lookup"><span data-stu-id="33410-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="33410-124">Dodaj następujący kod do `ImplementationClass` do zaimplementowania `Event1`, `Method1`, i `Prop1`:</span><span class="sxs-lookup"><span data-stu-id="33410-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     <span data-ttu-id="33410-125">`Implements` Instrukcji nazwy interfejsu i elementu członkowskiego interfejsu implementowana.</span><span class="sxs-lookup"><span data-stu-id="33410-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="33410-126">Definicja ukończenia `Prop1` przez dodanie pola prywatne do przechowywania wartości właściwości klasy:</span><span class="sxs-lookup"><span data-stu-id="33410-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     <span data-ttu-id="33410-127">Zwraca wartość `pval` z właściwości metoda dostępu get.</span><span class="sxs-lookup"><span data-stu-id="33410-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     <span data-ttu-id="33410-128">Ustaw wartość `pval` we właściwości akcesor zestawu.</span><span class="sxs-lookup"><span data-stu-id="33410-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  <span data-ttu-id="33410-129">Definicja ukończenia `Method1` przez dodanie poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="33410-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="33410-130">Aby przetestować implementacja interfejsu</span><span class="sxs-lookup"><span data-stu-id="33410-130">To test the implementation of the interface</span></span>  
  
1.  <span data-ttu-id="33410-131">Kliknij prawym przyciskiem myszy formularz startowy projektu w **Eksploratora rozwiązań**i kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="33410-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="33410-132">Edytor wyświetla klasy formularza uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="33410-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="33410-133">Domyślnie nazywa się formularz startowy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="33410-133">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="33410-134">Dodaj następujące `testInstance` do `Form1` klasy:</span><span class="sxs-lookup"><span data-stu-id="33410-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     <span data-ttu-id="33410-135">Przez zadeklarowanie `testInstance` jako `WithEvents`, `Form1` klasa może obsłużyć jego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="33410-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="33410-136">Dodaj następujące obsługi zdarzeń do `Form1` klasy do obsługi zdarzenia generowane przez `testInstance`:</span><span class="sxs-lookup"><span data-stu-id="33410-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  <span data-ttu-id="33410-137">Dodaj procedurę o nazwie `Test` do `Form1` klasy do przetestowania klasa implementacji:</span><span class="sxs-lookup"><span data-stu-id="33410-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     <span data-ttu-id="33410-138">`Test` Procedura powoduje utworzenie wystąpienia klasy, która implementuje `MyInterface`, przypisuje to wystąpienie do `testInstance` pola, ustawia właściwość i uruchamia metody za pomocą interfejsu.</span><span class="sxs-lookup"><span data-stu-id="33410-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="33410-139">Dodaj kod, aby wywołać `Test` procedury z `Form1 Load` procedury uruchamiania formularza:</span><span class="sxs-lookup"><span data-stu-id="33410-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  <span data-ttu-id="33410-140">Uruchom `Test` procedury, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="33410-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="33410-141">Zostanie wyświetlony komunikat "Prop1 ustawiono 9".</span><span class="sxs-lookup"><span data-stu-id="33410-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="33410-142">Po kliknięciu przycisku OK komunikat "Parametr X metoda1 wynosi 5" są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="33410-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="33410-143">Kliknij przycisk OK, zostanie wyświetlony komunikat "zdarzenia przechwycono programu obsługi zdarzeń".</span><span class="sxs-lookup"><span data-stu-id="33410-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33410-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33410-144">See Also</span></span>  
 [<span data-ttu-id="33410-145">Implements — instrukcja</span><span class="sxs-lookup"><span data-stu-id="33410-145">Implements Statement</span></span>](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="33410-146">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="33410-146">Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [<span data-ttu-id="33410-147">Interface — instrukcja</span><span class="sxs-lookup"><span data-stu-id="33410-147">Interface Statement</span></span>](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="33410-148">Event — instrukcja</span><span class="sxs-lookup"><span data-stu-id="33410-148">Event Statement</span></span>](../../../../visual-basic/language-reference/statements/event-statement.md)
