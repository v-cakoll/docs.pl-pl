---
title: "Porady: powiązywanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18e89d0a236d3b370c521b73dfb640a09137a5dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="0edf6-102">Porady: powiązywanie kontrolek formularzy systemu Windows ze składnikiem BindingSource przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="0edf6-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="0edf6-103">Po dodaniu formantów do formularza i ustalić interfejsu użytkownika dla aplikacji, kontrolki można powiązać źródła danych tak, aby w czasie wykonywania, użytkownicy mogą zmieniać i zapisywać danych związanych z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="0edf6-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>  
  
 <span data-ttu-id="0edf6-104">Powiązanie formantu lub serii formantów w formularzach systemu Windows najłatwiej odbywa się przy użyciu <xref:System.Windows.Forms.BindingSource> formant jako mostka między formantami formularza i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0edf6-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>  
  
 <span data-ttu-id="0edf6-105">Jeden lub więcej formantów w formularzu można powiązać danych. w poniższej procedurze <xref:System.Windows.Forms.TextBox> kontrolka jest powiązana ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="0edf6-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>  
  
 <span data-ttu-id="0edf6-106">Aby ukończyć tę procedurę, zakłada się, że będzie powiązać ze źródłem danych pochodzących z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0edf6-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="0edf6-107">Aby uzyskać więcej informacji na temat tworzenia źródła danych z innych magazynach danych, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="0edf6-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0edf6-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="0edf6-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0edf6-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="0edf6-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0edf6-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="0edf6-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="0edf6-111">Aby powiązać formantu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="0edf6-111">To bind a control at design time</span></span>  
  
1.  <span data-ttu-id="0edf6-112">Przeciągnij <xref:System.Windows.Forms.TextBox> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="0edf6-112">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>  
  
2.  <span data-ttu-id="0edf6-113">W **właściwości** okno:</span><span class="sxs-lookup"><span data-stu-id="0edf6-113">In the **Properties** window:</span></span>  
  
    1.  <span data-ttu-id="0edf6-114">Rozwiń węzeł **(DataBindings)** węzła.</span><span class="sxs-lookup"><span data-stu-id="0edf6-114">Expand the **(DataBindings)** node.</span></span>  
  
    2.  <span data-ttu-id="0edf6-115">Kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0edf6-115">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
         <span data-ttu-id="0edf6-116">**Źródła danych** otwiera edytor typów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0edf6-116">The **DataSource** UI type editor opens.</span></span>  
  
         <span data-ttu-id="0edf6-117">Jeśli wcześniej skonfigurowano źródła danych dla projektu lub formularza, będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="0edf6-117">If a data source has previously been configured for the project or form, it will appear.</span></span>  
  
3.  <span data-ttu-id="0edf6-118">Kliknij przycisk **Dodaj źródło danych projektu** Aby podłączyć się do danych i Utwórz źródło danych.</span><span class="sxs-lookup"><span data-stu-id="0edf6-118">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
4.  <span data-ttu-id="0edf6-119">Na **Kreator konfiguracji źródła danych** stronie powitalnej kliknij **dalej**.</span><span class="sxs-lookup"><span data-stu-id="0edf6-119">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="0edf6-120">Na **wybierz typ źródła danych** wybierz pozycję **bazy danych**.</span><span class="sxs-lookup"><span data-stu-id="0edf6-120">On the **Choose a Data Source Type** page, select **Database**.</span></span>  
  
6.  <span data-ttu-id="0edf6-121">Na **wybierz połączenie danych** wybierz połączenie danych z listy dostępnych połączeń.</span><span class="sxs-lookup"><span data-stu-id="0edf6-121">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="0edf6-122">Jeśli połączenie żądanych danych nie jest dostępne wybierz **nowe połączenie** można utworzyć nowego połączenia danych.</span><span class="sxs-lookup"><span data-stu-id="0edf6-122">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>  
  
7.  <span data-ttu-id="0edf6-123">Wybierz **tak, Zapisz połączenie** Aby zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0edf6-123">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
8.  <span data-ttu-id="0edf6-124">Wybierz obiekty bazy danych do wprowadzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0edf6-124">Select the database objects to bring into your application.</span></span> <span data-ttu-id="0edf6-125">W takim przypadku wybierz pola w tabeli, która będzie <xref:System.Windows.Forms.TextBox> do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="0edf6-125">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>  
  
9. <span data-ttu-id="0edf6-126">Zastąp domyślną nazwę zestawu danych, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="0edf6-126">Replace the default dataset name if you want.</span></span>  
  
10. <span data-ttu-id="0edf6-127">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="0edf6-127">Click **Finish**.</span></span>  
  
11. <span data-ttu-id="0edf6-128">W **właściwości** okna, kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwość ponownie.</span><span class="sxs-lookup"><span data-stu-id="0edf6-128">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="0edf6-129">W **źródła danych** Edytor typów interfejsu użytkownika, wybierz nazwę pola, które można powiązać <xref:System.Windows.Forms.TextBox> do.</span><span class="sxs-lookup"><span data-stu-id="0edf6-129">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>  
  
     <span data-ttu-id="0edf6-130">**Źródła danych** typ interfejsu użytkownika edytora zostanie zamknięty i zestawie danych <xref:System.Windows.Forms.BindingSource> i karty tabeli specyficzne dla czy połączenia danych są dodawane do formularza.</span><span class="sxs-lookup"><span data-stu-id="0edf6-130">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0edf6-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0edf6-131">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="0edf6-132">Dodawanie nowych źródeł danych</span><span class="sxs-lookup"><span data-stu-id="0edf6-132">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)  
 [<span data-ttu-id="0edf6-133">Okno źródła danych</span><span class="sxs-lookup"><span data-stu-id="0edf6-133">Data Sources Window</span></span>](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
