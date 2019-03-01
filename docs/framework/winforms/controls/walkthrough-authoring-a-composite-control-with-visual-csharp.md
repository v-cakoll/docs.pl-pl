---
title: 'Przewodnik: Tworzenie formantu złożonego za pomocą Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: a9ab771d87c3e5af4726806a262886845724cffd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977056"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="b0f16-102">Przewodnik: Tworzenie formantu złożonego za pomocą Visual C\#</span><span class="sxs-lookup"><span data-stu-id="b0f16-102">Walkthrough: Authoring a Composite Control with Visual C\#</span></span>
<span data-ttu-id="b0f16-103">Formanty złożone umożliwiają za pomocą którego niestandardowe interfejsy graficzne można tworzyć i ponownie używane.</span><span class="sxs-lookup"><span data-stu-id="b0f16-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="b0f16-104">Formant złożony jest zasadniczo składnika za pomocą wizualnej reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="b0f16-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="b0f16-105">W efekcie może składać się z co najmniej Windows Forms formantów, składników lub bloki kodu, które mogą rozszerzyć funkcjonalność, sprawdzanie poprawności danych wejściowych użytkownika, modyfikując właściwości wyświetlania lub wykonywania innych zadań wymaganych przez autora.</span><span class="sxs-lookup"><span data-stu-id="b0f16-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="b0f16-106">Formanty złożone można umieścić na formularzach Windows Forms w taki sam sposób jak inne kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b0f16-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="b0f16-107">W pierwszej części tego przewodnika, tworzenie prostego formantu złożonego o nazwie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="b0f16-108">W drugiej części tego przewodnika, możesz rozszerzyć funkcjonalność `ctlClock` poprzez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="b0f16-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0f16-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="b0f16-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b0f16-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b0f16-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b0f16-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b0f16-112">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="b0f16-112">Creating the Project</span></span>  
 <span data-ttu-id="b0f16-113">Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślną będzie poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="b0f16-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="b0f16-114">Aby utworzyć ctlClockLib Biblioteka kontrolek i kontrola ctlClock</span><span class="sxs-lookup"><span data-stu-id="b0f16-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="b0f16-115">Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b0f16-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="b0f16-116">Wybierz z listy projektów języka Visual C#, **Biblioteka kontrolek formularzy Windows** szablon projektu, należy wpisać `ctlClockLib` w **nazwa** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-116">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b0f16-117">Nazwa projektu `ctlClockLib`, również jest domyślnie przypisane do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b0f16-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="b0f16-118">Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b0f16-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="b0f16-119">Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ctlClock`, możesz określić swoje `ctlClock` za pomocą składnika `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="b0f16-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="b0f16-120">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1.cs**, a następnie kliknij przycisk **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-120">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="b0f16-121">Zmień nazwę pliku, aby `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-121">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="b0f16-122">Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="b0f16-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0f16-123">Domyślnie przez kontrolki złożonej dziedziczy <xref:System.Windows.Forms.UserControl> klasy udostępnianej przez system.</span><span class="sxs-lookup"><span data-stu-id="b0f16-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="b0f16-124"><xref:System.Windows.Forms.UserControl> Zapewnia funkcje wymagane przez formanty złożone wszystkie klasy i implementuje standardowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0f16-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="b0f16-125">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="b0f16-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="b0f16-126">Dodawanie Windows kontrolek i składników do kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="b0f16-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="b0f16-127">Interfejs graficzny jest integralną część złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="b0f16-128">Ten interfejs graficzny jest implementowany przez dodanie jednego lub kilku formantów Windows do powierzchni projektanta.</span><span class="sxs-lookup"><span data-stu-id="b0f16-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="b0f16-129">W poniższy pokaz możesz zintegrować formanty Windows złożonego formantu i napisać kod, aby zaimplementować funkcje.</span><span class="sxs-lookup"><span data-stu-id="b0f16-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="b0f16-130">Aby dodać etykietę i czasomierz do złożonego formantu</span><span class="sxs-lookup"><span data-stu-id="b0f16-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="b0f16-131">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij przycisk **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-131">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="b0f16-132">W **przybornika**, rozwiń węzeł **wspólnych formantów** węzłem, a następnie kliknij dwukrotnie plik **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-132">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="b0f16-133">A <xref:System.Windows.Forms.Label> formantu o nazwie `label1` zostanie dodany do formantu na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="b0f16-133">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="b0f16-134">W projektancie, kliknij **label1**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-134">In the designer, click **label1**.</span></span> <span data-ttu-id="b0f16-135">W oknie właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0f16-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="b0f16-136">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b0f16-136">Property</span></span>|<span data-ttu-id="b0f16-137">Zmień na</span><span class="sxs-lookup"><span data-stu-id="b0f16-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="b0f16-138">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b0f16-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="b0f16-139">**Text**</span><span class="sxs-lookup"><span data-stu-id="b0f16-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="b0f16-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="b0f16-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="b0f16-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="b0f16-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="b0f16-142">W **przybornika**, rozwiń węzeł **składniki** węzłem, a następnie kliknij dwukrotnie plik **czasomierza**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="b0f16-143">Ponieważ <xref:System.Windows.Forms.Timer> jest składnikiem, ma ona nie wizualnej reprezentacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b0f16-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="b0f16-144">W związku z tym, nie ma za pomocą kontrolek na powierzchni projektowej, ale raczej w **projektanta składników** (zasobnik w dolnej części powierzchni projektanta).</span><span class="sxs-lookup"><span data-stu-id="b0f16-144">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="b0f16-145">W **projektanta składników**, kliknij przycisk **timer1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości `1000` i <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-145">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="b0f16-146"><xref:System.Windows.Forms.Timer.Interval%2A> Właściwość kontroluje częstotliwość <xref:System.Windows.Forms.Timer> impulsów składnika.</span><span class="sxs-lookup"><span data-stu-id="b0f16-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="b0f16-147">Każdorazowo `timer1` znaczniki, uruchamia kod `timer1_Tick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0f16-147">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="b0f16-148">Interwał reprezentuje liczbę milisekund między taktami.</span><span class="sxs-lookup"><span data-stu-id="b0f16-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="b0f16-149">W **projektanta składników**, kliknij dwukrotnie **timer1** można przejść do `timer1_Tick` zdarzenie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-149">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="b0f16-150">Należy zmodyfikować kod, tak aby wyglądała jak poniższy przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="b0f16-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="b0f16-151">Pamiętaj zmieniać modyfikatora dostępu z `private` do `protected`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-151">Be sure to change the access modifier from `private` to `protected`.</span></span>  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     <span data-ttu-id="b0f16-152">Ten kod powoduje, że bieżący czas, który ma być wyświetlany w `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="b0f16-153">Ponieważ interwał `timer1` została ustawiona na `1000`, to zdarzenie wystąpi co tysięcy milisekund, w związku z tym aktualizacji bieżący czas co sekundę.</span><span class="sxs-lookup"><span data-stu-id="b0f16-153">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="b0f16-154">Zmodyfikuj metodę możliwym do zastąpienia przy użyciu `virtual` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="b0f16-154">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="b0f16-155">Aby uzyskać więcej informacji zobacz sekcję "Dziedziczenie z kontrolki użytkownika" poniżej.</span><span class="sxs-lookup"><span data-stu-id="b0f16-155">For more information, see the  "Inheriting from a User Control" section below.</span></span>  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. <span data-ttu-id="b0f16-156">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="b0f16-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="b0f16-157">Dodawanie właściwości do kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="b0f16-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="b0f16-158">Formant zegara teraz hermetyzuje <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.Timer> składnika, z których każdy swój własny zestaw właściwości związanych.</span><span class="sxs-lookup"><span data-stu-id="b0f16-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="b0f16-159">Gdy poszczególne właściwości tych kontrolek nie będą dostępne dla użytkowników kolejne kontrolki, można tworzyć i udostępnianie właściwości niestandardowych, pisząc odpowiednich bloków kodu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="b0f16-160">W poniższej procedurze będzie dodać właściwości do formantu, który umożliwia użytkownikowi zmianę koloru tła i tekstu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="b0f16-161">Aby dodać właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="b0f16-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="b0f16-162">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-162">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="b0f16-163">**Edytor kodu** dla kontrolki zostanie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b0f16-163">The **Code Editor** for your control opens.</span></span>  
  
