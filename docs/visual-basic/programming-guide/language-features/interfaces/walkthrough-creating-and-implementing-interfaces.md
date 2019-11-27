---
title: Tworzenie i implementowanie interfejsów
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 47176d2e7a512d8e8c27a90ac04d2a2a2af274b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345041"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="fde81-102">Wskazówki: tworzenie i wdrażanie interfejsów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fde81-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="fde81-103">Interfejsy opisują właściwości, metody i zdarzenia, ale pozostawiają szczegóły implementacji do struktur lub klas.</span><span class="sxs-lookup"><span data-stu-id="fde81-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="fde81-104">W tym instruktażu pokazano, jak zadeklarować i zaimplementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="fde81-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fde81-105">Ten Instruktaż nie zawiera informacji o sposobie tworzenia interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fde81-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="fde81-106">Aby zdefiniować interfejs</span><span class="sxs-lookup"><span data-stu-id="fde81-106">To define an interface</span></span>
  
1. <span data-ttu-id="fde81-107">Otwórz nowy projekt aplikacji Visual Basic systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fde81-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="fde81-108">Dodaj nowy moduł do projektu, klikając pozycję **Dodaj moduł** w menu **projekt** .</span><span class="sxs-lookup"><span data-stu-id="fde81-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="fde81-109">Nazwij nowy moduł `Module1.vb` a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="fde81-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="fde81-110">Zostanie wyświetlony kod dla nowego modułu.</span><span class="sxs-lookup"><span data-stu-id="fde81-110">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="fde81-111">Zdefiniuj interfejs o nazwie `TestInterface` w `Module1`, wpisując `Interface TestInterface` między instrukcją `Module` i `End Module`, a następnie naciskając klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="fde81-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="fde81-112">**Edytor kodu** tworzy wcięcie słowa kluczowego `Interface` i dodaje instrukcję `End Interface` w celu utworzenia bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="fde81-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="fde81-113">Zdefiniuj właściwość, metodę i zdarzenie dla interfejsu, umieszczając następujący kod między instrukcjami `Interface` i `End Interface`:</span><span class="sxs-lookup"><span data-stu-id="fde81-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="fde81-114">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="fde81-114">Implementation</span></span>

 <span data-ttu-id="fde81-115">Można zauważyć, że składnia użyta do deklarowania składowych interfejsu różni się od składni używanej do deklarowania elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="fde81-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="fde81-116">Różnica ta odzwierciedla fakt, że interfejsy nie mogą zawierać kodu implementacji.</span><span class="sxs-lookup"><span data-stu-id="fde81-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="fde81-117">Aby zaimplementować interfejs</span><span class="sxs-lookup"><span data-stu-id="fde81-117">To implement the interface</span></span>
  
