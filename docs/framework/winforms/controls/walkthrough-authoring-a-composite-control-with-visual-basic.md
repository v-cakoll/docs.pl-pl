---
title: 'Przewodnik: Tworzenie formantu złożonego za pomocą Visual Basic'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: e961826f4c33edf59934597734aec36ce301194e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694389"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="085a8-102">Przewodnik: Tworzenie formantu złożonego za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="085a8-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="085a8-103">Formanty złożone umożliwiają za pomocą którego niestandardowe interfejsy graficzne można tworzyć i ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="085a8-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="085a8-104">Formant złożony jest zasadniczo składnika za pomocą wizualnej reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="085a8-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="085a8-105">W efekcie może składać się z co najmniej Windows Forms formantów, składników lub bloki kodu, które mogą rozszerzyć funkcjonalność, sprawdzanie poprawności danych wejściowych użytkownika, modyfikując właściwości wyświetlania lub wykonywania innych zadań wymaganych przez autora.</span><span class="sxs-lookup"><span data-stu-id="085a8-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="085a8-106">Formanty złożone można umieścić na formularzach Windows Forms w taki sam sposób jak inne kontrolki.</span><span class="sxs-lookup"><span data-stu-id="085a8-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="085a8-107">W pierwszej części tego przewodnika, tworzenie prostego formantu złożonego o nazwie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="085a8-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="085a8-108">W drugiej części tego przewodnika, możesz rozszerzyć funkcjonalność `ctlClock` poprzez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="085a8-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="085a8-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="085a8-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="085a8-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="085a8-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="085a8-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="085a8-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="085a8-112">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="085a8-112">Creating the Project</span></span>  
 <span data-ttu-id="085a8-113">Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślną będzie poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="085a8-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="085a8-114">Aby utworzyć ctlClockLib Biblioteka kontrolek i kontrola ctlClock</span><span class="sxs-lookup"><span data-stu-id="085a8-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="085a8-115">Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="085a8-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="085a8-116">Wybierz z listy projektów języka Visual Basic, **Biblioteka formantów Windows** szablon projektu, należy wpisać `ctlClockLib` w **nazwa** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="085a8-116">From the list of Visual Basic projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="085a8-117">Nazwa projektu `ctlClockLib`, również jest domyślnie przypisane do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="085a8-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="085a8-118">Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="085a8-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="085a8-119">Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ctlClock`, możesz określić swoje `ctlClock` za pomocą składnika `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="085a8-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="085a8-120">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1.vb**, a następnie kliknij przycisk **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="085a8-120">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="085a8-121">Zmień nazwę pliku, aby `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="085a8-121">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="085a8-122">Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="085a8-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="085a8-123">Domyślnie przez kontrolki złożonej dziedziczy <xref:System.Windows.Forms.UserControl> klasy udostępnianej przez system.</span><span class="sxs-lookup"><span data-stu-id="085a8-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="085a8-124"><xref:System.Windows.Forms.UserControl> Zapewnia funkcje wymagane przez formanty złożone wszystkie klasy i implementuje standardowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="085a8-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="085a8-125">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="085a8-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="085a8-126">Dodawanie Windows kontrolek i składników do kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="085a8-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="085a8-127">Interfejs graficzny jest integralną część złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="085a8-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="085a8-128">Ten interfejs graficzny jest implementowany przez dodanie jednego lub kilku formantów Windows do powierzchni projektanta.</span><span class="sxs-lookup"><span data-stu-id="085a8-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="085a8-129">W poniższy pokaz możesz zintegrować formanty Windows złożonego formantu i napisać kod, aby zaimplementować funkcje.</span><span class="sxs-lookup"><span data-stu-id="085a8-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="085a8-130">Aby dodać etykietę i czasomierz do złożonego formantu</span><span class="sxs-lookup"><span data-stu-id="085a8-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="085a8-131">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.vb**, a następnie kliknij przycisk **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="085a8-131">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="085a8-132">W przyborniku, rozwiń węzeł **wspólnych formantów** węzłem, a następnie kliknij dwukrotnie plik **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="085a8-132">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="085a8-133">A <xref:System.Windows.Forms.Label> formantu o nazwie `Label1` zostanie dodany do formantu na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="085a8-133">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="085a8-134">W projektancie, kliknij **Label1**.</span><span class="sxs-lookup"><span data-stu-id="085a8-134">In the designer, click **Label1**.</span></span> <span data-ttu-id="085a8-135">W oknie właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="085a8-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="085a8-136">Właściwość</span><span class="sxs-lookup"><span data-stu-id="085a8-136">Property</span></span>|<span data-ttu-id="085a8-137">Zmień na</span><span class="sxs-lookup"><span data-stu-id="085a8-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="085a8-138">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="085a8-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="085a8-139">**Text**</span><span class="sxs-lookup"><span data-stu-id="085a8-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="085a8-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="085a8-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="085a8-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="085a8-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="085a8-142">W **przybornika**, rozwiń węzeł **składniki** węzłem, a następnie kliknij dwukrotnie plik **czasomierza**.</span><span class="sxs-lookup"><span data-stu-id="085a8-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="085a8-143">Ponieważ <xref:System.Windows.Forms.Timer> jest składnikiem, ma ona nie wizualnej reprezentacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="085a8-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="085a8-144">W związku z tym nie wydaje się za pomocą kontrolek na powierzchni projektowej, ale raczej w Projektancie składników (zasobnik w dolnej części powierzchni projektanta).</span><span class="sxs-lookup"><span data-stu-id="085a8-144">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="085a8-145">W Projektancie składników kliknij **Timer1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości `1000` i <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `True`.</span><span class="sxs-lookup"><span data-stu-id="085a8-145">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>  
  
     <span data-ttu-id="085a8-146"><xref:System.Windows.Forms.Timer.Interval%2A> Właściwość określa częstotliwość, z którym znaczniki składnika timer.</span><span class="sxs-lookup"><span data-stu-id="085a8-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="085a8-147">Każdorazowo `Timer1` znaczniki, uruchamia kod `Timer1_Tick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="085a8-147">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="085a8-148">Interwał reprezentuje liczbę milisekund między taktami.</span><span class="sxs-lookup"><span data-stu-id="085a8-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="085a8-149">W Projektancie składników, kliknij dwukrotnie **Timer1** można przejść do `Timer1_Tick` zdarzenie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="085a8-149">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="085a8-150">Należy zmodyfikować kod, tak aby wyglądała jak poniższy przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="085a8-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="085a8-151">Pamiętaj zmieniać modyfikatora dostępu z `Private` do `Protected`.</span><span class="sxs-lookup"><span data-stu-id="085a8-151">Be sure to change the access modifier from `Private` to `Protected`.</span></span>  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     <span data-ttu-id="085a8-152">Ten kod powoduje, że bieżący czas, który ma być wyświetlany w `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="085a8-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="085a8-153">Ponieważ interwał `Timer1` została ustawiona na `1000`, to zdarzenie wystąpi co tysięcy milisekund, w związku z tym aktualizacji bieżący czas co sekundę.</span><span class="sxs-lookup"><span data-stu-id="085a8-153">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="085a8-154">Zmodyfikuj metodę możliwym do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="085a8-154">Modify the method to be overridable.</span></span> <span data-ttu-id="085a8-155">Aby uzyskać więcej informacji zobacz sekcję "Dziedziczenie z kontrolki użytkownika" poniżej.</span><span class="sxs-lookup"><span data-stu-id="085a8-155">For more information, see the "Inheriting from a User Control" section below.</span></span>  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. <span data-ttu-id="085a8-156">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="085a8-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="085a8-157">Dodawanie właściwości do kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="085a8-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="085a8-158">Formant zegara teraz hermetyzuje <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.Timer> składnika, z których każdy swój własny zestaw właściwości związanych.</span><span class="sxs-lookup"><span data-stu-id="085a8-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="085a8-159">Gdy poszczególne właściwości tych kontrolek nie będą dostępne dla użytkowników kolejne kontrolki, można tworzyć i udostępnianie właściwości niestandardowych, pisząc odpowiednich bloków kodu.</span><span class="sxs-lookup"><span data-stu-id="085a8-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="085a8-160">W poniższej procedurze będzie dodać właściwości do formantu, który umożliwia użytkownikowi zmianę koloru tła i tekstu.</span><span class="sxs-lookup"><span data-stu-id="085a8-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="085a8-161">Aby dodać właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="085a8-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="085a8-162">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.vb**, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="085a8-162">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="085a8-163">Zostanie otwarty Edytor kodu dla formantu.</span><span class="sxs-lookup"><span data-stu-id="085a8-163">The Code Editor for your control opens.</span></span>  
  
2.  <span data-ttu-id="085a8-164">Znajdź `Public Class ctlClock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="085a8-164">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="085a8-165">Znajdujące się poniżej wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="085a8-165">Beneath it, type the following code.</span></span>  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     <span data-ttu-id="085a8-166">Te instrukcje tworzenia zmienne prywatne, które będą używane do przechowywania wartości właściwości, które masz zamiar utworzyć.</span><span class="sxs-lookup"><span data-stu-id="085a8-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="085a8-167">Wstaw następujący kod pod deklaracje zmiennych w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="085a8-167">Insert the following code beneath the variable declarations from step 2.</span></span>  
  
    ```vb  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     <span data-ttu-id="085a8-168">Poprzedzający kod wprowadza dwie właściwości niestandardowe, `ClockForeColor` i `ClockBackColor`, która jest dostępna dla kolejnych użytkowników tej kontrolki, wywołując `Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="085a8-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="085a8-169">`Get` i `Set` instrukcji zapewniać przechowywania i pobierania wartości właściwości, a także kod do implementacji funkcji odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="085a8-169">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="085a8-170">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="085a8-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="085a8-171">Testowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="085a8-171">Testing the Control</span></span>  
 <span data-ttu-id="085a8-172">Formanty nie są autonomiczne projektów; muszą one być obsługiwane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="085a8-172">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="085a8-173">Testowanie zachowania w czasie wykonywania kontroli nad i sprawdzić jego właściwości, za pomocą **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="085a8-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="085a8-174">Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="085a8-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="085a8-175">Aby przetestować formant</span><span class="sxs-lookup"><span data-stu-id="085a8-175">To test your control</span></span>  
  
