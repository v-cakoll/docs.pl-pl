---
title: 'Instrukcje: dodawanie kontrolek bez interfejsu użytkownika do formularzy systemu Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 90166821181e6562d0bef3ff85f7e7a95c479be0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223696"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="179a7-102">Instrukcje: dodawanie kontrolek bez interfejsu użytkownika do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="179a7-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>
<span data-ttu-id="179a7-103">Niewizualne kontrolki (lub składnika) zapewnia funkcje aplikacji.</span><span class="sxs-lookup"><span data-stu-id="179a7-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="179a7-104">W przeciwieństwie do innych formantów składniki nie udostępniają interfejs użytkownika dla użytkownika i dlatego nie powinny być wyświetlane na powierzchni projektanta formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="179a7-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="179a7-105">Po dodaniu składnika do formularza Windows Forms Designer przedstawia o zmiennych rozmiarach na pasku w dolnej części formularza, w którym są wyświetlane wszystkie składniki.</span><span class="sxs-lookup"><span data-stu-id="179a7-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="179a7-106">Po dodaniu kontrolki do zasobnika składnika można wybrać składnik i ustaw jego właściwości, tak jak inne kontrolki, w formularzu.</span><span class="sxs-lookup"><span data-stu-id="179a7-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="179a7-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="179a7-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="179a7-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="179a7-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="179a7-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="179a7-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-component-to-a-windows-form"></a><span data-ttu-id="179a7-110">Aby dodać składnik do formularza Windows</span><span class="sxs-lookup"><span data-stu-id="179a7-110">To add a component to a Windows Form</span></span>  
  
1.  <span data-ttu-id="179a7-111">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="179a7-111">Open the form.</span></span> <span data-ttu-id="179a7-112">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie formularzy Windows w Projektancie](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="179a7-112">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="179a7-113">W **przybornika**, kliknij składnik i przeciągnij go do formularza.</span><span class="sxs-lookup"><span data-stu-id="179a7-113">In the **Toolbox**, click a component and drag it to your form.</span></span>  
  
     <span data-ttu-id="179a7-114">Składnik jest wyświetlana w zasobniku składnika.</span><span class="sxs-lookup"><span data-stu-id="179a7-114">Your component appears in the component tray.</span></span>  
  
 <span data-ttu-id="179a7-115">Ponadto składniki można dodać do formularza w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="179a7-115">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="179a7-116">To typowy scenariusz, szczególnie, ponieważ składniki nie mają visual wyrażenia, w przeciwieństwie do formantów, które mają interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="179a7-116">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="179a7-117">W poniższym przykładzie <xref:System.Windows.Forms.Timer> składnik zostanie dodany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="179a7-117">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="179a7-118">(Należy pamiętać, że program Visual Studio zawiera szereg różnych czasomierzy; w przypadku używania formularzy Windows <xref:System.Windows.Forms.Timer> składnika.</span><span class="sxs-lookup"><span data-stu-id="179a7-118">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="179a7-119">Aby uzyskać więcej informacji na temat różnych czasomierzy w programie Visual Studio, zobacz [wprowadzenie do serwerowych czasomierzy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="179a7-119">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="179a7-120">Składniki często mają właściwości specyficzne dla kontrolki, które muszą być ustawione dla składnika działał efektywnie.</span><span class="sxs-lookup"><span data-stu-id="179a7-120">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="179a7-121">W przypadku właściwości <xref:System.Windows.Forms.Timer> poniżej składnika, ustawić `Interval` właściwości.</span><span class="sxs-lookup"><span data-stu-id="179a7-121">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="179a7-122">Pamiętaj, podczas dodawania składników do projektu, należy ustawić właściwości niezbędne do tego składnika.</span><span class="sxs-lookup"><span data-stu-id="179a7-122">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="179a7-123">Aby programowo dodać składnik do formularza Windows</span><span class="sxs-lookup"><span data-stu-id="179a7-123">To add a component to a Windows Form programmatically</span></span>  
  
1.  <span data-ttu-id="179a7-124">Utwórz wystąpienie obiektu <xref:System.Windows.Forms.Timer> klasy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="179a7-124">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>  
  
2.  <span data-ttu-id="179a7-125">Ustaw `Interval` właściwości, aby ustalić czas między taktami czasomierza.</span><span class="sxs-lookup"><span data-stu-id="179a7-125">Set the `Interval` property to determine the time between ticks of the timer.</span></span>  
  
3.  <span data-ttu-id="179a7-126">Skonfiguruj inne wymagane właściwości składnika.</span><span class="sxs-lookup"><span data-stu-id="179a7-126">Configure any other necessary properties for your component.</span></span>  
  
     <span data-ttu-id="179a7-127">Poniższy kod ilustruje tworzenie <xref:System.Windows.Forms.Timer> z jego `Interval` zestawu właściwości.</span><span class="sxs-lookup"><span data-stu-id="179a7-127">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>  
  
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
    >  <span data-ttu-id="179a7-128">Na komputerze lokalnym to zagrożenie bezpieczeństwa, za pośrednictwem sieci może narazić, odwołując się do złośliwego elementu UserControl.</span><span class="sxs-lookup"><span data-stu-id="179a7-128">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="179a7-129">Powinien to być jedynie kwestią w przypadku złośliwe osoby tworzącej szkodliwe kontrolka niestandardowa, a następnie przez Ciebie przez pomyłkę dodawania do projektu.</span><span class="sxs-lookup"><span data-stu-id="179a7-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="179a7-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="179a7-130">See also</span></span>

- [<span data-ttu-id="179a7-131">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="179a7-131">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="179a7-132">Instrukcje: dodawanie kontrolek do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="179a7-132">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="179a7-133">Instrukcje: dodawanie kontrolek ActiveX do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="179a7-133">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="179a7-134">Instrukcje: kopiowanie kontrolek pomiędzy formularzami systemu Windows</span><span class="sxs-lookup"><span data-stu-id="179a7-134">How to: Copy Controls Between Windows Forms</span></span>](how-to-copy-controls-between-windows-forms.md)
- [<span data-ttu-id="179a7-135">Umieszczanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="179a7-135">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="179a7-136">Etykietowanie pojedynczych formantów formularzy systemu Windows i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="179a7-136">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="179a7-137">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="179a7-137">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="179a7-138">Formanty formularzy systemu Windows według funkcji</span><span class="sxs-lookup"><span data-stu-id="179a7-138">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
