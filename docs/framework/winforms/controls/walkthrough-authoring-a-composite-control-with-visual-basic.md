---
title: "Wskazówki: tworzenie formantu złożonego za pomocą Visual Basic"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c31e76e9f190990f0a3dddab359ef9523783d955
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="f4dfa-102">Wskazówki: tworzenie formantu złożonego za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4dfa-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="f4dfa-103">Formanty złożone umożliwiają za pomocą którego niestandardowych interfejsów graficznego można tworzyć i użyć ponownie.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="f4dfa-104">Formantu złożonego jest zasadniczo składnik o wizualnej reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="f4dfa-105">W efekcie może składać się z co najmniej jeden program Windows Forms kontrolki, składniki lub bloki kodu, które mogą rozszerzyć funkcjonalność, sprawdzanie poprawności danych wejściowych użytkownika, modyfikując właściwości ekranu lub wykonywania innych zadań wymaganych przez autora.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="f4dfa-106">Formanty złożone można umieścić w formularzach systemu Windows w taki sam sposób jak inne formanty.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="f4dfa-107">W pierwszej części tego przewodnika, tworzenie prostego formantu złożonego o nazwie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="f4dfa-108">W drugiej części tego przewodnika, można rozszerzyć funkcjonalność `ctlClock` przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4dfa-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f4dfa-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f4dfa-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f4dfa-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f4dfa-112">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="f4dfa-112">Creating the Project</span></span>  
 <span data-ttu-id="f4dfa-113">Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślna będzie poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="f4dfa-114">Aby utworzyć biblioteki formantu ctlClockLib i kontroli ctlClock</span><span class="sxs-lookup"><span data-stu-id="f4dfa-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="f4dfa-115">Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="f4dfa-116">Z listy [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projektów, wybierz opcję **Biblioteka formantów systemu Windows** szablon projektu, typ `ctlClockLib` w **nazwa** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-116">From the list of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f4dfa-117">Nazwa projektu `ctlClockLib`, jest również przypisany do głównej przestrzeni nazw domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="f4dfa-118">Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="f4dfa-119">Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ctlClock`, można określić użytkownika `ctlClock` za pomocą składnika`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="f4dfa-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="f4dfa-120">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **UserControl1.vb**, a następnie kliknij przycisk **zmienić**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-120">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="f4dfa-121">Zmień nazwę pliku, aby `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-121">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="f4dfa-122">Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="f4dfa-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4dfa-123">Domyślnie formantu złożonego dziedziczy <xref:System.Windows.Forms.UserControl> klasy obsługiwanych przez system.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="f4dfa-124"><xref:System.Windows.Forms.UserControl> Klasa udostępnia funkcje wymagane przez formanty wszystkie złożone i implementuje standardowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="f4dfa-125">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="f4dfa-126">Dodawanie Windows formanty i składniki do złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="f4dfa-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="f4dfa-127">Wizualny interfejs jest integralną część złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="f4dfa-128">Ten interfejs visual jest implementowany przez dodanie jednego lub kilku formantów systemu Windows na powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="f4dfa-129">W następujących wykazanie możesz dołączyć formantów systemu Windows do formantu złożonego i napisać kod do implementacji funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="f4dfa-130">Aby dodać etykietę i czasomierz do formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="f4dfa-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="f4dfa-131">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.vb**, a następnie kliknij przycisk **Widok projektanta**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-131">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="f4dfa-132">W przyborniku rozwiń **formanty standardowe** węzeł, a następnie kliknij dwukrotnie plik **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-132">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="f4dfa-133">A <xref:System.Windows.Forms.Label> formantu o nazwie `Label1` zostanie dodany do formantu na powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-133">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="f4dfa-134">W projektancie, kliknij **Label1**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-134">In the designer, click **Label1**.</span></span> <span data-ttu-id="f4dfa-135">W oknie właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="f4dfa-136">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f4dfa-136">Property</span></span>|<span data-ttu-id="f4dfa-137">Zmień na</span><span class="sxs-lookup"><span data-stu-id="f4dfa-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="f4dfa-138">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="f4dfa-139">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="f4dfa-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="f4dfa-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="f4dfa-142">W **przybornika**, rozwiń węzeł **składniki** węzeł, a następnie kliknij dwukrotnie plik **czasomierza**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="f4dfa-143">Ponieważ <xref:System.Windows.Forms.Timer> to składnik go nie ma reprezentacji wizualnej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="f4dfa-144">W związku z tym nie ma z formantami na powierzchni projektanta, ale w Projektancie składników (na pasku zadań u dołu powierzchni projektanta).</span><span class="sxs-lookup"><span data-stu-id="f4dfa-144">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="f4dfa-145">W Projektancie składników, kliknij przycisk **czasomierz 1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości `1000` i <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `True`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-145">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>  
  
     <span data-ttu-id="f4dfa-146"><xref:System.Windows.Forms.Timer.Interval%2A> Właściwość kontroluje częstotliwość, z którym składnika timer znaczników.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="f4dfa-147">Zawsze `Timer1` znaczniki, go uruchamia kod w `Timer1_Tick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-147">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="f4dfa-148">Interwał reprezentuje liczbę milisekund między taktami.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="f4dfa-149">W Projektancie składników, kliknij dwukrotnie **czasomierz 1** można przejść do `Timer1_Tick` zdarzenia dla `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-149">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="f4dfa-150">Zmodyfikuj kod, aby go podobny Poniższy przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="f4dfa-151">Należy zmienić modyfikator dostępu z `Private` do `Protected`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-151">Be sure to change the access modifier from `Private` to `Protected`.</span></span>  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     <span data-ttu-id="f4dfa-152">Ten kod spowoduje, że bieżący czas, który będzie wyświetlany w `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="f4dfa-153">Ponieważ interwał `Timer1` ustawiono `1000`, to zdarzenie wystąpi co tysięcy milisekund, w związku z tym aktualizowanie bieżący czas ciągu sekundy.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-153">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="f4dfa-154">Zmodyfikuj metodę, aby możliwym do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-154">Modify the method to be overridable.</span></span> <span data-ttu-id="f4dfa-155">Aby uzyskać więcej informacji zobacz sekcję "Dziedziczy z kontrolki użytkownika" poniżej.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-155">For more information, see the "Inheriting from a User Control" section below.</span></span>  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. <span data-ttu-id="f4dfa-156">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="f4dfa-157">Dodawanie właściwości do złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="f4dfa-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="f4dfa-158">Teraz hermetyzuje formantu zegara <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.Timer> z zestawem właściwości związanego z używaniem składnika.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="f4dfa-159">Podczas poszczególnych właściwości tych kontrolek nie będzie dostępna dla kolejnych użytkowników formantu, można tworzyć i ujawnia właściwości niestandardowe pisząc odpowiednie bloki kodu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="f4dfa-160">W poniższej procedurze właściwości doda do formantu, który umożliwia użytkownikowi zmianę koloru tła i tekstu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="f4dfa-161">Aby dodać właściwość do formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="f4dfa-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="f4dfa-162">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClock.vb**, a następnie kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-162">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="f4dfa-163">Otwiera edytora kodu dla formantu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-163">The Code Editor for your control opens.</span></span>  
  
2.  <span data-ttu-id="f4dfa-164">Zlokalizuj `Public Class ctlClock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-164">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="f4dfa-165">Poniżej wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-165">Beneath it, type the following code.</span></span>  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     <span data-ttu-id="f4dfa-166">Te instrukcje tworzenia zmiennych prywatnych, które będzie używany do przechowywania wartości właściwości, które zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="f4dfa-167">Wstaw następujący kod pod deklaracje zmiennej w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-167">Insert the following code beneath the variable declarations from step 2.</span></span>  
  
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
  
     <span data-ttu-id="f4dfa-168">Poprzedni kod sprawia, że dwie właściwości niestandardowej, `ClockForeColor` i `ClockBackColor`, dostępne dla użytkowników kolejnych tego formantu, wywołując `Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="f4dfa-169">`Get` i `Set` zapewniają instrukcje dla magazynu i pobierania wartości właściwości, a także kod do implementowania odpowiednie właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-169">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="f4dfa-170">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="f4dfa-171">Testowanie formantu</span><span class="sxs-lookup"><span data-stu-id="f4dfa-171">Testing the Control</span></span>  
 <span data-ttu-id="f4dfa-172">Formanty nie są autonomicznych projektów; muszą one być obsługiwane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-172">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="f4dfa-173">Testowanie zachowania w czasie wykonywania formantu i wykonywania jej właściwości z **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="f4dfa-174">Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="f4dfa-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="f4dfa-175">Aby przetestować formantu</span><span class="sxs-lookup"><span data-stu-id="f4dfa-175">To test your control</span></span>  
  
1.  <span data-ttu-id="f4dfa-176">Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="f4dfa-177">Kontener testu siatki właściwości, wybierz `ClockBackColor` właściwości, a następnie kliknij strzałkę listy rozwijanej do wyświetlania paletę kolorów.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-177">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>  
  
3.  <span data-ttu-id="f4dfa-178">Wybierz kolor, klikając go.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="f4dfa-179">Kolor wybranego zmienia kolor tła formantu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="f4dfa-180">Sprawdź, czy za pomocą sekwencji podobnych zdarzeń `ClockForeColor` właściwości działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
5.  <span data-ttu-id="f4dfa-181">Kliknij przycisk **zamknąć** zamknąć **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-181">Click **Close** to close the **UserControl Test Container**.</span></span>  
  
     <span data-ttu-id="f4dfa-182">W tej sekcji i poprzednich sekcjach, już wspomniano, jak można łączyć składników i formantów systemu Windows z kodem i pakowania umożliwiają korzystanie z funkcji niestandardowych w formie formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-182">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="f4dfa-183">Wiesz już ujawnić właściwości formantu złożonego i testowanie formantu po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-183">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="f4dfa-184">W następnej sekcji dowiesz sposób tworzenia dziedziczonych formantu złożonego za pomocą `ctlClock` jako podstawy.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-184">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="f4dfa-185">Dziedziczenie z formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="f4dfa-185">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="f4dfa-186">W poprzednich sekcjach przedstawiono sposób łączenia formantów systemu Windows, składników i kodu w wielokrotnego użytku formanty złożone.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-186">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="f4dfa-187">Można teraz używać formantu złożonego jako podstawa, na których mogą być tworzone na inne formanty.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-187">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="f4dfa-188">Wyprowadzanie klasy z klasy podstawowej proces jest nazywany *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-188">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="f4dfa-189">W tej sekcji utworzysz formantu złożonego o nazwie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-189">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="f4dfa-190">Ten formant będzie pochodzić z kontrolki nadrzędnej, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-190">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="f4dfa-191">Dowiesz się rozszerzyć funkcjonalność `ctlClock` przez zastąpienie metody nadrzędnego i dodawanie nowych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-191">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="f4dfa-192">Pierwszym krokiem tworzenia dziedziczonych kontrolek jest pochodną nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-192">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="f4dfa-193">Ta akcja tworzy nowy formant, który zawiera wszystkie właściwości, metody i właściwości graficzne kontrolki nadrzędnej, ale mogą również działać jako podstawa dla nowych lub zmodyfikowanych funkcja.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-193">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="f4dfa-194">Można utworzyć formantu dziedziczonych</span><span class="sxs-lookup"><span data-stu-id="f4dfa-194">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="f4dfa-195">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **kontrolki użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-195">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="f4dfa-196">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-196">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="f4dfa-197">Wybierz **dziedziczone kontrolki użytkownika** szablonu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-197">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="f4dfa-198">W **nazwa** wpisz `ctlAlarmClock.vb`, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-198">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="f4dfa-199">**Selektora dziedziczenia** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-199">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="f4dfa-200">W obszarze **nazwa składnika**, kliknij dwukrotnie **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-200">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="f4dfa-201">W Eksploratorze rozwiązań przeglądać bieżących projektów.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-201">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4dfa-202">Plik o nazwie **ctlAlarmClock.vb** został dodany do bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-202">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="f4dfa-203">Dodawanie właściwości alarmu</span><span class="sxs-lookup"><span data-stu-id="f4dfa-203">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="f4dfa-204">Właściwości są dodawane do formantu dziedziczone w taki sam sposób, są one dodawane do formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-204">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="f4dfa-205">Teraz użyje składni deklaracji właściwości można dodać dwóch właściwości do formantu: `AlarmTime`, który będzie przechowywać wartość daty i godziny alarm jest wyłączona, i `AlarmSet`, który będzie wskazywać, czy ustawiono alarm.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-205">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="f4dfa-206">Aby dodać właściwości do formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="f4dfa-206">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="f4dfa-207">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-207">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="f4dfa-208">Zlokalizuj deklaracja klasy formantu ctlAlarmClock, który jest wyświetlany jako `Public Class ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-208">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="f4dfa-209">W deklaracji klasy wstaw poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-209">In the class declaration, insert the following code.</span></span>  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="f4dfa-210">Dodawanie do formantu interfejsu graficznego</span><span class="sxs-lookup"><span data-stu-id="f4dfa-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="f4dfa-211">Dziedziczony formantu ma wizualny interfejs, który jest taki sam jak formant, który dziedziczy z.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="f4dfa-212">Posiada tego samego formanty składników jako kontrolki nadrzędnej, ale właściwości formantów składowych nie będą dostępne, chyba że zostały one specjalnie widoczne.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="f4dfa-213">Można dodać do interfejsu graficznego dziedziczone formantu złożonego w taki sam sposób, jak z żadnym formantem złożonego.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="f4dfa-214">Aby kontynuować, dodawanie do wizualny interfejs zegar alarmu, należy dodać formant etykiety, który będzie flash, gdy jest podawania alarm.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="f4dfa-215">Aby dodać formantu etykiety</span><span class="sxs-lookup"><span data-stu-id="f4dfa-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="f4dfa-216">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock**i kliknij przycisk **Widok projektanta**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-216">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>  
  
     <span data-ttu-id="f4dfa-217">Projektant `ctlAlarmClock` w głównym oknie zostanie otwarta.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="f4dfa-218">Kliknij przycisk `lblDisplay` (wyświetlania część kontrolka) i wyświetlić okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-218">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4dfa-219">Gdy wyświetlane są wszystkie właściwości, są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="f4dfa-220">Oznacza to, że te właściwości są macierzysty `lblDisplay` i nie można zmodyfikować lub dostępne w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="f4dfa-221">Domyślnie formantach zawartych w kontrolce złożone są `Private`, i ich właściwości nie są dostępne w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-221">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4dfa-222">Kolejni użytkownicy złożonego formantu do dostępu do jego kontrole wewnętrzne należy zadeklarować je jako `Public` lub `Protected`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="f4dfa-223">Umożliwi to ustawienie i modyfikowanie właściwości kontrolki zawartych w formantu złożonego za pomocą odpowiedni kod.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="f4dfa-224">Dodaj <xref:System.Windows.Forms.Label> formantu złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="f4dfa-225">Za pomocą myszy, przeciągnij <xref:System.Windows.Forms.Label> formantu natychmiast poniżej wyświetlanego pola.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="f4dfa-226">W oknie właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="f4dfa-227">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f4dfa-227">Property</span></span>|<span data-ttu-id="f4dfa-228">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="f4dfa-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="f4dfa-229">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="f4dfa-230">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-230">**Text**</span></span>|<span data-ttu-id="f4dfa-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="f4dfa-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="f4dfa-233">**Widoczne**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-233">**Visible**</span></span>|`False`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="f4dfa-234">Dodawanie funkcji alarmu</span><span class="sxs-lookup"><span data-stu-id="f4dfa-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="f4dfa-235">W ramach poprzednich procedur dodać właściwości i kontrolkę, która spowoduje włączenie funkcji alarm złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="f4dfa-236">W tej procedurze zostanie Dodaj kod, aby porównany bieżący czas na czas alarmu i, jeśli są one takie same, dźwiękowe i alarmu flash.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="f4dfa-237">Przez zastąpienie `Timer1_Tick` metody `ctlClock` i dodanie dodatkowego kodu do niego, zostaną rozszerzyć możliwości `ctlAlarmClock` przy zachowaniu wszystkie funkcje związane z `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-237">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="f4dfa-238">Aby zastąpić metodę Timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="f4dfa-238">To override the Timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="f4dfa-239">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.vb**, a następnie kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-239">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="f4dfa-240">Zlokalizuj `Private blnAlarmSet As Boolean` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-240">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="f4dfa-241">Natychmiast poniżej, dodaj następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-241">Immediately beneath it, add the following statement.</span></span>  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  <span data-ttu-id="f4dfa-242">Zlokalizuj `End Class` instrukcji w dolnej części strony.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-242">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="f4dfa-243">Tuż przed `End Class` instrukcji, Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-243">Just before the `End Class` statement, add the following code.</span></span>  
  
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
  
     <span data-ttu-id="f4dfa-244">Dodanie tego kodu wykonuje kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-244">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="f4dfa-245">`Overrides` Instrukcji kieruje formant do użycia tej metody zamiast metody, która została odziedziczona z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-245">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="f4dfa-246">Gdy ta metoda jest wywoływana, wywołuje metodę zastępuje on wywołując `MyBase.Timer1_Tick` instrukcji zapewnienie, że włączone wszystkie funkcje kontroli oryginalnego jest przedstawiony w tym formancie.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-246">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="f4dfa-247">Następnie uruchomieniu dodatkowy kod w celu włączać funkcje alarm.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-247">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="f4dfa-248">Po wystąpieniu alarmu, a sygnały dźwiękowe będzie Twój głos zostanie wysłuchany pojawi miga formantu etykiety.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-248">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4dfa-249">Ponieważ program obsługi zdarzeń dziedziczone są zastępowanie, nie masz określa zdarzenie z `Handles` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-249">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="f4dfa-250">Zdarzenie jest już podłączony.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-250">The event is already hooked up.</span></span> <span data-ttu-id="f4dfa-251">Wszystko, co jest zastępowanie to implementację programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-251">All you are overriding is the implementation of the handler.</span></span>  
  
     <span data-ttu-id="f4dfa-252">Formant alarm zegara jest niemal ukończone.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-252">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="f4dfa-253">Jedyną operacją, której jest wdrożenie sposób, aby je wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-253">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="f4dfa-254">Aby to zrobić, można dodać kod `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-254">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="f4dfa-255">Aby zaimplementować metodę bliskie</span><span class="sxs-lookup"><span data-stu-id="f4dfa-255">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="f4dfa-256">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock.vb**, a następnie kliknij przycisk **Widok projektanta**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-256">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="f4dfa-257">W projektancie, kliknij dwukrotnie **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-257">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="f4dfa-258">**Edytora kodu** otwiera `Private Sub lblAlarm_Click` wiersza.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-258">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>  
  
3.  <span data-ttu-id="f4dfa-259">Zmodyfikuj tę metodę, tak, aby podobny do następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-259">Modify this method so that it resembles the following code.</span></span>  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  <span data-ttu-id="f4dfa-260">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-260">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="f4dfa-261">Przy użyciu dziedziczone kontrolkę w formularzu</span><span class="sxs-lookup"><span data-stu-id="f4dfa-261">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="f4dfa-262">Można przetestować dziedziczone formantu przetestowane formantu klasy podstawowej, tak samo `ctlClock`: naciśnij klawisz F5, aby skompilować projekt i uruchomić kontrolę w **kontenera testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="f4dfa-263">Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="f4dfa-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="f4dfa-264">Aby umieścić formantu do użycia, należy udostępnić go w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="f4dfa-265">Podobnie jak w przypadku złożonego formantu standardowego, dziedziczone formantu złożonego nie może występować samodzielnie i musi być hostowany w formularzu lub innych kontenera.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="f4dfa-266">Ponieważ `ctlAlarmClock` głębokość większej funkcjonalności, dodatkowy kod jest wymagany do testowania go.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="f4dfa-267">W tej procedurze, jak napisać prosty program, aby przetestować funkcje `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="f4dfa-268">Jak napisać kod, aby ustawić i wyświetlić `AlarmTime` właściwość `ctlAlarmClock`i Testuj jego związanego z używaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="f4dfa-269">Tworzenie i dodawanie formantu do formularza testu</span><span class="sxs-lookup"><span data-stu-id="f4dfa-269">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="f4dfa-270">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-270">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="f4dfa-271">Na **pliku** menu wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-271">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="f4dfa-272">Dodaj nową **aplikacji systemu Windows** projektu do rozwiązania i nadaj mu nazwę `Test`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
     <span data-ttu-id="f4dfa-273">**Testu** projekt zostanie dodany do Eksploratora rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-273">The **Test** project is added to Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="f4dfa-274">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `Test` węzła projektu, a następnie kliknij przycisk **Dodaj odwołanie** do wyświetlenia **Dodaj odwołanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-274">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="f4dfa-275">Kliknij kartę **projekty**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="f4dfa-276">Projekt **ctlClockLib** zostaną wyświetlone w obszarze **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-276">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="f4dfa-277">Kliknij dwukrotnie **ctlClockLib** można dodać odwołania do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-277">Double-click **ctlClockLib** to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="f4dfa-278">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
