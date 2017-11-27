---
title: Definiowanie klas (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec002e1709fa5fe31dfe7744fb91a230c32337a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="50315-102">Wskazówki: definiowanie klas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50315-102">Walkthrough: Defining Classes (Visual Basic)</span></span>
<span data-ttu-id="50315-103">W tym przewodniku pokazano, jak zdefiniować klasy, które następnie służy do tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="50315-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="50315-104">Ponadto przedstawiono sposób dodawania właściwości i metod do nowej klasy, a demonstruje sposób inicjowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="50315-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-a-class"></a><span data-ttu-id="50315-105">Aby zdefiniować klasę</span><span class="sxs-lookup"><span data-stu-id="50315-105">To define a class</span></span>  
  
1.  <span data-ttu-id="50315-106">Tworzenie projektu, klikając **nowy projekt** na **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="50315-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="50315-107">**Nowy projekt** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="50315-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="50315-108">Wybierz z listy aplikacji systemu Windows [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] szablony, aby wyświetlić nowy projekt projektu.</span><span class="sxs-lookup"><span data-stu-id="50315-108">Select Windows Application from the list of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="50315-109">Dodaj nową klasę w projekcie, klikając **Dodaj klasę** na **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="50315-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="50315-110">**Dodaj nowy element** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="50315-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="50315-111">Wybierz **klasy** szablonu.</span><span class="sxs-lookup"><span data-stu-id="50315-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="50315-112">Nazwa nowej klasy `UserNameInfo.vb`, a następnie kliknij przycisk **Dodaj** do wyświetlenia kodu dla nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="50315-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="50315-113">Można użyć [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **edytora kodu** Aby dodać klasę do uruchamiania formularza, wpisując `Class` — słowo kluczowe następuje nazwa nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="50315-113">You can use the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="50315-114">**Edytora kodu** zawiera odpowiednią `End Class` instrukcji dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="50315-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="50315-115">Zdefiniuj pole prywatne dla klasy przez dodanie poniższego kodu między `Class` i `End Class` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="50315-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     <span data-ttu-id="50315-116">Deklarowanie pole jako `Private` oznacza może być używany tylko w klasie.</span><span class="sxs-lookup"><span data-stu-id="50315-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="50315-117">Można udostępnić pola z poza klasą za pomocą modyfikatorów dostępu, takich jak `Public` które zapewniają więcej dostęp.</span><span class="sxs-lookup"><span data-stu-id="50315-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="50315-118">Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="50315-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="50315-119">Definiuje właściwości dla klasy przez dodanie poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="50315-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  <span data-ttu-id="50315-120">Zdefiniuj metodę w klasie przez dodanie poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="50315-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. <span data-ttu-id="50315-121">Zdefiniuj sparametryzowanym konstruktorze dla nowej klasy, dodając procedurę o nazwie `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="50315-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     <span data-ttu-id="50315-122">`Sub New` Konstruktor jest wywoływana automatycznie po utworzeniu obiektu, w oparciu o tę klasę.</span><span class="sxs-lookup"><span data-stu-id="50315-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="50315-123">Ten konstruktor ustawia wartość pola, zawierające nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="50315-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
### <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="50315-124">Aby utworzyć przycisk, aby przetestować klasy</span><span class="sxs-lookup"><span data-stu-id="50315-124">To create a button to test the class</span></span>  
  
1.  <span data-ttu-id="50315-125">Zmień formularz startowy do trybu projektowania, klikając prawym przyciskiem myszy jego nazwę w **Eksploratora rozwiązań** , a następnie klikając polecenie **Widok projektanta**.</span><span class="sxs-lookup"><span data-stu-id="50315-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="50315-126">Domyślnie formularz startowy projektów aplikacji systemu Windows nosi nazwę Form1.vb.</span><span class="sxs-lookup"><span data-stu-id="50315-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="50315-127">Następnie zostanie wyświetlony formularz główny.</span><span class="sxs-lookup"><span data-stu-id="50315-127">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="50315-128">Dodawanie przycisku do formularza głównego, a następnie kliknij dwukrotnie, aby wyświetlić kod `Button1_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="50315-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="50315-129">Dodaj następujący kod, aby wywołać procedurę testu:</span><span class="sxs-lookup"><span data-stu-id="50315-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a><span data-ttu-id="50315-130">Do uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="50315-130">To run your application</span></span>  
  
1.  <span data-ttu-id="50315-131">Uruchom aplikację, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="50315-131">Run your application by pressing F5.</span></span> <span data-ttu-id="50315-132">Kliknij przycisk w formularzu do wywołania tej procedury testu.</span><span class="sxs-lookup"><span data-stu-id="50315-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="50315-133">Wyświetla komunikat informujący, że w oryginalnej `UserName` jest "MOORE, DOMINIKA", ponieważ wywołana procedura `Capitalize` metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="50315-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="50315-134">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="50315-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="50315-135">`Button1 Click` Procedury zmienia wartość `UserName` właściwości i wyświetla komunikat informujący, że nowa wartość `UserName` jest "Worden, Jan".</span><span class="sxs-lookup"><span data-stu-id="50315-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50315-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50315-136">See Also</span></span>  
 [<span data-ttu-id="50315-137">Programowanie zorientowane obiektowo</span><span class="sxs-lookup"><span data-stu-id="50315-137">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)  
 [<span data-ttu-id="50315-138">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="50315-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