1.  <span data-ttu-id="085a8-176">Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="085a8-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="085a8-177">W siatce właściwości kontener testu, wybierz `ClockBackColor` właściwości, a następnie kliknij strzałkę listy rozwijanej do wyświetlania palety kolorów.</span><span class="sxs-lookup"><span data-stu-id="085a8-177">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>  
  
3.  <span data-ttu-id="085a8-178">Wybierz kolor, klikając go.</span><span class="sxs-lookup"><span data-stu-id="085a8-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="085a8-179">Kolor tła kontrolki zmienia kolor, który wybrano.</span><span class="sxs-lookup"><span data-stu-id="085a8-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="085a8-180">Upewnij się, że za pomocą sekwencji podobnych zdarzeń `ClockForeColor` właściwości działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="085a8-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
5.  <span data-ttu-id="085a8-181">Kliknij przycisk **Zamknij** zamknąć **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="085a8-181">Click **Close** to close the **UserControl Test Container**.</span></span>  
  
     <span data-ttu-id="085a8-182">W poprzedniej sekcji i w tej sekcji, wiesz, jak można łączyć składników i formantów Windows z kodem i pakowania do dostarczają niestandardowych funkcjonalności w formie kontrolek złożonych.</span><span class="sxs-lookup"><span data-stu-id="085a8-182">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="085a8-183">Wiesz, że udostępnianie właściwości złożonej kontrolki i testowanie formantu po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="085a8-183">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="085a8-184">W następnej sekcji zostanie dowiesz się, jak skonstruować dziedziczone kontrolki złożonej za pomocą `ctlClock` jako podstawy.</span><span class="sxs-lookup"><span data-stu-id="085a8-184">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="085a8-185">Dziedziczenie z kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="085a8-185">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="085a8-186">W poprzednich sekcjach wiesz, jak połączyć kontrolki Windows, składników i kod do kontrolek złożonych wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="085a8-186">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="085a8-187">Złożonego formantu może być teraz używane jako podstawa, na którym mogą być wbudowane w innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="085a8-187">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="085a8-188">Wyprowadzanie klasy z klasy bazowej proces jest nazywany *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="085a8-188">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="085a8-189">W tej sekcji spowoduje utworzenie kontrolki złożonej o nazwie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="085a8-189">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="085a8-190">Ta kontrolka będzie pochodzić z kontrolki nadrzędnej, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="085a8-190">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="085a8-191">Jak rozszerzyć funkcjonalność `ctlClock` nadpisywania metod nadrzędnego i dodawania nowych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="085a8-191">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="085a8-192">Pierwszym krokiem w tworzeniu odziedziczoną kontrolkę jest pochodną jego obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="085a8-192">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="085a8-193">Ta akcja tworzy nowy formant, który zawiera wszystkie właściwości, metod i właściwości graficzne kontroli nadrzędnej, ale mogą również działać jako podstawa dla nowych lub zmodyfikowanych funkcja.</span><span class="sxs-lookup"><span data-stu-id="085a8-193">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="085a8-194">Aby utworzyć odziedziczoną kontrolkę</span><span class="sxs-lookup"><span data-stu-id="085a8-194">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="085a8-195">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **kontrolki użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="085a8-195">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="085a8-196">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="085a8-196">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="085a8-197">Wybierz **dziedziczone kontrolki użytkownika** szablonu.</span><span class="sxs-lookup"><span data-stu-id="085a8-197">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="085a8-198">W **nazwa** wpisz `ctlAlarmClock.vb`, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="085a8-198">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="085a8-199">**Selektor dziedziczenia** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="085a8-199">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="085a8-200">W obszarze **nazwa składnika**, kliknij dwukrotnie **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="085a8-200">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="085a8-201">W Eksploratorze rozwiązań należy przejrzeć bieżących projektów.</span><span class="sxs-lookup"><span data-stu-id="085a8-201">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="085a8-202">Plik o nazwie **ctlAlarmClock.vb** został dodany do bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="085a8-202">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="085a8-203">Dodawanie właściwości alarmów</span><span class="sxs-lookup"><span data-stu-id="085a8-203">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="085a8-204">Właściwości są dodawane do odziedziczoną kontrolkę w taki sam sposób, w których są one dodawane do kontrolek złożonych.</span><span class="sxs-lookup"><span data-stu-id="085a8-204">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="085a8-205">Teraz użyjesz Składnia deklaracji właściwości można dodać dwie właściwości do kontrolki: `AlarmTime`, której będzie przechowywana wartość daty i godziny alarmu jest wyłączona, a `AlarmSet`, który będzie wskazywać, czy ustawiono alarmu.</span><span class="sxs-lookup"><span data-stu-id="085a8-205">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="085a8-206">Aby dodać właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="085a8-206">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="085a8-207">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="085a8-207">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="085a8-208">Znajdź deklarację klasy dla formantu ctlAlarmClock, który jest wyświetlany jako `Public Class ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="085a8-208">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="085a8-209">W deklaracji klasy Wstaw następujący kod.</span><span class="sxs-lookup"><span data-stu-id="085a8-209">In the class declaration, insert the following code.</span></span>  
  
    ```vb  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="085a8-210">Dodawanie do interfejsu graficznego formantu</span><span class="sxs-lookup"><span data-stu-id="085a8-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="085a8-211">Odziedziczone kontrolki ma interfejs graficzny, która jest taka sama jak formant, który dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="085a8-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="085a8-212">Posiada on te same kontrolki składowych co kontrolki nadrzędnej, ale właściwości formantów składowych nie będzie dostępna, chyba że zostały one specjalnie ujawnione.</span><span class="sxs-lookup"><span data-stu-id="085a8-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="085a8-213">Można dodać do graficznego interfejsu dziedziczone złożonego formantu w taki sam sposób jak należy dodać do dowolnego złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="085a8-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="085a8-214">Aby kontynuować, dodając do zegar alarm wizualny interfejs, dodasz formant etykiety, który będzie flash, gdy jest podawania alarmu.</span><span class="sxs-lookup"><span data-stu-id="085a8-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="085a8-215">Aby dodać formant etykiety</span><span class="sxs-lookup"><span data-stu-id="085a8-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="085a8-216">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**i kliknij przycisk **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="085a8-216">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>  
  
     <span data-ttu-id="085a8-217">Projektant `ctlAlarmClock` otwiera się w głównym oknie.</span><span class="sxs-lookup"><span data-stu-id="085a8-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="085a8-218">Kliknij przycisk `lblDisplay` (wyświetlanie części kontrolki) i wyświetlić okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="085a8-218">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="085a8-219">Chociaż wyświetlane są wszystkie właściwości, są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="085a8-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="085a8-220">Oznacza to, że te właściwości są natywne `lblDisplay` i nie może zostać zmodyfikowany lub dostępne w oknie dialogowym właściwości.</span><span class="sxs-lookup"><span data-stu-id="085a8-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="085a8-221">Domyślnie są zawarte w kontrolki złożonej kontrolki `Private`, i ich właściwości nie są dostępne w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="085a8-221">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="085a8-222">Kolejni użytkownicy złożonej kontrolki mają mieć dostęp do jego wewnętrznych kontroli, zadeklarować je jako `Public` lub `Protected`.</span><span class="sxs-lookup"><span data-stu-id="085a8-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="085a8-223">To pozwala ustawić i zmodyfikować właściwości formantów zawartych w złożonej kontrolki przy użyciu odpowiedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="085a8-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="085a8-224">Dodaj <xref:System.Windows.Forms.Label> kontrolki złożonej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="085a8-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="085a8-225">Za pomocą myszy, przeciągnij <xref:System.Windows.Forms.Label> formantu bezpośrednio poniżej wyświetlanego pola.</span><span class="sxs-lookup"><span data-stu-id="085a8-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="085a8-226">W oknie właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="085a8-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="085a8-227">Właściwość</span><span class="sxs-lookup"><span data-stu-id="085a8-227">Property</span></span>|<span data-ttu-id="085a8-228">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="085a8-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="085a8-229">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="085a8-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="085a8-230">**Text**</span><span class="sxs-lookup"><span data-stu-id="085a8-230">**Text**</span></span>|<span data-ttu-id="085a8-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="085a8-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="085a8-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="085a8-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="085a8-233">**Widoczne**</span><span class="sxs-lookup"><span data-stu-id="085a8-233">**Visible**</span></span>|`False`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="085a8-234">Dodawanie funkcji alarmów</span><span class="sxs-lookup"><span data-stu-id="085a8-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="085a8-235">W ramach poprzednich procedur dodać właściwości i formant, który spowoduje włączenie funkcji alarmu w złożonej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="085a8-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="085a8-236">W tej procedurze należy dodać kod do porównania bieżącego czasu do czasu alarmów i, jeśli są takie same, dźwięk i flash alarmu.</span><span class="sxs-lookup"><span data-stu-id="085a8-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="085a8-237">Przez zastąpienie `Timer1_Tick` metody `ctlClock` i dodanie dodatkowego kodu do niego, zostaną rozszerzone możliwości `ctlAlarmClock` przy zachowaniu wszystkich funkcji związanych z `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="085a8-237">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="085a8-238">Aby zastąpić metodę Timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="085a8-238">To override the Timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="085a8-239">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.vb**, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="085a8-239">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="085a8-240">Znajdź `Private blnAlarmSet As Boolean` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="085a8-240">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="085a8-241">Bezpośrednio pod nim, należy dodać następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="085a8-241">Immediately beneath it, add the following statement.</span></span>  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  <span data-ttu-id="085a8-242">Znajdź `End Class` instrukcji w dolnej części strony.</span><span class="sxs-lookup"><span data-stu-id="085a8-242">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="085a8-243">Tuż przed `End Class` instrukcji, Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="085a8-243">Just before the `End Class` statement, add the following code.</span></span>  
  
    ```vb  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     <span data-ttu-id="085a8-244">Dodanie tego kodu w ramach kilku zadań.</span><span class="sxs-lookup"><span data-stu-id="085a8-244">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="085a8-245">`Overrides` Instrukcja określa, że formant Aby użyć tej metody, zamiast metody, która została odziedziczona z bazowej.</span><span class="sxs-lookup"><span data-stu-id="085a8-245">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="085a8-246">Gdy ta metoda jest wywoływana, wywołuje metodę, zastępuje ona wywołując `MyBase.Timer1_Tick` instrukcji, zapewniając wszystkich funkcji włączonych oryginalnego formantu jest przedstawiony w tym elemencie sterującym.</span><span class="sxs-lookup"><span data-stu-id="085a8-246">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="085a8-247">Następnie działa dodatkowego kodu, aby włączać funkcje alarmu.</span><span class="sxs-lookup"><span data-stu-id="085a8-247">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="085a8-248">Formant etykiety migające pojawi się alarm występuje, gdy sygnały dźwiękowe będzie Twój głos zostanie wysłuchany.</span><span class="sxs-lookup"><span data-stu-id="085a8-248">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="085a8-249">Ponieważ są zastępują program obsługi zdarzeń dziedziczone, nie należy określić to zdarzenie o `Handles` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="085a8-249">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="085a8-250">Zdarzenie jest już podłączony.</span><span class="sxs-lookup"><span data-stu-id="085a8-250">The event is already hooked up.</span></span> <span data-ttu-id="085a8-251">Wszystko, co jest zastąpienie stanowi implementację programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="085a8-251">All you are overriding is the implementation of the handler.</span></span>  
  
     <span data-ttu-id="085a8-252">Formant alarm zegara jest niemal ukończone.</span><span class="sxs-lookup"><span data-stu-id="085a8-252">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="085a8-253">Jest jedynym elementem, który pozostaje do zaimplementowania sposób, aby je wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="085a8-253">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="085a8-254">Aby to zrobić, można dodać kod `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="085a8-254">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="085a8-255">Aby wdrożyć metodę bliskie</span><span class="sxs-lookup"><span data-stu-id="085a8-255">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="085a8-256">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.vb**, a następnie kliknij przycisk **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="085a8-256">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="085a8-257">W projektancie, kliknij dwukrotnie **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="085a8-257">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="085a8-258">**Edytor kodu** otwiera `Private Sub lblAlarm_Click` wiersza.</span><span class="sxs-lookup"><span data-stu-id="085a8-258">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>  
  