7.  <span data-ttu-id="f4dfa-279">W **przybornika**, rozwiń węzeł **ctlClockLib składniki** węzła.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
8.  <span data-ttu-id="f4dfa-280">Kliknij dwukrotnie **ctlAlarmClock** można dodać wystąpienia `ctlAlarmClock` do formularza.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-280">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>  
  
9. <span data-ttu-id="f4dfa-281">W **przybornika**, Znajdź i kliknij dwukrotnie **DateTimePicker** można dodać <xref:System.Windows.Forms.DateTimePicker> sterowania do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> kontroli przez dwukrotne kliknięcie **etykiety**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
10. <span data-ttu-id="f4dfa-282">Umieść formanty w dogodnym miejscu w formularzu za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-282">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
11. <span data-ttu-id="f4dfa-283">Ustaw właściwości tych kontrolek w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-283">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="f4dfa-284">Formant</span><span class="sxs-lookup"><span data-stu-id="f4dfa-284">Control</span></span>|<span data-ttu-id="f4dfa-285">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f4dfa-285">Property</span></span>|<span data-ttu-id="f4dfa-286">Wartość</span><span class="sxs-lookup"><span data-stu-id="f4dfa-286">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="f4dfa-287">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-287">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="f4dfa-288">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-288">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="f4dfa-289">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-289">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="f4dfa-290">**Format**</span><span class="sxs-lookup"><span data-stu-id="f4dfa-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. <span data-ttu-id="f4dfa-291">W projektancie, kliknij dwukrotnie **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-291">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="f4dfa-292">**Edytora kodu** otwiera się `Private Sub dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-292">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>  
  
