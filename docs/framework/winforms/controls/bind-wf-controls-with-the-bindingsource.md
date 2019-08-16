---
title: 'Instrukcje: wiązanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 180fafa9ace5927fd84ec5dc0a1b2a342f771efd
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040016"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="618be-102">Instrukcje: wiązanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="618be-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="618be-103">Po dodaniu kontrolek do formularza i określeniu interfejsu użytkownika dla aplikacji można powiązać kontrolki ze źródłem danych, aby w czasie wykonywania użytkownicy mogli zmieniać i zapisywać dane związane z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="618be-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>

 <span data-ttu-id="618be-104">Powiązanie kontrolki lub serii formantów w Windows Forms jest najłatwiej realizowane przy użyciu <xref:System.Windows.Forms.BindingSource> formantu jako mostka między kontrolkami w formularzu a źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="618be-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>

 <span data-ttu-id="618be-105">Co najmniej jedna kontrolka w formularzu może być powiązana z danymi; w poniższej procedurze <xref:System.Windows.Forms.TextBox> formant jest powiązany ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="618be-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>

 <span data-ttu-id="618be-106">Aby wykonać tę procedurę, zakłada się, że zostanie utworzone powiązanie ze źródłem danych uzyskanym z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="618be-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="618be-107">Aby uzyskać więcej informacji na temat tworzenia źródeł danych z innych magazynów danych, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="618be-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>

## <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="618be-108">Aby powiązać formant w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="618be-108">To bind a control at design time</span></span>

1. <span data-ttu-id="618be-109"><xref:System.Windows.Forms.TextBox> Przeciągnij kontrolkę do formularza.</span><span class="sxs-lookup"><span data-stu-id="618be-109">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>

2. <span data-ttu-id="618be-110">W oknie **Właściwości** :</span><span class="sxs-lookup"><span data-stu-id="618be-110">In the **Properties** window:</span></span>

    1. <span data-ttu-id="618be-111">Rozwiń węzeł **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="618be-111">Expand the **(DataBindings)** node.</span></span>

    2. <span data-ttu-id="618be-112">Kliknij strzałkę obok <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="618be-112">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

         <span data-ttu-id="618be-113">Zostanie otwarty Edytor typów interfejsu użytkownika **źródła danych** .</span><span class="sxs-lookup"><span data-stu-id="618be-113">The **DataSource** UI type editor opens.</span></span>

         <span data-ttu-id="618be-114">Jeśli źródło danych zostało wcześniej skonfigurowane dla projektu lub formularza, pojawi się.</span><span class="sxs-lookup"><span data-stu-id="618be-114">If a data source has previously been configured for the project or form, it will appear.</span></span>

3. <span data-ttu-id="618be-115">Kliknij pozycję **Dodaj źródło danych projektu** , aby połączyć się z danymi i utworzyć źródło danych.</span><span class="sxs-lookup"><span data-stu-id="618be-115">Click **Add Project Data Source** to connect to data and create a data source.</span></span>

4. <span data-ttu-id="618be-116">Na stronie powitalnej **Kreatora konfiguracji źródła danych** kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="618be-116">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>

5. <span data-ttu-id="618be-117">Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych**.</span><span class="sxs-lookup"><span data-stu-id="618be-117">On the **Choose a Data Source Type** page, select **Database**.</span></span>

6. <span data-ttu-id="618be-118">Na stronie **Wybierz połączenie danych** wybierz połączenie danych z listy dostępnych połączeń.</span><span class="sxs-lookup"><span data-stu-id="618be-118">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="618be-119">Jeśli żądane połączenie danych nie jest dostępne wybierz pozycję **nowe połączenie** , aby utworzyć nowe połączenie danych.</span><span class="sxs-lookup"><span data-stu-id="618be-119">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>

7. <span data-ttu-id="618be-120">Wybierz opcję **tak, Zapisz połączenie,** aby zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="618be-120">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>

8. <span data-ttu-id="618be-121">Wybierz obiekty bazy danych do dołączenia do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="618be-121">Select the database objects to bring into your application.</span></span> <span data-ttu-id="618be-122">W takim przypadku wybierz pole w tabeli, które <xref:System.Windows.Forms.TextBox> ma być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="618be-122">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>

9. <span data-ttu-id="618be-123">W razie potrzeby Zastąp domyślną nazwę zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="618be-123">Replace the default dataset name if you want.</span></span>

10. <span data-ttu-id="618be-124">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="618be-124">Click **Finish**.</span></span>

11. <span data-ttu-id="618be-125">W oknie **Właściwości** kliknij strzałkę obok tej <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="618be-125">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="618be-126">W edytorze typów interfejsu użytkownika **źródła danych** wybierz nazwę pola, do którego <xref:System.Windows.Forms.TextBox> ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="618be-126">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>

     <span data-ttu-id="618be-127">Edytor typów interfejsu użytkownika **źródła** danych zostanie zamknięty, a zestaw <xref:System.Windows.Forms.BindingSource> danych, a karta tabeli dla tego połączenia danych jest dodawana do formularza.</span><span class="sxs-lookup"><span data-stu-id="618be-127">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>

## <a name="see-also"></a><span data-ttu-id="618be-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="618be-128">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="618be-129">Dodawanie nowych źródeł danych</span><span class="sxs-lookup"><span data-stu-id="618be-129">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- <span data-ttu-id="618be-130">[Okno źródeł danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="618be-130">[Data Sources Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span></span>