3.  <span data-ttu-id="085a8-259">Zmodyfikuj tę metodę, tak, aby wyglądała jak poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="085a8-259">Modify this method so that it resembles the following code.</span></span>  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  <span data-ttu-id="085a8-260">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="085a8-260">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="085a8-261">Za pomocą odziedziczoną kontrolkę w formularzu</span><span class="sxs-lookup"><span data-stu-id="085a8-261">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="085a8-262">Można przetestować kontroli nad dziedziczone przetestowane kontrolki klasy bazowej, tak samo `ctlClock`: Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="085a8-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="085a8-263">Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="085a8-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="085a8-264">Aby przełączyć kontrolki do użycia, należy ją hostować na formularzu.</span><span class="sxs-lookup"><span data-stu-id="085a8-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="085a8-265">Podobnie jak w przypadku złożonego formantu standardowego dziedziczone złożonego formantu nie może występować samodzielnie i musi być hostowany w formie lub innego kontenera.</span><span class="sxs-lookup"><span data-stu-id="085a8-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="085a8-266">Ponieważ `ctlAlarmClock` ma większą głębokość funkcjonalności, dodatkowy kod jest wymagany do testowania.</span><span class="sxs-lookup"><span data-stu-id="085a8-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="085a8-267">W tej procedurze, jak napisać prosty program, aby przetestować działanie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="085a8-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="085a8-268">Możesz napisać kod, aby ustawić i wyświetlić `AlarmTime` właściwość `ctlAlarmClock`i przetestujesz jej nieodłączne funkcji.</span><span class="sxs-lookup"><span data-stu-id="085a8-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="085a8-269">Tworzenie i dodawanie formantu do formularza testu</span><span class="sxs-lookup"><span data-stu-id="085a8-269">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="085a8-270">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="085a8-270">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="085a8-271">Na **pliku** menu wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="085a8-271">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="085a8-272">Dodaj nową **aplikacji Windows** projektu do rozwiązania i nadaj mu nazwę `Test`.</span><span class="sxs-lookup"><span data-stu-id="085a8-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
     <span data-ttu-id="085a8-273">**Testu** projekt jest dodawany do Eksploratora rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="085a8-273">The **Test** project is added to Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="085a8-274">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `Test` węzła projektu, a następnie kliknij przycisk **Dodaj odwołanie** do wyświetlenia **Dodaj odwołanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="085a8-274">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="085a8-275">Kliknij kartę **projektów**.</span><span class="sxs-lookup"><span data-stu-id="085a8-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="085a8-276">Projekt **ctlClockLib** zostaną wyświetlone w obszarze **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="085a8-276">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="085a8-277">Kliknij dwukrotnie **ctlClockLib** można dodać odwołania do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="085a8-277">Double-click **ctlClockLib** to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="085a8-278">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="085a8-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