1. <span data-ttu-id="fde81-118">Dodaj klasę o nazwie `ImplementationClass` przez dodanie następującej instrukcji do `Module1`, po instrukcji `End Interface`, ale przed instrukcją `End Module`, a następnie naciśnij klawisz ENTER:</span><span class="sxs-lookup"><span data-stu-id="fde81-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="fde81-119">Jeśli pracujesz w zintegrowanym środowisku programistycznym, **Edytor kodu** dostarcza pasującą instrukcję `End Class` po naciśnięciu klawisza ENTER.</span><span class="sxs-lookup"><span data-stu-id="fde81-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="fde81-120">Dodaj następującą instrukcję `Implements`, aby `ImplementationClass`, która nazywa interfejs implementujący przez klasę:</span><span class="sxs-lookup"><span data-stu-id="fde81-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="fde81-121">Gdy jest wyświetlany oddzielnie od innych elementów w górnej części klasy lub struktury, instrukcja `Implements` wskazuje, że Klasa lub struktura implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="fde81-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="fde81-122">Jeśli pracujesz w zintegrowanym środowisku programistycznym, **Edytor kodu** implementuje elementy członkowskie klasy wymagane przez `TestInterface` po naciśnięciu klawisza Enter i można pominąć następny krok.</span><span class="sxs-lookup"><span data-stu-id="fde81-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="fde81-123">Jeśli nie Pracujesz w zintegrowanym środowisku programistycznym, musisz zaimplementować wszystkie elementy członkowskie interfejsu `MyInterface`.</span><span class="sxs-lookup"><span data-stu-id="fde81-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="fde81-124">Dodaj następujący kod, aby `ImplementationClass` zaimplementować `Event1`, `Method1`i `Prop1`:</span><span class="sxs-lookup"><span data-stu-id="fde81-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="fde81-125">Instrukcja `Implements` nazywa interfejs i składową interfejsu, która jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="fde81-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="fde81-126">Wypełnij definicje `Prop1`, dodając pole private do klasy, która przechowuje wartość właściwości:</span><span class="sxs-lookup"><span data-stu-id="fde81-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="fde81-127">Zwróć wartość `pval` z metody dostępu get właściwości.</span><span class="sxs-lookup"><span data-stu-id="fde81-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="fde81-128">Ustaw wartość `pval` w metodzie dostępu do zestawu właściwości.</span><span class="sxs-lookup"><span data-stu-id="fde81-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="fde81-129">Wypełnij definicje `Method1`, dodając następujący kod.</span><span class="sxs-lookup"><span data-stu-id="fde81-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="fde81-130">Aby przetestować implementację interfejsu</span><span class="sxs-lookup"><span data-stu-id="fde81-130">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="fde81-131">Kliknij prawym przyciskiem myszy formularz startowy dla projektu w **Eksplorator rozwiązań**, a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="fde81-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="fde81-132">Edytor wyświetla klasę dla formularza startowego.</span><span class="sxs-lookup"><span data-stu-id="fde81-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="fde81-133">Domyślnie formularz startowy jest nazywany `Form1`.</span><span class="sxs-lookup"><span data-stu-id="fde81-133">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="fde81-134">Dodaj następujące pole `testInstance` do klasy `Form1`:</span><span class="sxs-lookup"><span data-stu-id="fde81-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="fde81-135">Deklarując `testInstance` jako `WithEvents`, Klasa `Form1` może obsłużyć swoje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fde81-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="fde81-136">Dodaj następującą procedurę obsługi zdarzeń do klasy `Form1`, aby obsłużyć zdarzenia zgłoszone przez `testInstance`:</span><span class="sxs-lookup"><span data-stu-id="fde81-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="fde81-137">Dodaj podprocedurę o nazwie `Test` do klasy `Form1` w celu przetestowania klasy implementacji:</span><span class="sxs-lookup"><span data-stu-id="fde81-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="fde81-138">Procedura `Test` tworzy wystąpienie klasy implementującej `MyInterface`, przypisuje to wystąpienie do pola `testInstance`, ustawia właściwość i uruchamia metodę za pomocą interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fde81-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="fde81-139">Dodaj kod, aby wywołać procedurę `Test` z procedury `Form1 Load` w formularzu startowym:</span><span class="sxs-lookup"><span data-stu-id="fde81-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="fde81-140">Uruchom procedurę `Test`, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="fde81-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="fde81-141">Zostanie wyświetlony komunikat "Prop1 został ustawiony na 9".</span><span class="sxs-lookup"><span data-stu-id="fde81-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="fde81-142">Po kliknięciu przycisku OK zostanie wyświetlony komunikat "parametr X dla Metoda1 jest 5".</span><span class="sxs-lookup"><span data-stu-id="fde81-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="fde81-143">Kliknij przycisk OK, a zostanie wyświetlony komunikat "procedura obsługi zdarzeń przechwycono zdarzenie".</span><span class="sxs-lookup"><span data-stu-id="fde81-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde81-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fde81-144">See also</span></span>

- [<span data-ttu-id="fde81-145">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fde81-145">Implements Statement</span></span>](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="fde81-146">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="fde81-146">Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="fde81-147">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fde81-147">Interface Statement</span></span>](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="fde81-148">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fde81-148">Event Statement</span></span>](../../../../visual-basic/language-reference/statements/event-statement.md)