13. <span data-ttu-id="f4dfa-293">Zmodyfikuj kod, dzięki czemu jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-293">Modify the code so that it resembles the following.</span></span>  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. <span data-ttu-id="f4dfa-294">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **testu**, a następnie kliknij przycisk **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
15. <span data-ttu-id="f4dfa-295">Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-295">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="f4dfa-296">Uruchamia test program.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-296">The test program starts.</span></span> <span data-ttu-id="f4dfa-297">Należy pamiętać, że bieżący czas jest aktualizowany w `ctlAlarmClock` kontroli i czy czas rozpoczęcia jest wyświetlany w <xref:System.Windows.Forms.DateTimePicker> formantu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
16. <span data-ttu-id="f4dfa-298">Kliknij przycisk <xref:System.Windows.Forms.DateTimePicker> gdzie minuty, godziny są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
17. <span data-ttu-id="f4dfa-299">Przy użyciu klawiatury, ustaw wartość minut, która jest większa niż bieżący czas systemowy przez jedną minutę `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="f4dfa-300">Czas w ustawieniach alarm, gdy jest wyświetlany w obszarze `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="f4dfa-301">Poczekaj na wyświetlonej czasu do czasu ustawienie alarmu.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="f4dfa-302">Po wyświetlonym czasie osiągnie czas, do którego ustawiono alarmu, dźwiękowe dźwięku i `lblAlarm` będzie flash.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-302">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>  
  
18. <span data-ttu-id="f4dfa-303">Wyłączyć alarm, klikając `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-303">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="f4dfa-304">Alarm mogą teraz zresetować.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-304">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="f4dfa-305">Ten przewodnik zawiera obejmujący wiele kluczowych założeń.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="f4dfa-306">Wiesz już, można utworzyć formantu złożonego przez połączenie formanty i składniki w kontenerze formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="f4dfa-307">Kiedy znasz już pozwala dodać właściwości do formantu i napisać kod do implementacji funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="f4dfa-308">W ostatniej sekcji przedstawiono mogą rozszerzyć funkcjonalność danego formantu złożonego za pomocą dziedziczenia i zmieniać funkcje metod hosta przez zastąpienie tych metod.</span><span class="sxs-lookup"><span data-stu-id="f4dfa-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4dfa-309">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4dfa-309">See Also</span></span>  
 [<span data-ttu-id="f4dfa-310">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f4dfa-310">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="f4dfa-311">Instrukcje: tworzenie kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="f4dfa-311">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [<span data-ttu-id="f4dfa-312">Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="f4dfa-312">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="f4dfa-313">Wskazówki dotyczące tworzenia składników</span><span class="sxs-lookup"><span data-stu-id="f4dfa-313">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