7.  <span data-ttu-id="085a8-279">W **przybornika**, rozwiń węzeł **ctlClockLib składniki** węzła.</span><span class="sxs-lookup"><span data-stu-id="085a8-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
8.  <span data-ttu-id="085a8-280">Kliknij dwukrotnie **ctlAlarmClock** można dodać wystąpienia `ctlAlarmClock` do formularza.</span><span class="sxs-lookup"><span data-stu-id="085a8-280">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>  
  
9. <span data-ttu-id="085a8-281">W **przybornika**, zlokalizuj i kliknij dwukrotnie **DateTimePicker** dodać <xref:System.Windows.Forms.DateTimePicker> sterowania do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> kontroli przez dwukrotne kliknięcie **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="085a8-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
10. <span data-ttu-id="085a8-282">Umieść formanty w wygodne miejsce w formularzu za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="085a8-282">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
11. <span data-ttu-id="085a8-283">Ustaw właściwości tych kontrolek, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="085a8-283">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="085a8-284">Formant</span><span class="sxs-lookup"><span data-stu-id="085a8-284">Control</span></span>|<span data-ttu-id="085a8-285">Właściwość</span><span class="sxs-lookup"><span data-stu-id="085a8-285">Property</span></span>|<span data-ttu-id="085a8-286">Wartość</span><span class="sxs-lookup"><span data-stu-id="085a8-286">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="085a8-287">**Text**</span><span class="sxs-lookup"><span data-stu-id="085a8-287">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="085a8-288">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="085a8-288">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="085a8-289">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="085a8-289">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="085a8-290">**Format**</span><span class="sxs-lookup"><span data-stu-id="085a8-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. <span data-ttu-id="085a8-291">W projektancie, kliknij dwukrotnie **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="085a8-291">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="085a8-292">**Edytor kodu** otwiera `Private Sub dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="085a8-292">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>  
  
