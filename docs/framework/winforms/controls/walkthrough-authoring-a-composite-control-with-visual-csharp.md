---
title: 'Wskazówki: tworzenie formantu złożonego za pomocą Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 1c669860b545150e75777b8c8cc434f47675ec5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="56c29-102">Wskazówki: tworzenie formantu złożonego za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="56c29-102">Walkthrough: Authoring a Composite Control with Visual C#</span></span> #
<span data-ttu-id="56c29-103">Formanty złożone umożliwiają za pomocą którego niestandardowych interfejsów graficznego można tworzyć i użyć ponownie.</span><span class="sxs-lookup"><span data-stu-id="56c29-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="56c29-104">Formantu złożonego jest zasadniczo składnik o wizualnej reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="56c29-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="56c29-105">W efekcie może składać się z co najmniej jeden program Windows Forms kontrolki, składniki lub bloki kodu, które mogą rozszerzyć funkcjonalność, sprawdzanie poprawności danych wejściowych użytkownika, modyfikując właściwości ekranu lub wykonywania innych zadań wymaganych przez autora.</span><span class="sxs-lookup"><span data-stu-id="56c29-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="56c29-106">Formanty złożone można umieścić w formularzach systemu Windows w taki sam sposób jak inne formanty.</span><span class="sxs-lookup"><span data-stu-id="56c29-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="56c29-107">W pierwszej części tego przewodnika, tworzenie prostego formantu złożonego o nazwie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="56c29-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="56c29-108">W drugiej części tego przewodnika, można rozszerzyć funkcjonalność `ctlClock` przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="56c29-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56c29-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="56c29-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="56c29-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="56c29-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="56c29-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="56c29-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="56c29-112">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="56c29-112">Creating the Project</span></span>  
 <span data-ttu-id="56c29-113">Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślna będzie poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="56c29-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="56c29-114">Aby utworzyć biblioteki formantu ctlClockLib i kontroli ctlClock</span><span class="sxs-lookup"><span data-stu-id="56c29-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="56c29-115">Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="56c29-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="56c29-116">Wybierz z listy projektów Visual C#, **Biblioteka formantów formularzy systemu Windows** szablon projektu, typ `ctlClockLib` w **nazwa** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="56c29-116">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="56c29-117">Nazwa projektu `ctlClockLib`, jest również przypisany do głównej przestrzeni nazw domyślnie.</span><span class="sxs-lookup"><span data-stu-id="56c29-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="56c29-118">Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="56c29-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="56c29-119">Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ctlClock`, można określić użytkownika `ctlClock` za pomocą składnika `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="56c29-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="56c29-120">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1.cs**, a następnie kliknij przycisk **zmienić**.</span><span class="sxs-lookup"><span data-stu-id="56c29-120">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="56c29-121">Zmień nazwę pliku, aby `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="56c29-121">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="56c29-122">Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="56c29-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56c29-123">Domyślnie formantu złożonego dziedziczy <xref:System.Windows.Forms.UserControl> klasy obsługiwanych przez system.</span><span class="sxs-lookup"><span data-stu-id="56c29-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="56c29-124"><xref:System.Windows.Forms.UserControl> Klasa udostępnia funkcje wymagane przez formanty wszystkie złożone i implementuje standardowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="56c29-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="56c29-125">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="56c29-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="56c29-126">Dodawanie Windows formanty i składniki do złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="56c29-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="56c29-127">Wizualny interfejs jest integralną część złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="56c29-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="56c29-128">Ten interfejs visual jest implementowany przez dodanie jednego lub kilku formantów systemu Windows na powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="56c29-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="56c29-129">W następujących wykazanie możesz dołączyć formantów systemu Windows do formantu złożonego i napisać kod do implementacji funkcji.</span><span class="sxs-lookup"><span data-stu-id="56c29-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="56c29-130">Aby dodać etykietę i czasomierz do formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="56c29-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="56c29-131">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij przycisk **Widok projektanta**.</span><span class="sxs-lookup"><span data-stu-id="56c29-131">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="56c29-132">W **przybornika**, rozwiń węzeł **formanty standardowe** węzeł, a następnie kliknij dwukrotnie plik **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="56c29-132">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="56c29-133">A <xref:System.Windows.Forms.Label> formantu o nazwie `label1` zostanie dodany do formantu na powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="56c29-133">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="56c29-134">W projektancie, kliknij **label1**.</span><span class="sxs-lookup"><span data-stu-id="56c29-134">In the designer, click **label1**.</span></span> <span data-ttu-id="56c29-135">W oknie właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="56c29-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="56c29-136">Właściwość</span><span class="sxs-lookup"><span data-stu-id="56c29-136">Property</span></span>|<span data-ttu-id="56c29-137">Zmień na</span><span class="sxs-lookup"><span data-stu-id="56c29-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="56c29-138">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="56c29-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="56c29-139">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="56c29-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="56c29-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="56c29-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="56c29-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="56c29-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="56c29-142">W **przybornika**, rozwiń węzeł **składniki** węzeł, a następnie kliknij dwukrotnie plik **czasomierza**.</span><span class="sxs-lookup"><span data-stu-id="56c29-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="56c29-143">Ponieważ <xref:System.Windows.Forms.Timer> to składnik go nie ma reprezentacji wizualnej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="56c29-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="56c29-144">W związku z tym nie ma z formantami na powierzchni projektanta, ale raczej w **projektanta składników** (pasku w dolnej części powierzchni projektanta).</span><span class="sxs-lookup"><span data-stu-id="56c29-144">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="56c29-145">W **projektanta składników**, kliknij przycisk **czasomierz 1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości `1000` i <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="56c29-145">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="56c29-146"><xref:System.Windows.Forms.Timer.Interval%2A> Właściwość kontroluje częstotliwość <xref:System.Windows.Forms.Timer> Takty składnika.</span><span class="sxs-lookup"><span data-stu-id="56c29-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="56c29-147">Zawsze `timer1` znaczniki, go uruchamia kod w `timer1_Tick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="56c29-147">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="56c29-148">Interwał reprezentuje liczbę milisekund między taktami.</span><span class="sxs-lookup"><span data-stu-id="56c29-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="56c29-149">W **projektanta składników**, kliknij dwukrotnie **czasomierz 1** można przejść do `timer1_Tick` zdarzenia dla `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="56c29-149">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="56c29-150">Zmodyfikuj kod, aby go podobny Poniższy przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="56c29-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="56c29-151">Należy zmienić modyfikator dostępu z `private` do `protected`.</span><span class="sxs-lookup"><span data-stu-id="56c29-151">Be sure to change the access modifier from `private` to `protected`.</span></span>  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     <span data-ttu-id="56c29-152">Ten kod spowoduje, że bieżący czas, który będzie wyświetlany w `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="56c29-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="56c29-153">Ponieważ interwał `timer1` ustawiono `1000`, to zdarzenie wystąpi co tysięcy milisekund, w związku z tym aktualizowanie bieżący czas ciągu sekundy.</span><span class="sxs-lookup"><span data-stu-id="56c29-153">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="56c29-154">Zmodyfikuj metodę, aby żaden z `virtual` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="56c29-154">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="56c29-155">Aby uzyskać więcej informacji zobacz sekcję "Dziedziczy z kontrolki użytkownika" poniżej.</span><span class="sxs-lookup"><span data-stu-id="56c29-155">For more information, see the  "Inheriting from a User Control" section below.</span></span>  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. <span data-ttu-id="56c29-156">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="56c29-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="56c29-157">Dodawanie właściwości do złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="56c29-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="56c29-158">Teraz hermetyzuje formantu zegara <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.Timer> z zestawem właściwości związanego z używaniem składnika.</span><span class="sxs-lookup"><span data-stu-id="56c29-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="56c29-159">Podczas poszczególnych właściwości tych kontrolek nie będzie dostępna dla kolejnych użytkowników formantu, można tworzyć i ujawnia właściwości niestandardowe pisząc odpowiednie bloki kodu.</span><span class="sxs-lookup"><span data-stu-id="56c29-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="56c29-160">W poniższej procedurze właściwości doda do formantu, który umożliwia użytkownikowi zmianę koloru tła i tekstu.</span><span class="sxs-lookup"><span data-stu-id="56c29-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="56c29-161">Aby dodać właściwość do formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="56c29-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="56c29-162">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="56c29-162">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="56c29-163">**Edytora kodu** dla formantu zostanie otwarty.</span><span class="sxs-lookup"><span data-stu-id="56c29-163">The **Code Editor** for your control opens.</span></span>  
  
2.  <span data-ttu-id="56c29-164">Zlokalizuj `public partial class ctlClock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56c29-164">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="56c29-165">Poniżej nawiasu otwierającego (`{)`, wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="56c29-165">Beneath the opening brace (`{)`, type the following code.</span></span>  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     <span data-ttu-id="56c29-166">Te instrukcje tworzenia zmiennych prywatnych, które będzie używany do przechowywania wartości właściwości, które zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="56c29-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="56c29-167">Wpisz następujący kod pod deklaracje zmiennej w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="56c29-167">Type the following code beneath the variable declarations from step 2.</span></span>  
  
    ```csharp  
    // Declares the name and type of the property.  
    public Color ClockBackColor  
    {  
        // Retrieves the value of the private variable colBColor.  
        get  
        {  
            return colBColor;  
        }  
        // Stores the selected value in the private variable colBColor, and   
        // updates the background color of the label control lblDisplay.  
        set  
        {  
            colBColor = value;  
            lblDisplay.BackColor = colBColor;     
        }  
    }  
    // Provides a similar set of instructions for the foreground color.  
    public Color ClockForeColor  
    {  
        get  
        {  
            return colFColor;  
        }  
        set  
        {  
            colFColor = value;  
            lblDisplay.ForeColor = colFColor;  
        }  
    }  
    ```  
  
     <span data-ttu-id="56c29-168">Poprzedni kod sprawia, że dwie właściwości niestandardowej, `ClockForeColor` i `ClockBackColor`, dostępne dla użytkowników kolejnych tego formantu.</span><span class="sxs-lookup"><span data-stu-id="56c29-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="56c29-169">`get` i `set` zapewniają instrukcje dla magazynu i pobierania wartości właściwości, a także kod do implementowania odpowiednie właściwości.</span><span class="sxs-lookup"><span data-stu-id="56c29-169">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="56c29-170">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="56c29-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="56c29-171">Testowanie formantu</span><span class="sxs-lookup"><span data-stu-id="56c29-171">Testing the Control</span></span>  
 <span data-ttu-id="56c29-172">Formanty nie są aplikacje autonomiczne; muszą one być obsługiwane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="56c29-172">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="56c29-173">Testowanie zachowania w czasie wykonywania formantu i wykonywania jej właściwości z **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="56c29-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="56c29-174">Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="56c29-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="56c29-175">Aby przetestować formantu</span><span class="sxs-lookup"><span data-stu-id="56c29-175">To test your control</span></span>  
  
