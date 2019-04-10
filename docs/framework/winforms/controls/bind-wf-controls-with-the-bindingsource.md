---
title: 'Instrukcje: wiązanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: a4f87303954494e8e32d32e68fb3f1244f25680a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304561"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="caadb-102">Instrukcje: wiązanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="caadb-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="caadb-103">Po dodać formanty do formularza i określić interfejsu użytkownika dla aplikacji, formanty można powiązać ze źródłem danych, tak, aby w czasie wykonywania, użytkownicy mogą zmienić i zapisać dane związane z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="caadb-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>  
  
 <span data-ttu-id="caadb-104">Powiązania kontroli lub szeregu formantów w formularzach Windows Forms najłatwiej odbywa się przy użyciu <xref:System.Windows.Forms.BindingSource> kontroli jako Most między kontrolek w formularzu i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="caadb-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>  
  
 <span data-ttu-id="caadb-105">Co najmniej jedną kontrolkę w formularzu można powiązać z danych. w poniższej procedurze <xref:System.Windows.Forms.TextBox> kontrolka jest powiązana ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="caadb-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>  
  
 <span data-ttu-id="caadb-106">Aby ukończyć tę procedurę, zakłada się, czy zostaną powiązane ze źródłem danych pochodzących z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="caadb-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="caadb-107">Aby uzyskać więcej informacji na temat tworzenia źródeł danych z innych magazynów danych, zobacz [dodasz nowe źródła danych](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="caadb-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="caadb-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="caadb-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="caadb-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="caadb-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="caadb-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="caadb-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="caadb-111">Aby powiązać formant w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="caadb-111">To bind a control at design time</span></span>  
  
1. <span data-ttu-id="caadb-112">Przeciągnij <xref:System.Windows.Forms.TextBox> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="caadb-112">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>  
  
2. <span data-ttu-id="caadb-113">W **właściwości** okna:</span><span class="sxs-lookup"><span data-stu-id="caadb-113">In the **Properties** window:</span></span>  
  
    1.  <span data-ttu-id="caadb-114">Rozwiń **(powiązania danych)** węzła.</span><span class="sxs-lookup"><span data-stu-id="caadb-114">Expand the **(DataBindings)** node.</span></span>  
  
    2.  <span data-ttu-id="caadb-115">Kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="caadb-115">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
         <span data-ttu-id="caadb-116">**DataSource** zostanie otwarty Edytor typów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="caadb-116">The **DataSource** UI type editor opens.</span></span>  
  
         <span data-ttu-id="caadb-117">Jeśli wcześniej skonfigurowano źródła danych dla projektu lub formularza, pojawi się.</span><span class="sxs-lookup"><span data-stu-id="caadb-117">If a data source has previously been configured for the project or form, it will appear.</span></span>  
  
3. <span data-ttu-id="caadb-118">Kliknij przycisk **Dodaj źródło danych projektu** do nawiązywania połączeń z danymi i Utwórz źródło danych.</span><span class="sxs-lookup"><span data-stu-id="caadb-118">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
4. <span data-ttu-id="caadb-119">Na **Kreatora konfiguracji źródła danych** strona powitalna, kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="caadb-119">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
5. <span data-ttu-id="caadb-120">Na **wybierz typ źródła danych** wybierz opcję **bazy danych**.</span><span class="sxs-lookup"><span data-stu-id="caadb-120">On the **Choose a Data Source Type** page, select **Database**.</span></span>  
  
6. <span data-ttu-id="caadb-121">Na **wybierz połączenie danych** wybierz połączenie danych z listy dostępnych połączeń.</span><span class="sxs-lookup"><span data-stu-id="caadb-121">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="caadb-122">Jeśli żądane połączenie danych nie jest dostępna, wybierz **nowe połączenie** Aby utworzyć nowe połączenie danych.</span><span class="sxs-lookup"><span data-stu-id="caadb-122">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>  
  
7. <span data-ttu-id="caadb-123">Wybierz **tak, Zapisz połączenie** można zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="caadb-123">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
8. <span data-ttu-id="caadb-124">Wybierz obiekty bazy danych w celu dostosowania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="caadb-124">Select the database objects to bring into your application.</span></span> <span data-ttu-id="caadb-125">W takim przypadku wybierz pola w tabeli, które chcieliby <xref:System.Windows.Forms.TextBox> do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="caadb-125">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>  
  
9. <span data-ttu-id="caadb-126">Zastąp domyślną nazwę zestawu danych, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="caadb-126">Replace the default dataset name if you want.</span></span>  
  
10. <span data-ttu-id="caadb-127">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="caadb-127">Click **Finish**.</span></span>  
  
11. <span data-ttu-id="caadb-128">W **właściwości** okna, kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwość ponownie.</span><span class="sxs-lookup"><span data-stu-id="caadb-128">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="caadb-129">W **DataSource** Edytor typów interfejsu użytkownika, wybierz nazwę pola, które można powiązać <xref:System.Windows.Forms.TextBox> do.</span><span class="sxs-lookup"><span data-stu-id="caadb-129">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>  
  
     <span data-ttu-id="caadb-130">**DataSource** typ interfejsu użytkownika edytora zostanie zamknięty i zestaw danych <xref:System.Windows.Forms.BindingSource> karty tabeli specyficzne dla, połączenia danych są dodawane do formularza.</span><span class="sxs-lookup"><span data-stu-id="caadb-130">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caadb-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="caadb-131">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="caadb-132">Dodawanie nowych źródeł danych</span><span class="sxs-lookup"><span data-stu-id="caadb-132">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- [<span data-ttu-id="caadb-133">Okno Źródła danych</span><span class="sxs-lookup"><span data-stu-id="caadb-133">Data Sources Window</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))