13. <span data-ttu-id="085a8-293">Zmodyfikuj kod, dzięki czemu jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="085a8-293">Modify the code so that it resembles the following.</span></span>  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. <span data-ttu-id="085a8-294">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="085a8-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
15. <span data-ttu-id="085a8-295">Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="085a8-295">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="085a8-296">Zostanie uruchomiony test program.</span><span class="sxs-lookup"><span data-stu-id="085a8-296">The test program starts.</span></span> <span data-ttu-id="085a8-297">Należy pamiętać, że bieżący czas jest aktualizowana w `ctlAlarmClock` kontroli i że godzina rozpoczęcia jest wyświetlany w <xref:System.Windows.Forms.DateTimePicker> kontroli.</span><span class="sxs-lookup"><span data-stu-id="085a8-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
16. <span data-ttu-id="085a8-298">Kliknij przycisk <xref:System.Windows.Forms.DateTimePicker> gdzie minuty godziny są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="085a8-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
17. <span data-ttu-id="085a8-299">Za pomocą klawiatury, ustaw wartość minut, która jest większa niż bieżąca godzina wyświetlane według jedną minutę `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="085a8-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="085a8-300">Czas ustawienie alarmu jest wyświetlany w `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="085a8-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="085a8-301">Poczekaj, aż wyświetlonym czasie osiągnąć czas ustawienie alarmu.</span><span class="sxs-lookup"><span data-stu-id="085a8-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="085a8-302">Po wyświetlonym czasie osiągnie czas, w którym ustawiono alarmu, dźwięku dźwiękowe i `lblAlarm` będzie flash.</span><span class="sxs-lookup"><span data-stu-id="085a8-302">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>  
  