2.  <span data-ttu-id="b0f16-164">Znajdź `public partial class ctlClock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b0f16-164">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="b0f16-165">Poniżej otwierający nawias klamrowy (`{)`, wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="b0f16-165">Beneath the opening brace (`{)`, type the following code.</span></span>  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     <span data-ttu-id="b0f16-166">Te instrukcje tworzenia zmienne prywatne, które będą używane do przechowywania wartości właściwości, które masz zamiar utworzyć.</span><span class="sxs-lookup"><span data-stu-id="b0f16-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="b0f16-167">Wpisz następujący kod pod deklaracje zmiennych w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="b0f16-167">Type the following code beneath the variable declarations from step 2.</span></span>  
  
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
  
     <span data-ttu-id="b0f16-168">Poprzedzający kod wprowadza dwie właściwości niestandardowe, `ClockForeColor` i `ClockBackColor`, która jest dostępna dla kolejnych użytkowników tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b0f16-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="b0f16-169">`get` i `set` instrukcji zapewniać przechowywania i pobierania wartości właściwości, a także kod do implementacji funkcji odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0f16-169">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="b0f16-170">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="b0f16-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="b0f16-171">Testowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="b0f16-171">Testing the Control</span></span>  
 <span data-ttu-id="b0f16-172">Formanty nie są aplikacje autonomiczne; muszą one być obsługiwane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="b0f16-172">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="b0f16-173">Testowanie zachowania w czasie wykonywania kontroli nad i sprawdzić jego właściwości, za pomocą **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="b0f16-174">Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="b0f16-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="b0f16-175">Aby przetestować formant</span><span class="sxs-lookup"><span data-stu-id="b0f16-175">To test your control</span></span>  
  
1.  <span data-ttu-id="b0f16-176">Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="b0f16-177">W siatce właściwości kontener testu, zlokalizuj `ClockBackColor` właściwości, a następnie wybierz właściwość do wyświetlenia palety kolorów.</span><span class="sxs-lookup"><span data-stu-id="b0f16-177">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>  
  
3.  <span data-ttu-id="b0f16-178">Wybierz kolor, klikając go.</span><span class="sxs-lookup"><span data-stu-id="b0f16-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="b0f16-179">Kolor tła kontrolki zmienia kolor, który wybrano.</span><span class="sxs-lookup"><span data-stu-id="b0f16-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="b0f16-180">Upewnij się, że za pomocą sekwencji podobnych zdarzeń `ClockForeColor` właściwości działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="b0f16-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
     <span data-ttu-id="b0f16-181">W poprzedniej sekcji i w tej sekcji, wiesz, jak można łączyć składników i formantów Windows z kodem i pakowania do dostarczają niestandardowych funkcjonalności w formie kontrolek złożonych.</span><span class="sxs-lookup"><span data-stu-id="b0f16-181">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="b0f16-182">Wiesz, że udostępnianie właściwości złożonej kontrolki i testowanie formantu po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-182">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="b0f16-183">W następnej sekcji zostanie dowiesz się, jak skonstruować dziedziczone kontrolki złożonej za pomocą `ctlClock` jako podstawy.</span><span class="sxs-lookup"><span data-stu-id="b0f16-183">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="b0f16-184">Dziedziczenie z kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="b0f16-184">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="b0f16-185">W poprzednich sekcjach wiesz, jak połączyć kontrolki Windows, składników i kod do kontrolek złożonych wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="b0f16-185">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="b0f16-186">Złożonego formantu może być teraz używane jako podstawa, na którym mogą być wbudowane w innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="b0f16-186">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="b0f16-187">Wyprowadzanie klasy z klasy bazowej proces jest nazywany *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="b0f16-187">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="b0f16-188">W tej sekcji spowoduje utworzenie kontrolki złożonej o nazwie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-188">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="b0f16-189">Ta kontrolka będzie pochodzić z kontrolki nadrzędnej, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-189">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="b0f16-190">Jak rozszerzyć funkcjonalność `ctlClock` nadpisywania metod nadrzędnego i dodawania nowych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0f16-190">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="b0f16-191">Pierwszym krokiem w tworzeniu odziedziczoną kontrolkę jest pochodną jego obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b0f16-191">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="b0f16-192">Ta akcja tworzy nowy formant, który zawiera wszystkie właściwości, metod i właściwości graficzne kontroli nadrzędnej, ale mogą również działać jako podstawa dla nowych lub zmodyfikowanych funkcja.</span><span class="sxs-lookup"><span data-stu-id="b0f16-192">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="b0f16-193">Aby utworzyć odziedziczoną kontrolkę</span><span class="sxs-lookup"><span data-stu-id="b0f16-193">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="b0f16-194">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **kontrolki użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-194">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="b0f16-195">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b0f16-195">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="b0f16-196">Wybierz **dziedziczone kontrolki użytkownika** szablonu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-196">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="b0f16-197">W **nazwa** wpisz `ctlAlarmClock.cs`, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-197">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="b0f16-198">**Selektor dziedziczenia** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b0f16-198">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="b0f16-199">W obszarze **nazwa składnika**, kliknij dwukrotnie **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-199">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="b0f16-200">W Eksploratorze rozwiązań należy przejrzeć bieżących projektów.</span><span class="sxs-lookup"><span data-stu-id="b0f16-200">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0f16-201">Plik o nazwie **ctlAlarmClock.cs** został dodany do bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-201">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="b0f16-202">Dodawanie właściwości alarmów</span><span class="sxs-lookup"><span data-stu-id="b0f16-202">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="b0f16-203">Właściwości są dodawane do odziedziczoną kontrolkę w taki sam sposób, w których są one dodawane do kontrolek złożonych.</span><span class="sxs-lookup"><span data-stu-id="b0f16-203">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="b0f16-204">Teraz użyjesz Składnia deklaracji właściwości można dodać dwie właściwości do kontrolki: `AlarmTime`, której będzie przechowywana wartość daty i godziny alarmu jest wyłączona, a `AlarmSet`, który będzie wskazywać, czy ustawiono alarmu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-204">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="b0f16-205">Aby dodać właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="b0f16-205">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="b0f16-206">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-206">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="b0f16-207">Znajdź `public class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b0f16-207">Locate the `public class` statement.</span></span> <span data-ttu-id="b0f16-208">Należy zauważyć, że formant dziedziczy `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-208">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="b0f16-209">Poniżej otwierający nawias klamrowy (`{)` instrukcji, wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="b0f16-209">Beneath the opening brace (`{)` statement, type the following code.</span></span>  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="b0f16-210">Dodawanie do interfejsu graficznego formantu</span><span class="sxs-lookup"><span data-stu-id="b0f16-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="b0f16-211">Odziedziczone kontrolki ma interfejs graficzny, która jest taka sama jak formant, który dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="b0f16-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="b0f16-212">Posiada on te same kontrolki składowych co kontrolki nadrzędnej, ale właściwości formantów składowych nie będzie dostępna, chyba że zostały one specjalnie ujawnione.</span><span class="sxs-lookup"><span data-stu-id="b0f16-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="b0f16-213">Można dodać do graficznego interfejsu dziedziczone złożonego formantu w taki sam sposób jak należy dodać do dowolnego złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="b0f16-214">Aby kontynuować, dodając do zegar alarm wizualny interfejs, dodasz formant etykiety, który będzie flash, gdy jest podawania alarmu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="b0f16-215">Aby dodać formant etykiety</span><span class="sxs-lookup"><span data-stu-id="b0f16-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="b0f16-216">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-216">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="b0f16-217">Projektant `ctlAlarmClock` otwiera się w głównym oknie.</span><span class="sxs-lookup"><span data-stu-id="b0f16-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="b0f16-218">Kliknij przycisk Wyświetl części kontrolki i wyświetlać w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0f16-218">Click the display portion of the control, and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0f16-219">Chociaż wyświetlane są wszystkie właściwości, są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="b0f16-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="b0f16-220">Oznacza to, że te właściwości są natywne `lblDisplay` i nie może zostać zmodyfikowany lub dostępne w oknie dialogowym właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0f16-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="b0f16-221">Domyślnie są zawarte w kontrolki złożonej kontrolki `private`, i ich właściwości nie są dostępne w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="b0f16-221">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0f16-222">Kolejni użytkownicy złożonej kontrolki mają mieć dostęp do jego wewnętrznych kontroli, zadeklarować je jako `public` lub `protected`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="b0f16-223">To pozwala ustawić i zmodyfikować właściwości formantów zawartych w złożonej kontrolki przy użyciu odpowiedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="b0f16-224">Dodaj <xref:System.Windows.Forms.Label> kontrolki złożonej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b0f16-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="b0f16-225">Za pomocą myszy, przeciągnij <xref:System.Windows.Forms.Label> formantu bezpośrednio poniżej wyświetlanego pola.</span><span class="sxs-lookup"><span data-stu-id="b0f16-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="b0f16-226">W oknie właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0f16-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="b0f16-227">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b0f16-227">Property</span></span>|<span data-ttu-id="b0f16-228">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="b0f16-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="b0f16-229">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b0f16-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="b0f16-230">**Text**</span><span class="sxs-lookup"><span data-stu-id="b0f16-230">**Text**</span></span>|<span data-ttu-id="b0f16-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="b0f16-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="b0f16-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="b0f16-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="b0f16-233">**Widoczne**</span><span class="sxs-lookup"><span data-stu-id="b0f16-233">**Visible**</span></span>|`false`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="b0f16-234">Dodawanie funkcji alarmów</span><span class="sxs-lookup"><span data-stu-id="b0f16-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="b0f16-235">W ramach poprzednich procedur dodać właściwości i formant, który spowoduje włączenie funkcji alarmu w złożonej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b0f16-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="b0f16-236">W tej procedurze należy dodać kod do porównania bieżącego czasu do czasu alarmów i, jeśli są takie same, zaktualizować alarmu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="b0f16-237">Przez zastąpienie `timer1_Tick` metody `ctlClock` i dodanie dodatkowego kodu do niego, zostaną rozszerzone możliwości `ctlAlarmClock` przy zachowaniu wszystkich funkcji związanych z `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-237">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="b0f16-238">Aby zastąpić metodę timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="b0f16-238">To override the timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="b0f16-239">W **Edytor kodu**, zlokalizuj `private bool blnAlarmSet;` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b0f16-239">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="b0f16-240">Bezpośrednio pod nim, należy dodać następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="b0f16-240">Immediately beneath it, add the following statement.</span></span>  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  <span data-ttu-id="b0f16-241">W **Edytor kodu**, zlokalizuj zamykającego nawiasu klamrowego (`})` na końcu tej klasy.</span><span class="sxs-lookup"><span data-stu-id="b0f16-241">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="b0f16-242">Tuż przed nawiasu klamrowego Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="b0f16-242">Just before the brace, add the following code.</span></span>  
  
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
  
     <span data-ttu-id="b0f16-243">Dodanie tego kodu w ramach kilku zadań.</span><span class="sxs-lookup"><span data-stu-id="b0f16-243">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="b0f16-244">`override` Instrukcja określa, że formant Aby użyć tej metody, zamiast metody, która została odziedziczona z bazowej.</span><span class="sxs-lookup"><span data-stu-id="b0f16-244">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="b0f16-245">Gdy ta metoda jest wywoływana, wywołuje metodę, zastępuje ona wywołując `base.timer1_Tick` instrukcji, zapewniając wszystkich funkcji włączonych oryginalnego formantu jest przedstawiony w tym elemencie sterującym.</span><span class="sxs-lookup"><span data-stu-id="b0f16-245">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="b0f16-246">Następnie działa dodatkowego kodu, aby włączać funkcje alarmu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-246">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="b0f16-247">Migające formant etykiety będą wyświetlane po wystąpieniu alarmu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-247">A flashing label control will appear when the alarm occurs.</span></span>  
  
     <span data-ttu-id="b0f16-248">Formant alarm zegara jest niemal ukończone.</span><span class="sxs-lookup"><span data-stu-id="b0f16-248">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="b0f16-249">Jest jedynym elementem, który pozostaje do zaimplementowania sposób, aby je wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="b0f16-249">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="b0f16-250">Aby to zrobić, można dodać kod `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="b0f16-250">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="b0f16-251">Aby wdrożyć metodę bliskie</span><span class="sxs-lookup"><span data-stu-id="b0f16-251">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="b0f16-252">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.cs**, a następnie kliknij przycisk **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-252">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="b0f16-253">Zostanie otwarty projektant.</span><span class="sxs-lookup"><span data-stu-id="b0f16-253">The designer opens.</span></span>  
  