1.  <span data-ttu-id="56c29-176">Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="56c29-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="56c29-177">Kontener testu siatki właściwości, odszukaj `ClockBackColor` właściwości, a następnie wybierz właściwość do wyświetlenia paletę kolorów.</span><span class="sxs-lookup"><span data-stu-id="56c29-177">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>  
  
3.  <span data-ttu-id="56c29-178">Wybierz kolor, klikając go.</span><span class="sxs-lookup"><span data-stu-id="56c29-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="56c29-179">Kolor wybranego zmienia kolor tła formantu.</span><span class="sxs-lookup"><span data-stu-id="56c29-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="56c29-180">Sprawdź, czy za pomocą sekwencji podobnych zdarzeń `ClockForeColor` właściwości działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="56c29-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
     <span data-ttu-id="56c29-181">W tej sekcji i poprzednich sekcjach, już wspomniano, jak można łączyć składników i formantów systemu Windows z kodem i pakowania umożliwiają korzystanie z funkcji niestandardowych w formie formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="56c29-181">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="56c29-182">Wiesz już ujawnić właściwości formantu złożonego i testowanie formantu po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="56c29-182">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="56c29-183">W następnej sekcji dowiesz sposób tworzenia dziedziczonych formantu złożonego za pomocą `ctlClock` jako podstawy.</span><span class="sxs-lookup"><span data-stu-id="56c29-183">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="56c29-184">Dziedziczenie z formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="56c29-184">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="56c29-185">W poprzednich sekcjach przedstawiono sposób łączenia formantów systemu Windows, składników i kodu w wielokrotnego użytku formanty złożone.</span><span class="sxs-lookup"><span data-stu-id="56c29-185">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="56c29-186">Można teraz używać formantu złożonego jako podstawa, na których mogą być tworzone na inne formanty.</span><span class="sxs-lookup"><span data-stu-id="56c29-186">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="56c29-187">Wyprowadzanie klasy z klasy podstawowej proces jest nazywany *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="56c29-187">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="56c29-188">W tej sekcji utworzysz formantu złożonego o nazwie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="56c29-188">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="56c29-189">Ten formant będzie pochodzić z kontrolki nadrzędnej, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="56c29-189">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="56c29-190">Dowiesz się rozszerzyć funkcjonalność `ctlClock` przez zastąpienie metody nadrzędnego i dodawanie nowych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="56c29-190">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="56c29-191">Pierwszym krokiem tworzenia dziedziczonych kontrolek jest pochodną nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="56c29-191">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="56c29-192">Ta akcja tworzy nowy formant, który zawiera wszystkie właściwości, metody i właściwości graficzne kontrolki nadrzędnej, ale mogą również działać jako podstawa dla nowych lub zmodyfikowanych funkcja.</span><span class="sxs-lookup"><span data-stu-id="56c29-192">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="56c29-193">Można utworzyć formantu dziedziczonych</span><span class="sxs-lookup"><span data-stu-id="56c29-193">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="56c29-194">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **kontrolki użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="56c29-194">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="56c29-195">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="56c29-195">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="56c29-196">Wybierz **dziedziczone kontrolki użytkownika** szablonu.</span><span class="sxs-lookup"><span data-stu-id="56c29-196">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="56c29-197">W **nazwa** wpisz `ctlAlarmClock.cs`, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="56c29-197">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="56c29-198">**Selektora dziedziczenia** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="56c29-198">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="56c29-199">W obszarze **nazwa składnika**, kliknij dwukrotnie **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="56c29-199">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="56c29-200">W Eksploratorze rozwiązań przeglądać bieżących projektów.</span><span class="sxs-lookup"><span data-stu-id="56c29-200">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56c29-201">Plik o nazwie **ctlAlarmClock.cs** został dodany do bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="56c29-201">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="56c29-202">Dodawanie właściwości alarmu</span><span class="sxs-lookup"><span data-stu-id="56c29-202">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="56c29-203">Właściwości są dodawane do formantu dziedziczone w taki sam sposób, są one dodawane do formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="56c29-203">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="56c29-204">Teraz użyje składni deklaracji właściwości można dodać dwóch właściwości do formantu: `AlarmTime`, który będzie przechowywać wartość daty i godziny alarm jest wyłączona, i `AlarmSet`, który będzie wskazywać, czy ustawiono alarm.</span><span class="sxs-lookup"><span data-stu-id="56c29-204">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="56c29-205">Aby dodać właściwości do formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="56c29-205">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="56c29-206">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="56c29-206">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="56c29-207">Zlokalizuj `public class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56c29-207">Locate the `public class` statement.</span></span> <span data-ttu-id="56c29-208">Należy pamiętać, że formant dziedziczy `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="56c29-208">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="56c29-209">Poniżej nawiasu otwierającego (`{)` instrukcji, wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="56c29-209">Beneath the opening brace (`{)` statement, type the following code.</span></span>  
  
    ```csharp  
    private DateTime dteAlarmTime;  
    private bool blnAlarmSet;  
    // These properties will be declared as public to allow future   
    // developers to access them.  
    public DateTime AlarmTime  
    {  
        get  
        {  
            return dteAlarmTime;  
        }  
        set  
        {  
            dteAlarmTime = value;  
        }  
    }  
    public bool AlarmSet  
    {  
        get  
        {  
            return blnAlarmSet;  
        }  
        set  
        {  
            blnAlarmSet = value;  
        }  
    }  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="56c29-210">Dodawanie do formantu interfejsu graficznego</span><span class="sxs-lookup"><span data-stu-id="56c29-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="56c29-211">Dziedziczony formantu ma wizualny interfejs, który jest taki sam jak formant, który dziedziczy z.</span><span class="sxs-lookup"><span data-stu-id="56c29-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="56c29-212">Posiada tego samego formanty składników jako kontrolki nadrzędnej, ale właściwości formantów składowych nie będą dostępne, chyba że zostały one specjalnie widoczne.</span><span class="sxs-lookup"><span data-stu-id="56c29-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="56c29-213">Można dodać do interfejsu graficznego dziedziczone formantu złożonego w taki sam sposób, jak z żadnym formantem złożonego.</span><span class="sxs-lookup"><span data-stu-id="56c29-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="56c29-214">Aby kontynuować, dodawanie do wizualny interfejs zegar alarmu, należy dodać formant etykiety, który będzie flash, gdy jest podawania alarm.</span><span class="sxs-lookup"><span data-stu-id="56c29-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="56c29-215">Aby dodać formantu etykiety</span><span class="sxs-lookup"><span data-stu-id="56c29-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="56c29-216">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **Widok projektanta**.</span><span class="sxs-lookup"><span data-stu-id="56c29-216">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="56c29-217">Projektant `ctlAlarmClock` w głównym oknie zostanie otwarta.</span><span class="sxs-lookup"><span data-stu-id="56c29-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="56c29-218">Kliknij przycisk Wyświetl części kontrolki i wyświetlić okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="56c29-218">Click the display portion of the control, and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56c29-219">Gdy wyświetlane są wszystkie właściwości, są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="56c29-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="56c29-220">Oznacza to, że te właściwości są macierzysty `lblDisplay` i nie można zmodyfikować lub dostępne w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="56c29-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="56c29-221">Domyślnie formantach zawartych w kontrolce złożone są `private`, i ich właściwości nie są dostępne w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="56c29-221">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56c29-222">Kolejni użytkownicy złożonego formantu do dostępu do jego kontrole wewnętrzne należy zadeklarować je jako `public` lub `protected`.</span><span class="sxs-lookup"><span data-stu-id="56c29-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="56c29-223">Umożliwi to ustawienie i modyfikowanie właściwości kontrolki zawartych w formantu złożonego za pomocą odpowiedni kod.</span><span class="sxs-lookup"><span data-stu-id="56c29-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="56c29-224">Dodaj <xref:System.Windows.Forms.Label> formantu złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="56c29-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="56c29-225">Za pomocą myszy, przeciągnij <xref:System.Windows.Forms.Label> formantu natychmiast poniżej wyświetlanego pola.</span><span class="sxs-lookup"><span data-stu-id="56c29-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="56c29-226">W oknie właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="56c29-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="56c29-227">Właściwość</span><span class="sxs-lookup"><span data-stu-id="56c29-227">Property</span></span>|<span data-ttu-id="56c29-228">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="56c29-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="56c29-229">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="56c29-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="56c29-230">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="56c29-230">**Text**</span></span>|<span data-ttu-id="56c29-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="56c29-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="56c29-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="56c29-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="56c29-233">**Widoczne**</span><span class="sxs-lookup"><span data-stu-id="56c29-233">**Visible**</span></span>|`false`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="56c29-234">Dodawanie funkcji alarmu</span><span class="sxs-lookup"><span data-stu-id="56c29-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="56c29-235">W ramach poprzednich procedur dodać właściwości i kontrolkę, która spowoduje włączenie funkcji alarm złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="56c29-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="56c29-236">W tej procedurze zostanie Dodaj kod, aby porównany bieżący czas na czas alarmu i, jeśli są one takie same na flash alarmu.</span><span class="sxs-lookup"><span data-stu-id="56c29-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="56c29-237">Przez zastąpienie `timer1_Tick` metody `ctlClock` i dodanie dodatkowego kodu do niego, zostaną rozszerzyć możliwości `ctlAlarmClock` przy zachowaniu wszystkie funkcje związane z `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="56c29-237">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="56c29-238">Aby zastąpić metodę timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="56c29-238">To override the timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="56c29-239">W **edytora kodu**, zlokalizuj `private bool blnAlarmSet;` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56c29-239">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="56c29-240">Natychmiast poniżej, dodaj następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="56c29-240">Immediately beneath it, add the following statement.</span></span>  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  <span data-ttu-id="56c29-241">W **edytora kodu**, zlokalizuj zamykający nawias klamrowy (`})` na końcu tej klasy.</span><span class="sxs-lookup"><span data-stu-id="56c29-241">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="56c29-242">Tuż przed nawiasem Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="56c29-242">Just before the brace, add the following code.</span></span>  
  
    ```csharp  
    protected override void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Calls the Timer1_Tick method of ctlClock.  
        base.timer1_Tick(sender, e);  
        // Checks to see if the alarm is set.  
        if (AlarmSet == false)  
            return;  
        else  
            // If the date, hour, and minute of the alarm time are the same as  
            // the current time, flash an alarm.   
        {  
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==   
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)  
            {  
                // Sets lblAlarmVisible to true, and changes the background color based on  
                // the value of blnColorTicker. The background color of the label   
                // will flash once per tick of the clock.  
                lblAlarm.Visible = true;  
                if (blnColorTicker == false)   
                {  
                    lblAlarm.BackColor = Color.Red;  
                    blnColorTicker = true;  
                }  
                else  
                {  
                    lblAlarm.BackColor = Color.Blue;  
                    blnColorTicker = false;  
                }  
            }  
            else  
            {  
                // Once the alarm has sounded for a minute, the label is made   
                // invisible again.  
                lblAlarm.Visible = false;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="56c29-243">Dodanie tego kodu wykonuje kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="56c29-243">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="56c29-244">`override` Instrukcji kieruje formant do użycia tej metody zamiast metody, która została odziedziczona z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="56c29-244">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="56c29-245">Gdy ta metoda jest wywoływana, wywołuje metodę zastępuje on wywołując `base.timer1_Tick` instrukcji zapewnienie, że włączone wszystkie funkcje kontroli oryginalnego jest przedstawiony w tym formancie.</span><span class="sxs-lookup"><span data-stu-id="56c29-245">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="56c29-246">Następnie uruchomieniu dodatkowy kod w celu włączać funkcje alarm.</span><span class="sxs-lookup"><span data-stu-id="56c29-246">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="56c29-247">Po wystąpieniu alarmu, zostanie wyświetlony miga formantu etykiety.</span><span class="sxs-lookup"><span data-stu-id="56c29-247">A flashing label control will appear when the alarm occurs.</span></span>  
  
     <span data-ttu-id="56c29-248">Formant alarm zegara jest niemal ukończone.</span><span class="sxs-lookup"><span data-stu-id="56c29-248">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="56c29-249">Jedyną operacją, której jest wdrożenie sposób, aby je wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="56c29-249">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="56c29-250">Aby to zrobić, można dodać kod `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="56c29-250">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="56c29-251">Aby zaimplementować metodę bliskie</span><span class="sxs-lookup"><span data-stu-id="56c29-251">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="56c29-252">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.cs**, a następnie kliknij przycisk **Widok projektanta**.</span><span class="sxs-lookup"><span data-stu-id="56c29-252">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="56c29-253">Zostanie otwarte okno projektowania.</span><span class="sxs-lookup"><span data-stu-id="56c29-253">The designer opens.</span></span>  
  
2.  <span data-ttu-id="56c29-254">Dodawanie przycisku do formantu.</span><span class="sxs-lookup"><span data-stu-id="56c29-254">Add a button to the control.</span></span> <span data-ttu-id="56c29-255">Ustaw właściwości przycisku w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="56c29-255">Set the properties of the button as follows.</span></span>  
  
    |<span data-ttu-id="56c29-256">Właściwość</span><span class="sxs-lookup"><span data-stu-id="56c29-256">Property</span></span>|<span data-ttu-id="56c29-257">Wartość</span><span class="sxs-lookup"><span data-stu-id="56c29-257">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="56c29-258">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="56c29-258">**Name**</span></span>|`btnAlarmOff`|  
    |<span data-ttu-id="56c29-259">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="56c29-259">**Text**</span></span>|<span data-ttu-id="56c29-260">**Wyłączyć Alarm**</span><span class="sxs-lookup"><span data-stu-id="56c29-260">**Disable Alarm**</span></span>|  
  
3.  <span data-ttu-id="56c29-261">W projektancie, kliknij dwukrotnie **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="56c29-261">In the designer, double-click **btnAlarmOff**.</span></span>  
  
     <span data-ttu-id="56c29-262">**Edytora kodu** otwiera `private void btnAlarmOff_Click` wiersza.</span><span class="sxs-lookup"><span data-stu-id="56c29-262">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>  
  
4.  <span data-ttu-id="56c29-263">Zmodyfikuj tę metodę, tak, aby podobny do następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="56c29-263">Modify this method so that it resembles the following code.</span></span>  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  <span data-ttu-id="56c29-264">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="56c29-264">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="56c29-265">Przy użyciu dziedziczone kontrolkę w formularzu</span><span class="sxs-lookup"><span data-stu-id="56c29-265">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="56c29-266">Można przetestować dziedziczone formantu przetestowane formantu klasy podstawowej, tak samo `ctlClock`: naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontenera testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="56c29-266">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="56c29-267">Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="56c29-267">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="56c29-268">Aby umieścić formantu do użycia, należy udostępnić go w formularzu.</span><span class="sxs-lookup"><span data-stu-id="56c29-268">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="56c29-269">Podobnie jak w przypadku złożonego formantu standardowego, dziedziczone formantu złożonego nie może występować samodzielnie i musi być hostowany w formularzu lub innych kontenera.</span><span class="sxs-lookup"><span data-stu-id="56c29-269">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="56c29-270">Ponieważ `ctlAlarmClock` głębokość większej funkcjonalności, dodatkowy kod jest wymagany do testowania go.</span><span class="sxs-lookup"><span data-stu-id="56c29-270">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="56c29-271">W tej procedurze, jak napisać prosty program, aby przetestować funkcje `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="56c29-271">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="56c29-272">Jak napisać kod, aby ustawić i wyświetlić `AlarmTime` właściwość `ctlAlarmClock`i Testuj jego związanego z używaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="56c29-272">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="56c29-273">Tworzenie i dodawanie formantu do formularza testu</span><span class="sxs-lookup"><span data-stu-id="56c29-273">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="56c29-274">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="56c29-274">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="56c29-275">Dodaj nową **aplikacji systemu Windows** projektu do rozwiązania i nadaj mu nazwę `Test`.</span><span class="sxs-lookup"><span data-stu-id="56c29-275">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
3.  <span data-ttu-id="56c29-276">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** węzła dla projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="56c29-276">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="56c29-277">Kliknij przycisk **Dodaj odwołanie** do wyświetlenia **Dodaj odwołanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="56c29-277">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="56c29-278">Kliknij kartę **projekty**.</span><span class="sxs-lookup"><span data-stu-id="56c29-278">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="56c29-279">Twoje `ctlClockLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="56c29-279">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="56c29-280">Kliknij dwukrotnie plik projektu można dodać odwołania do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="56c29-280">Double-click the project to add the reference to the test project.</span></span>  
  
4.  <span data-ttu-id="56c29-281">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="56c29-281">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="56c29-282">W **przybornika**, rozwiń węzeł **ctlClockLib składniki** węzła.</span><span class="sxs-lookup"><span data-stu-id="56c29-282">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
6.  <span data-ttu-id="56c29-283">Kliknij dwukrotnie **ctlAlarmClock** można dodać kopię `ctlAlarmClock` do formularza.</span><span class="sxs-lookup"><span data-stu-id="56c29-283">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>  
  
7.  <span data-ttu-id="56c29-284">W **przybornika**, Znajdź i kliknij dwukrotnie **DateTimePicker** można dodać <xref:System.Windows.Forms.DateTimePicker> sterowania do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> kontroli przez dwukrotne kliknięcie **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="56c29-284">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
8.  <span data-ttu-id="56c29-285">Umieść formanty w dogodnym miejscu w formularzu za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="56c29-285">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
9. <span data-ttu-id="56c29-286">Ustaw właściwości tych kontrolek w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="56c29-286">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="56c29-287">Formant</span><span class="sxs-lookup"><span data-stu-id="56c29-287">Control</span></span>|<span data-ttu-id="56c29-288">Właściwość</span><span class="sxs-lookup"><span data-stu-id="56c29-288">Property</span></span>|<span data-ttu-id="56c29-289">Wartość</span><span class="sxs-lookup"><span data-stu-id="56c29-289">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="56c29-290">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="56c29-290">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="56c29-291">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="56c29-291">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="56c29-292">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="56c29-292">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="56c29-293">**Format**</span><span class="sxs-lookup"><span data-stu-id="56c29-293">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. <span data-ttu-id="56c29-294">W projektancie, kliknij dwukrotnie **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="56c29-294">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="56c29-295">**Edytora kodu** otwiera się `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="56c29-295">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>  
  
11. <span data-ttu-id="56c29-296">Zmodyfikuj kod, dzięki czemu jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="56c29-296">Modify the code so that it resembles the following.</span></span>  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. <span data-ttu-id="56c29-297">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="56c29-297">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
13. <span data-ttu-id="56c29-298">Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="56c29-298">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="56c29-299">Uruchamia test program.</span><span class="sxs-lookup"><span data-stu-id="56c29-299">The test program starts.</span></span> <span data-ttu-id="56c29-300">Należy pamiętać, że bieżący czas jest aktualizowany w `ctlAlarmClock` kontroli i czy czas rozpoczęcia jest wyświetlany w <xref:System.Windows.Forms.DateTimePicker> formantu.</span><span class="sxs-lookup"><span data-stu-id="56c29-300">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
14. <span data-ttu-id="56c29-301">Kliknij przycisk <xref:System.Windows.Forms.DateTimePicker> gdzie minuty, godziny są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="56c29-301">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
15. <span data-ttu-id="56c29-302">Przy użyciu klawiatury, ustaw wartość minut, która jest większa niż bieżący czas systemowy przez jedną minutę `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="56c29-302">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="56c29-303">Czas w ustawieniach alarm, gdy jest wyświetlany w obszarze `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="56c29-303">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="56c29-304">Poczekaj na wyświetlonej czasu do czasu ustawienie alarmu.</span><span class="sxs-lookup"><span data-stu-id="56c29-304">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="56c29-305">Gdy czas, do którego alarm jest ustawiona, osiągnie wyświetlonym czasie `lblAlarm` będzie flash.</span><span class="sxs-lookup"><span data-stu-id="56c29-305">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>  
  
16. <span data-ttu-id="56c29-306">Wyłączyć alarm, klikając `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="56c29-306">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="56c29-307">Alarm mogą teraz zresetować.</span><span class="sxs-lookup"><span data-stu-id="56c29-307">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="56c29-308">Ten przewodnik zawiera obejmujący wiele kluczowych założeń.</span><span class="sxs-lookup"><span data-stu-id="56c29-308">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="56c29-309">Wiesz już, można utworzyć formantu złożonego przez połączenie formanty i składniki w kontenerze formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="56c29-309">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="56c29-310">Kiedy znasz już pozwala dodać właściwości do formantu i napisać kod do implementacji funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="56c29-310">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="56c29-311">W ostatniej sekcji przedstawiono mogą rozszerzyć funkcjonalność danego formantu złożonego za pomocą dziedziczenia i zmieniać funkcje metod hosta przez zastąpienie tych metod.</span><span class="sxs-lookup"><span data-stu-id="56c29-311">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c29-312">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56c29-312">See Also</span></span>  
 [<span data-ttu-id="56c29-313">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="56c29-313">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="56c29-314">Programowanie przy użyciu składników</span><span class="sxs-lookup"><span data-stu-id="56c29-314">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="56c29-315">Wskazówki dotyczące tworzenia składników</span><span class="sxs-lookup"><span data-stu-id="56c29-315">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="56c29-316">Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="56c29-316">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="56c29-317">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="56c29-317">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