18. <span data-ttu-id="085a8-303">Wyłączyć alarm, klikając `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="085a8-303">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="085a8-304">Może teraz zresetować alarmu.</span><span class="sxs-lookup"><span data-stu-id="085a8-304">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="085a8-305">W tym przewodniku ma obejmujący wiele kluczowych założeń.</span><span class="sxs-lookup"><span data-stu-id="085a8-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="085a8-306">Wiesz, że tworzenie formantu złożonego, łącząc w kontenerze kontrolek złożonych kontrolek i składników.</span><span class="sxs-lookup"><span data-stu-id="085a8-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="085a8-307">Wiesz, można dodać właściwości do kontrolki, a następnie napisać kod do implementacji funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="085a8-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="085a8-308">W ostatniej sekcji pokazano, aby rozszerzyć funkcjonalność danej kontrolki złożonej za pomocą dziedziczenia i zmieniać funkcje metod hosta przez zastąpienie tych metod.</span><span class="sxs-lookup"><span data-stu-id="085a8-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="085a8-309">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="085a8-309">See also</span></span>
- [<span data-ttu-id="085a8-310">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="085a8-310">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
- [<span data-ttu-id="085a8-311">Instrukcje: Formanty złożone autora</span><span class="sxs-lookup"><span data-stu-id="085a8-311">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)
- [<span data-ttu-id="085a8-312">Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="085a8-312">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="085a8-313">Tworzenie składników — wskazówki</span><span class="sxs-lookup"><span data-stu-id="085a8-313">Component Authoring Walkthroughs</span></span>](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
