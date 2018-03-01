---
title: "Porady: dodawanie formantów bez interfejsu użytkownika do formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3abbf931cff9ad459e8c9221f91430ecccefa9cc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="94bc0-102">Porady: dodawanie formantów bez interfejsu użytkownika do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94bc0-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>
<span data-ttu-id="94bc0-103">Niewizualne kontrolki (lub składnik) zapewnia funkcje do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94bc0-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="94bc0-104">W odróżnieniu od innych kontrolek składników nie udostępniają interfejsu użytkownika dla użytkownika i w związku z tym nie trzeba będzie wyświetlany na powierzchni projektanta formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94bc0-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="94bc0-105">Gdy składnik zostanie dodany do formularza, Projektant formularzy systemu Windows wyświetla o zmiennym rozmiarze na pasku w dolnej części formularza, w którym są wyświetlane wszystkie składniki.</span><span class="sxs-lookup"><span data-stu-id="94bc0-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="94bc0-106">Po dodaniu formantu do składnika na pasku zadań, można wybrać składnika i ustawienia swoich właściwości, jak w przypadku innych formantu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="94bc0-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94bc0-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="94bc0-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="94bc0-108">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="94bc0-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="94bc0-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="94bc0-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-component-to-a-windows-form"></a><span data-ttu-id="94bc0-110">Aby dodać składnik do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94bc0-110">To add a component to a Windows Form</span></span>  
  
1.  <span data-ttu-id="94bc0-111">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="94bc0-111">Open the form.</span></span> <span data-ttu-id="94bc0-112">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formularzy systemu Windows w Projektancie](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="94bc0-112">For details, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="94bc0-113">W **przybornika**, kliknij i przeciągnij go do formularza.</span><span class="sxs-lookup"><span data-stu-id="94bc0-113">In the **Toolbox**, click a component and drag it to your form.</span></span>  
  
     <span data-ttu-id="94bc0-114">Składnik zostanie wyświetlona na pasku składnika.</span><span class="sxs-lookup"><span data-stu-id="94bc0-114">Your component appears in the component tray.</span></span>  
  
 <span data-ttu-id="94bc0-115">Ponadto składniki można dodać do formularza w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="94bc0-115">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="94bc0-116">Jest to typowy scenariusz, szczególnie, ponieważ składniki nie ma wyrażenia visual, w przeciwieństwie do formantów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="94bc0-116">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="94bc0-117">W poniższym przykładzie <xref:System.Windows.Forms.Timer> dodawania składnika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="94bc0-117">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="94bc0-118">(Należy pamiętać, że [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zawiera szereg różnych czasomierze; w takim przypadku należy użyć formularzy systemu Windows <xref:System.Windows.Forms.Timer> składnika.</span><span class="sxs-lookup"><span data-stu-id="94bc0-118">(Note that [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="94bc0-119">Aby uzyskać więcej informacji na temat różnych czasomierze w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], zobacz [wprowadzenie do serwerowych czasomierze](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span><span class="sxs-lookup"><span data-stu-id="94bc0-119">For more information about the different timers in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="94bc0-120">Składniki często mają właściwości specyficzne dla kontroli, które muszą być ustawione dla składnika efektywnie działać.</span><span class="sxs-lookup"><span data-stu-id="94bc0-120">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="94bc0-121">W przypadku liczby <xref:System.Windows.Forms.Timer> poniższego składnika, ustawić `Interval` właściwości.</span><span class="sxs-lookup"><span data-stu-id="94bc0-121">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="94bc0-122">Pamiętaj, podczas dodawania składników do projektu, ustawienie właściwości wymagane dla tego składnika.</span><span class="sxs-lookup"><span data-stu-id="94bc0-122">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="94bc0-123">Aby programowo Dodaj składnik do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94bc0-123">To add a component to a Windows Form programmatically</span></span>  
  
1.  <span data-ttu-id="94bc0-124">Utwórz wystąpienie <xref:System.Windows.Forms.Timer> klasy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="94bc0-124">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>  
  
2.  <span data-ttu-id="94bc0-125">Ustaw `Interval` właściwości w celu określenia czasu między taktami czasomierza.</span><span class="sxs-lookup"><span data-stu-id="94bc0-125">Set the `Interval` property to determine the time between ticks of the timer.</span></span>  
  
3.  <span data-ttu-id="94bc0-126">Skonfiguruj inne wymagane właściwości dla składnika.</span><span class="sxs-lookup"><span data-stu-id="94bc0-126">Configure any other necessary properties for your component.</span></span>  
  
     <span data-ttu-id="94bc0-127">Poniższy kod przedstawia tworzenie <xref:System.Windows.Forms.Timer> z jego `Interval` zestawu właściwości.</span><span class="sxs-lookup"><span data-stu-id="94bc0-127">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="94bc0-128">Na komputerze lokalnym zagrożenie bezpieczeństwa w sieci może udostępniać za pomocą odwołań do elementu UserControl złośliwe.</span><span class="sxs-lookup"><span data-stu-id="94bc0-128">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="94bc0-129">Tylko będzie to problemem w przypadku złośliwe osoby tworzenie kontrolkę niestandardową szkodliwy, następuje można przez pomyłkę dodanie go do projektu.</span><span class="sxs-lookup"><span data-stu-id="94bc0-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bc0-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94bc0-130">See Also</span></span>  
 [<span data-ttu-id="94bc0-131">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94bc0-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="94bc0-132">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94bc0-132">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="94bc0-133">Instrukcje: dodawanie kontrolek ActiveX do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94bc0-133">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="94bc0-134">Instrukcje: kopiowanie kontrolek pomiędzy formularzami Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94bc0-134">How to: Copy Controls Between Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [<span data-ttu-id="94bc0-135">Umieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94bc0-135">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="94bc0-136">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="94bc0-136">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="94bc0-137">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94bc0-137">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="94bc0-138">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="94bc0-138">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
