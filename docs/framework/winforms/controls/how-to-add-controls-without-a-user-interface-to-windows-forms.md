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
ms.openlocfilehash: 49bf927085d29b60c1d9cf5d61df3894495349db
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210410"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="0caa6-102">Instrukcje: dodawanie kontrolek bez interfejsu użytkownika do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0caa6-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>

<span data-ttu-id="0caa6-103">Niewizualne kontrolki (lub składnika) zapewnia funkcje aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0caa6-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="0caa6-104">W przeciwieństwie do innych formantów składniki nie udostępniają interfejs użytkownika dla użytkownika i dlatego nie powinny być wyświetlane na powierzchni projektanta formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="0caa6-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="0caa6-105">Po dodaniu składnika do formularza Windows Forms Designer przedstawia o zmiennych rozmiarach na pasku w dolnej części formularza, w którym są wyświetlane wszystkie składniki.</span><span class="sxs-lookup"><span data-stu-id="0caa6-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="0caa6-106">Po dodaniu kontrolki do zasobnika składnika można wybrać składnik i ustaw jego właściwości, tak jak inne kontrolki, w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0caa6-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>

## <a name="add-a-component-to-a-windows-form"></a><span data-ttu-id="0caa6-107">Dodaj składnik do formularza Windows</span><span class="sxs-lookup"><span data-stu-id="0caa6-107">Add a component to a Windows Form</span></span>

1. <span data-ttu-id="0caa6-108">Otwórz formularz w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0caa6-108">Open the form in Visual Studio.</span></span> <span data-ttu-id="0caa6-109">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie formularzy Windows w Projektancie](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0caa6-109">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="0caa6-110">W **przybornika**, kliknij składnik i przeciągnij go do formularza.</span><span class="sxs-lookup"><span data-stu-id="0caa6-110">In the **Toolbox**, click a component and drag it to your form.</span></span>

     <span data-ttu-id="0caa6-111">Składnik jest wyświetlana w zasobniku składnika.</span><span class="sxs-lookup"><span data-stu-id="0caa6-111">Your component appears in the component tray.</span></span>

<span data-ttu-id="0caa6-112">Ponadto składniki można dodać do formularza w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0caa6-112">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="0caa6-113">To typowy scenariusz, szczególnie, ponieważ składniki nie mają visual wyrażenia, w przeciwieństwie do formantów, które mają interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0caa6-113">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="0caa6-114">W poniższym przykładzie <xref:System.Windows.Forms.Timer> składnik zostanie dodany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0caa6-114">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="0caa6-115">(Należy pamiętać, że program Visual Studio zawiera szereg różnych czasomierzy; w przypadku używania formularzy Windows <xref:System.Windows.Forms.Timer> składnika.</span><span class="sxs-lookup"><span data-stu-id="0caa6-115">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="0caa6-116">Aby uzyskać więcej informacji na temat różnych czasomierzy w programie Visual Studio, zobacz [wprowadzenie do serwerowych czasomierzy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="0caa6-116">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>

> [!CAUTION]
> <span data-ttu-id="0caa6-117">Składniki często mają właściwości specyficzne dla kontrolki, które muszą być ustawione dla składnika działał efektywnie.</span><span class="sxs-lookup"><span data-stu-id="0caa6-117">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="0caa6-118">W przypadku właściwości <xref:System.Windows.Forms.Timer> poniżej składnika, ustawić `Interval` właściwości.</span><span class="sxs-lookup"><span data-stu-id="0caa6-118">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="0caa6-119">Pamiętaj, podczas dodawania składników do projektu, należy ustawić właściwości niezbędne do tego składnika.</span><span class="sxs-lookup"><span data-stu-id="0caa6-119">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>

## <a name="add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="0caa6-120">Dodaj składnik do formularza Windows programowe</span><span class="sxs-lookup"><span data-stu-id="0caa6-120">Add a component to a Windows Form programmatically</span></span>

1. <span data-ttu-id="0caa6-121">Utwórz wystąpienie obiektu <xref:System.Windows.Forms.Timer> klasy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0caa6-121">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>

2. <span data-ttu-id="0caa6-122">Ustaw `Interval` właściwości, aby ustalić czas między taktami czasomierza.</span><span class="sxs-lookup"><span data-stu-id="0caa6-122">Set the `Interval` property to determine the time between ticks of the timer.</span></span>

3. <span data-ttu-id="0caa6-123">Skonfiguruj inne wymagane właściwości składnika.</span><span class="sxs-lookup"><span data-stu-id="0caa6-123">Configure any other necessary properties for your component.</span></span>

     <span data-ttu-id="0caa6-124">Poniższy kod ilustruje tworzenie <xref:System.Windows.Forms.Timer> z jego `Interval` zestawu właściwości.</span><span class="sxs-lookup"><span data-stu-id="0caa6-124">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>

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
    > <span data-ttu-id="0caa6-125">Na komputerze lokalnym to zagrożenie bezpieczeństwa, za pośrednictwem sieci może narazić, odwołując się do złośliwego elementu UserControl.</span><span class="sxs-lookup"><span data-stu-id="0caa6-125">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="0caa6-126">Powinien to być jedynie kwestią w przypadku złośliwe osoby tworzącej szkodliwe kontrolka niestandardowa, a następnie przez Ciebie przez pomyłkę dodawania do projektu.</span><span class="sxs-lookup"><span data-stu-id="0caa6-126">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="0caa6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0caa6-127">See also</span></span>

- [<span data-ttu-id="0caa6-128">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0caa6-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="0caa6-129">Instrukcje: Dodawanie formantów do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0caa6-129">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="0caa6-130">Instrukcje: Dodawanie kontrolek ActiveX do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0caa6-130">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="0caa6-131">Instrukcje: Kopiowanie formantów pomiędzy formularzami Windows</span><span class="sxs-lookup"><span data-stu-id="0caa6-131">How to: Copy Controls Between Windows Forms</span></span>](how-to-copy-controls-between-windows-forms.md)
- [<span data-ttu-id="0caa6-132">Umieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0caa6-132">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="0caa6-133">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="0caa6-133">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="0caa6-134">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0caa6-134">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="0caa6-135">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="0caa6-135">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
