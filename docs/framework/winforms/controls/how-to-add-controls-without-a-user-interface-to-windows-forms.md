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
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987085"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="c36d8-102">Instrukcje: dodawanie kontrolek bez interfejsu użytkownika do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c36d8-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>

<span data-ttu-id="c36d8-103">Niewizualny formant (lub składnik) zapewnia funkcjonalność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c36d8-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="c36d8-104">W przeciwieństwie do innych kontrolek składniki nie udostępniają użytkownikowi interfejsu użytkownika, więc nie muszą być wyświetlane na powierzchni Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c36d8-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="c36d8-105">Po dodaniu składnika do formularza Projektant formularzy systemu Windows wyświetla zasobnik o zmiennym rozmiarze w dolnej części formularza, w którym są wyświetlane wszystkie składniki.</span><span class="sxs-lookup"><span data-stu-id="c36d8-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="c36d8-106">Po dodaniu kontrolki do zasobnika składników można wybrać składnik i ustawić jego właściwości, tak jak każda inna kontrolka w formularzu.</span><span class="sxs-lookup"><span data-stu-id="c36d8-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>

## <a name="add-a-component-to-a-windows-form"></a><span data-ttu-id="c36d8-107">Dodawanie składnika do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c36d8-107">Add a component to a Windows Form</span></span>

1. <span data-ttu-id="c36d8-108">Otwórz formularz w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c36d8-108">Open the form in Visual Studio.</span></span> <span data-ttu-id="c36d8-109">Aby uzyskać szczegółowe informacje [, zobacz How to: Wyświetl Windows Forms w projektancie](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c36d8-109">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="c36d8-110">W **przyborniku**kliknij składnik i przeciągnij go do formularza.</span><span class="sxs-lookup"><span data-stu-id="c36d8-110">In the **Toolbox**, click a component and drag it to your form.</span></span>

     <span data-ttu-id="c36d8-111">Składnik zostanie wyświetlony na pasku składnika.</span><span class="sxs-lookup"><span data-stu-id="c36d8-111">Your component appears in the component tray.</span></span>

<span data-ttu-id="c36d8-112">Ponadto składniki mogą być dodawane do formularza w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c36d8-112">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="c36d8-113">Jest to typowy scenariusz, szczególnie ze względu na to, że składniki nie mają wyrażenia wizualnego, w przeciwieństwie do kontrolek, które mają interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c36d8-113">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="c36d8-114">W poniższym <xref:System.Windows.Forms.Timer> przykładzie składnik jest dodawany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c36d8-114">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="c36d8-115">(Należy zauważyć, że program Visual Studio zawiera szereg różnych czasomierzy; w tym przypadku należy użyć <xref:System.Windows.Forms.Timer> składnika Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c36d8-115">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="c36d8-116">Aby uzyskać więcej informacji na temat różnych czasomierzy w programie Visual Studio, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="c36d8-116">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>

> [!CAUTION]
> <span data-ttu-id="c36d8-117">Składniki często mają właściwości specyficzne dla kontrolki, które muszą być ustawione, aby składnik działał efektywnie.</span><span class="sxs-lookup"><span data-stu-id="c36d8-117">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="c36d8-118">W przypadku <xref:System.Windows.Forms.Timer> składnika poniżej ustawia się `Interval` właściwość.</span><span class="sxs-lookup"><span data-stu-id="c36d8-118">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="c36d8-119">Należy pamiętać, że podczas dodawania składników do projektu ustawiane są właściwości niezbędne dla tego składnika.</span><span class="sxs-lookup"><span data-stu-id="c36d8-119">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>

## <a name="add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="c36d8-120">Programistyczne Dodawanie składnika do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c36d8-120">Add a component to a Windows Form programmatically</span></span>

1. <span data-ttu-id="c36d8-121">Utwórz wystąpienie <xref:System.Windows.Forms.Timer> klasy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c36d8-121">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>

2. <span data-ttu-id="c36d8-122">Ustaw właściwość `Interval` , aby określić czas między taktami czasomierza.</span><span class="sxs-lookup"><span data-stu-id="c36d8-122">Set the `Interval` property to determine the time between ticks of the timer.</span></span>

3. <span data-ttu-id="c36d8-123">Skonfiguruj inne niezbędne właściwości składnika.</span><span class="sxs-lookup"><span data-stu-id="c36d8-123">Configure any other necessary properties for your component.</span></span>

     <span data-ttu-id="c36d8-124">Poniższy kod przedstawia tworzenie elementu <xref:System.Windows.Forms.Timer> `Interval` z zestawem właściwości.</span><span class="sxs-lookup"><span data-stu-id="c36d8-124">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>

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
    > <span data-ttu-id="c36d8-125">Komputer lokalny może być narażony na zagrożenia bezpieczeństwa przez sieć, odwołując się do złośliwego elementu UserControl.</span><span class="sxs-lookup"><span data-stu-id="c36d8-125">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="c36d8-126">Może to stanowić problem tylko w przypadku złośliwej osoby, która tworzy szkodliwą kontrolkę niestandardową, a następnie nie dodawaj jej do projektu.</span><span class="sxs-lookup"><span data-stu-id="c36d8-126">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="c36d8-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c36d8-127">See also</span></span>

- [<span data-ttu-id="c36d8-128">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c36d8-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="c36d8-129">Instrukcje: Dodawanie formantów do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c36d8-129">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="c36d8-130">Instrukcje: Dodaj kontrolki ActiveX do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c36d8-130">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="c36d8-131">Umieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c36d8-131">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="c36d8-132">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="c36d8-132">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="c36d8-133">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c36d8-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="c36d8-134">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="c36d8-134">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