2.  <span data-ttu-id="b0f16-254">Dodaj przycisk do formantu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-254">Add a button to the control.</span></span> <span data-ttu-id="b0f16-255">Ustaw następujące właściwości przycisku.</span><span class="sxs-lookup"><span data-stu-id="b0f16-255">Set the properties of the button as follows.</span></span>  
  
    |<span data-ttu-id="b0f16-256">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b0f16-256">Property</span></span>|<span data-ttu-id="b0f16-257">Wartość</span><span class="sxs-lookup"><span data-stu-id="b0f16-257">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b0f16-258">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b0f16-258">**Name**</span></span>|`btnAlarmOff`|  
    |<span data-ttu-id="b0f16-259">**Text**</span><span class="sxs-lookup"><span data-stu-id="b0f16-259">**Text**</span></span>|<span data-ttu-id="b0f16-260">**Wyłącz alarmów**</span><span class="sxs-lookup"><span data-stu-id="b0f16-260">**Disable Alarm**</span></span>|  
  
3.  <span data-ttu-id="b0f16-261">W projektancie, kliknij dwukrotnie **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-261">In the designer, double-click **btnAlarmOff**.</span></span>  
  
     <span data-ttu-id="b0f16-262">**Edytor kodu** otwiera `private void btnAlarmOff_Click` wiersza.</span><span class="sxs-lookup"><span data-stu-id="b0f16-262">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>  
  
