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
ms.openlocfilehash: c41d3b2c8d905395f1249b15709da8dbdf5d4632
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640436"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="b5649-102">Przewodnik: Definiowanie klas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5649-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="b5649-103">W tym instruktażu przedstawiono sposób definiowania klas, które można następnie wykorzystać do tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="b5649-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="b5649-104">Ponadto dowiesz się, jak dodać właściwości i metod do nowej klasy i pokazuje, jak można zainicjować obiektu.</span><span class="sxs-lookup"><span data-stu-id="b5649-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="b5649-105">Aby zdefiniować klasę</span><span class="sxs-lookup"><span data-stu-id="b5649-105">To define a class</span></span>
  
1.  <span data-ttu-id="b5649-106">Utwórz projekt, klikając **nowy projekt** na **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="b5649-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="b5649-107">**Nowy projekt** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b5649-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="b5649-108">Wybierz aplikację Windows z listy szablonów projektu języka Visual Basic, aby wyświetlić nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="b5649-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="b5649-109">Dodaj nową klasę do projektu, klikając pozycję **Dodaj klasę** na **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="b5649-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="b5649-110">**Dodaj nowy element** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b5649-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="b5649-111">Wybierz **klasy** szablonu.</span><span class="sxs-lookup"><span data-stu-id="b5649-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="b5649-112">Nadaj nowej klasie `UserNameInfo.vb`, a następnie kliknij przycisk **Dodaj** Aby wyświetlić kod dla nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="b5649-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  <span data-ttu-id="b5649-113">Visual Basic można użyć **Edytor kodu** Aby dodać klasę do formularza uruchamiania, wpisując `Class` następuje nazwa nowej klasy, słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="b5649-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="b5649-114">**Edytor kodu** zapewnia odpowiedni `End Class` instrukcji dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="b5649-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="b5649-115">Zdefiniuj prywatnego pola do klasy, dodając następujący kod między `Class` i `End Class` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="b5649-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="b5649-116">Deklarowanie pola jako `Private` oznacza może być używany tylko w klasie.</span><span class="sxs-lookup"><span data-stu-id="b5649-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="b5649-117">Możesz udostępnić pola z poza klasy za pomocą modyfikatorów dostępu, takich jak `Public` dostarczające większy dostęp.</span><span class="sxs-lookup"><span data-stu-id="b5649-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="b5649-118">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b5649-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="b5649-119">Zdefiniuj właściwość klasy, dodając następujący kod:</span><span class="sxs-lookup"><span data-stu-id="b5649-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  <span data-ttu-id="b5649-120">Zdefiniuj metodę dla klasy, dodając następujący kod:</span><span class="sxs-lookup"><span data-stu-id="b5649-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="b5649-121">Zdefiniuj sparametryzowania konstruktora dla nowej klasy, dodając procedurę o nazwie `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="b5649-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="b5649-122">`Sub New` Konstruktor jest wywoływana automatycznie, gdy tworzony jest obiekt na podstawie tej klasy.</span><span class="sxs-lookup"><span data-stu-id="b5649-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="b5649-123">Ten konstruktor określa wartości pola, który zawiera nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b5649-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="b5649-124">Aby utworzyć przycisk do przetestowania klasy</span><span class="sxs-lookup"><span data-stu-id="b5649-124">To create a button to test the class</span></span>
  
1.  <span data-ttu-id="b5649-125">Zmień formularz początkowy do trybu projektowania, klikając prawym przyciskiem myszy jej nazwę w **Eksploratora rozwiązań** , a następnie klikając polecenie **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="b5649-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="b5649-126">Domyślnie formularz początkowy dla projektów aplikacji Windows nazwie Form1.vb.</span><span class="sxs-lookup"><span data-stu-id="b5649-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="b5649-127">Następnie zostanie wyświetlony formularz główny.</span><span class="sxs-lookup"><span data-stu-id="b5649-127">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="b5649-128">Dodawanie przycisku do formularza głównego i go dwukrotnie, aby wyświetlić kod `Button1_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b5649-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="b5649-129">Dodaj następujący kod, aby wywołać procedurę testu:</span><span class="sxs-lookup"><span data-stu-id="b5649-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="b5649-130">Aby uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="b5649-130">To run your application</span></span>
  
1.  <span data-ttu-id="b5649-131">Uruchom aplikację, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="b5649-131">Run your application by pressing F5.</span></span> <span data-ttu-id="b5649-132">Kliknij przycisk na formularzu, aby wywołać procedurę testu.</span><span class="sxs-lookup"><span data-stu-id="b5649-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="b5649-133">Wyświetla komunikat informujący, że oryginalna `UserName` jest "MOORE, DOMINIKA", ponieważ wywołana procedura `Capitalize` metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="b5649-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="b5649-134">Kliknij przycisk **OK** aby odrzucić okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b5649-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="b5649-135">`Button1 Click` Procedury zmienia wartość `UserName` właściwości i wyświetla komunikat informujący, że nowa wartość `UserName` jest "Worden, Jan".</span><span class="sxs-lookup"><span data-stu-id="b5649-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5649-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5649-136">See also</span></span>

- [<span data-ttu-id="b5649-137">Programowanie zorientowane obiektowo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5649-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="b5649-138">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="b5649-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
