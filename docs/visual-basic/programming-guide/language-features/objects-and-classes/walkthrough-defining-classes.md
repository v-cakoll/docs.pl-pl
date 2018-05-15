---
title: Definiowanie klas (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: aac30a8b0272ae6c141138a91585953237ab8098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="898a0-102">Wskazówki: definiowanie klas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="898a0-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="898a0-103">W tym przewodniku pokazano, jak zdefiniować klasy, które następnie służy do tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="898a0-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="898a0-104">Ponadto przedstawiono sposób dodawania właściwości i metod do nowej klasy, a demonstruje sposób inicjowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="898a0-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="898a0-105">Aby zdefiniować klasę</span><span class="sxs-lookup"><span data-stu-id="898a0-105">To define a class</span></span>
  
1.  <span data-ttu-id="898a0-106">Tworzenie projektu, klikając **nowy projekt** na **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="898a0-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="898a0-107">**Nowy projekt** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="898a0-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="898a0-108">Wybierz aplikację systemu Windows na liście szablony projektu Visual Basic, aby wyświetlić nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="898a0-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="898a0-109">Dodaj nową klasę w projekcie, klikając **Dodaj klasę** na **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="898a0-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="898a0-110">**Dodaj nowy element** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="898a0-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="898a0-111">Wybierz **klasy** szablonu.</span><span class="sxs-lookup"><span data-stu-id="898a0-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="898a0-112">Nazwa nowej klasy `UserNameInfo.vb`, a następnie kliknij przycisk **Dodaj** do wyświetlenia kodu dla nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="898a0-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  <span data-ttu-id="898a0-113">Korzystając z języka Visual Basic **edytora kodu** Aby dodać klasę do uruchamiania formularza, wpisując `Class` — słowo kluczowe następuje nazwa nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="898a0-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="898a0-114">**Edytora kodu** zawiera odpowiednią `End Class` instrukcji dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="898a0-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="898a0-115">Zdefiniuj pole prywatne dla klasy przez dodanie poniższego kodu między `Class` i `End Class` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="898a0-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="898a0-116">Deklarowanie pole jako `Private` oznacza może być używany tylko w klasie.</span><span class="sxs-lookup"><span data-stu-id="898a0-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="898a0-117">Można udostępnić pola z poza klasą za pomocą modyfikatorów dostępu, takich jak `Public` które zapewniają więcej dostęp.</span><span class="sxs-lookup"><span data-stu-id="898a0-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="898a0-118">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="898a0-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="898a0-119">Definiuje właściwości dla klasy przez dodanie poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="898a0-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  <span data-ttu-id="898a0-120">Zdefiniuj metodę w klasie przez dodanie poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="898a0-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="898a0-121">Zdefiniuj sparametryzowanym konstruktorze dla nowej klasy, dodając procedurę o nazwie `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="898a0-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="898a0-122">`Sub New` Konstruktor jest wywoływana automatycznie po utworzeniu obiektu, w oparciu o tę klasę.</span><span class="sxs-lookup"><span data-stu-id="898a0-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="898a0-123">Ten konstruktor ustawia wartość pola, zawierające nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="898a0-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="898a0-124">Aby utworzyć przycisk, aby przetestować klasy</span><span class="sxs-lookup"><span data-stu-id="898a0-124">To create a button to test the class</span></span>
  
1.  <span data-ttu-id="898a0-125">Zmień formularz startowy do trybu projektowania, klikając prawym przyciskiem myszy jego nazwę w **Eksploratora rozwiązań** , a następnie klikając polecenie **Widok projektanta**.</span><span class="sxs-lookup"><span data-stu-id="898a0-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="898a0-126">Domyślnie formularz startowy projektów aplikacji systemu Windows nosi nazwę Form1.vb.</span><span class="sxs-lookup"><span data-stu-id="898a0-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="898a0-127">Następnie zostanie wyświetlony formularz główny.</span><span class="sxs-lookup"><span data-stu-id="898a0-127">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="898a0-128">Dodawanie przycisku do formularza głównego, a następnie kliknij dwukrotnie, aby wyświetlić kod `Button1_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="898a0-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="898a0-129">Dodaj następujący kod, aby wywołać procedurę testu:</span><span class="sxs-lookup"><span data-stu-id="898a0-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="898a0-130">Do uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="898a0-130">To run your application</span></span>
  
1.  <span data-ttu-id="898a0-131">Uruchom aplikację, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="898a0-131">Run your application by pressing F5.</span></span> <span data-ttu-id="898a0-132">Kliknij przycisk w formularzu do wywołania tej procedury testu.</span><span class="sxs-lookup"><span data-stu-id="898a0-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="898a0-133">Wyświetla komunikat informujący, że w oryginalnej `UserName` jest "MOORE, DOMINIKA", ponieważ wywołana procedura `Capitalize` metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="898a0-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="898a0-134">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="898a0-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="898a0-135">`Button1 Click` Procedury zmienia wartość `UserName` właściwości i wyświetla komunikat informujący, że nowa wartość `UserName` jest "Worden, Jan".</span><span class="sxs-lookup"><span data-stu-id="898a0-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="898a0-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="898a0-136">See also</span></span>

[<span data-ttu-id="898a0-137">Programowanie zorientowane obiektowo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="898a0-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
[<span data-ttu-id="898a0-138">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="898a0-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)