4.  <span data-ttu-id="b0f16-263">Zmodyfikuj tę metodę, tak, aby wyglądała jak poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="b0f16-263">Modify this method so that it resembles the following code.</span></span>  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  <span data-ttu-id="b0f16-264">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="b0f16-264">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="b0f16-265">Za pomocą odziedziczoną kontrolkę w formularzu</span><span class="sxs-lookup"><span data-stu-id="b0f16-265">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="b0f16-266">Można przetestować kontroli nad dziedziczone przetestowane kontrolki klasy bazowej, tak samo `ctlClock`: Naciśnij klawisz F5, aby skompilować projekt i uruchomić Twoją kontrolą w **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-266">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="b0f16-267">Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="b0f16-267">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="b0f16-268">Aby przełączyć kontrolki do użycia, należy ją hostować na formularzu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-268">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="b0f16-269">Podobnie jak w przypadku złożonego formantu standardowego dziedziczone złożonego formantu nie może występować samodzielnie i musi być hostowany w formie lub innego kontenera.</span><span class="sxs-lookup"><span data-stu-id="b0f16-269">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="b0f16-270">Ponieważ `ctlAlarmClock` ma większą głębokość funkcjonalności, dodatkowy kod jest wymagany do testowania.</span><span class="sxs-lookup"><span data-stu-id="b0f16-270">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="b0f16-271">W tej procedurze, jak napisać prosty program, aby przetestować działanie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-271">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="b0f16-272">Możesz napisać kod, aby ustawić i wyświetlić `AlarmTime` właściwość `ctlAlarmClock`i przetestujesz jej nieodłączne funkcji.</span><span class="sxs-lookup"><span data-stu-id="b0f16-272">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="b0f16-273">Tworzenie i dodawanie formantu do formularza testu</span><span class="sxs-lookup"><span data-stu-id="b0f16-273">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="b0f16-274">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-274">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="b0f16-275">Dodaj nową **aplikacji Windows** projektu do rozwiązania i nadaj mu nazwę `Test`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-275">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
3.  <span data-ttu-id="b0f16-276">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** węzeł dla projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="b0f16-276">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="b0f16-277">Kliknij przycisk **Dodaj odwołanie** do wyświetlenia **Dodaj odwołanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b0f16-277">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="b0f16-278">Kliknij kartę **projektów**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-278">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="b0f16-279">Twoje `ctlClockLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-279">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="b0f16-280">Kliknij dwukrotnie projektu można dodać odwołania do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="b0f16-280">Double-click the project to add the reference to the test project.</span></span>  
  
4.  <span data-ttu-id="b0f16-281">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-281">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="b0f16-282">W **przybornika**, rozwiń węzeł **ctlClockLib składniki** węzła.</span><span class="sxs-lookup"><span data-stu-id="b0f16-282">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
6.  <span data-ttu-id="b0f16-283">Kliknij dwukrotnie **ctlAlarmClock** można dodać kopię `ctlAlarmClock` do formularza.</span><span class="sxs-lookup"><span data-stu-id="b0f16-283">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>  
  
7.  <span data-ttu-id="b0f16-284">W **przybornika**, zlokalizuj i kliknij dwukrotnie **DateTimePicker** dodać <xref:System.Windows.Forms.DateTimePicker> sterowania do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> kontroli przez dwukrotne kliknięcie **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-284">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
8.  <span data-ttu-id="b0f16-285">Umieść formanty w wygodne miejsce w formularzu za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="b0f16-285">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
9. <span data-ttu-id="b0f16-286">Ustaw właściwości tych kontrolek, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b0f16-286">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="b0f16-287">formant</span><span class="sxs-lookup"><span data-stu-id="b0f16-287">Control</span></span>|<span data-ttu-id="b0f16-288">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b0f16-288">Property</span></span>|<span data-ttu-id="b0f16-289">Wartość</span><span class="sxs-lookup"><span data-stu-id="b0f16-289">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="b0f16-290">**Text**</span><span class="sxs-lookup"><span data-stu-id="b0f16-290">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="b0f16-291">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b0f16-291">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="b0f16-292">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="b0f16-292">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="b0f16-293">**Format**</span><span class="sxs-lookup"><span data-stu-id="b0f16-293">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. <span data-ttu-id="b0f16-294">W projektancie, kliknij dwukrotnie **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-294">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="b0f16-295">**Edytor kodu** otwiera `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-295">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>  
  
11. <span data-ttu-id="b0f16-296">Zmodyfikuj kod, dzięki czemu jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="b0f16-296">Modify the code so that it resembles the following.</span></span>  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. <span data-ttu-id="b0f16-297">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-297">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
13. <span data-ttu-id="b0f16-298">Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="b0f16-298">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="b0f16-299">Zostanie uruchomiony test program.</span><span class="sxs-lookup"><span data-stu-id="b0f16-299">The test program starts.</span></span> <span data-ttu-id="b0f16-300">Należy pamiętać, że bieżący czas jest aktualizowana w `ctlAlarmClock` kontroli i że godzina rozpoczęcia jest wyświetlany w <xref:System.Windows.Forms.DateTimePicker> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b0f16-300">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
14. <span data-ttu-id="b0f16-301">Kliknij przycisk <xref:System.Windows.Forms.DateTimePicker> gdzie minuty godziny są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b0f16-301">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
15. <span data-ttu-id="b0f16-302">Za pomocą klawiatury, ustaw wartość minut, która jest większa niż bieżąca godzina wyświetlane według jedną minutę `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-302">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="b0f16-303">Czas ustawienie alarmu jest wyświetlany w `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-303">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="b0f16-304">Poczekaj, aż wyświetlonym czasie osiągnąć czas ustawienie alarmu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-304">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="b0f16-305">Po wyświetlonym czasie osiągnie czas, w którym ustawiono alarmu, `lblAlarm` będzie flash.</span><span class="sxs-lookup"><span data-stu-id="b0f16-305">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>  
  
16. <span data-ttu-id="b0f16-306">Wyłączyć alarm, klikając `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="b0f16-306">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="b0f16-307">Może teraz zresetować alarmu.</span><span class="sxs-lookup"><span data-stu-id="b0f16-307">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="b0f16-308">W tym przewodniku ma obejmujący wiele kluczowych założeń.</span><span class="sxs-lookup"><span data-stu-id="b0f16-308">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="b0f16-309">Wiesz, że tworzenie formantu złożonego, łącząc w kontenerze kontrolek złożonych kontrolek i składników.</span><span class="sxs-lookup"><span data-stu-id="b0f16-309">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="b0f16-310">Wiesz, można dodać właściwości do kontrolki, a następnie napisać kod do implementacji funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="b0f16-310">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="b0f16-311">W ostatniej sekcji pokazano, aby rozszerzyć funkcjonalność danej kontrolki złożonej za pomocą dziedziczenia i zmieniać funkcje metod hosta przez zastąpienie tych metod.</span><span class="sxs-lookup"><span data-stu-id="b0f16-311">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f16-312">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0f16-312">See also</span></span>
- [<span data-ttu-id="b0f16-313">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b0f16-313">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
- [<span data-ttu-id="b0f16-314">Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="b0f16-314">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="b0f16-315">Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="b0f16-315">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
