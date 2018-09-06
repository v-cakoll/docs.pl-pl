---
title: 'Wskazówki: kopiowanie i wklejanie formantu ElementHost w oddzielnych formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 55b426fbe95bac269183a649ecd839175a8cbdda
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037256"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a><span data-ttu-id="d7800-102">Wskazówki: kopiowanie i wklejanie formantu ElementHost w oddzielnych formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d7800-102">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>
<span data-ttu-id="d7800-103">W tym instruktażu pokazano, jak kopiowanie kontrolki Windows Presentation Foundation (WPF) z jednego formularza Windows na inny.</span><span class="sxs-lookup"><span data-stu-id="d7800-103">This walkthrough shows you how to copy a Windows Presentation Foundation (WPF) control from one Windows Form to another.</span></span>  
  
 <span data-ttu-id="d7800-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="d7800-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="d7800-105">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="d7800-105">Create the project.</span></span>  
  
-   <span data-ttu-id="d7800-106">Kopiowanie kontrolki WPF.</span><span class="sxs-lookup"><span data-stu-id="d7800-106">Copy a WPF Control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7800-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="d7800-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d7800-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="d7800-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d7800-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d7800-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d7800-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d7800-110">Prerequisites</span></span>  
 <span data-ttu-id="d7800-111">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="d7800-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="d7800-112">.</span><span class="sxs-lookup"><span data-stu-id="d7800-112">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d7800-113">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="d7800-113">Creating the Project</span></span>  
 <span data-ttu-id="d7800-114">Pierwszym krokiem jest utworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d7800-114">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7800-115">Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d7800-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d7800-116">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="d7800-116">To create the project</span></span>  
  
-   <span data-ttu-id="d7800-117">Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `CopyElementHost`.</span><span class="sxs-lookup"><span data-stu-id="d7800-117">Create a new Windows Forms Application project in Visual Basic or Visual C# named `CopyElementHost`.</span></span>  
  
## <a name="copying-a-wpf-control"></a><span data-ttu-id="d7800-118">Kopiowanie kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="d7800-118">Copying a WPF Control</span></span>  
 <span data-ttu-id="d7800-119">Po dodaniu kontrolki WPF do projektu, skopiuj go do innych formularzy w projekcie.</span><span class="sxs-lookup"><span data-stu-id="d7800-119">After you add a WPF control to the project, you can copy it to other forms in the project.</span></span>  
  
#### <a name="to-copy-a-wpf-control"></a><span data-ttu-id="d7800-120">Aby skopiować kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="d7800-120">To copy a WPF control</span></span>  
  
1.  <span data-ttu-id="d7800-121">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d7800-121">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="d7800-122">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d7800-122">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="d7800-123">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="d7800-123">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="d7800-124">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="d7800-124">Build the project.</span></span>  
  
3.  <span data-ttu-id="d7800-125">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="d7800-125">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="d7800-126">Z **przybornika**, przeciągnij wystąpienie `UserControl1` na formularz.</span><span class="sxs-lookup"><span data-stu-id="d7800-126">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="d7800-127">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="d7800-127">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
5.  <span data-ttu-id="d7800-128">Za pomocą `elementHost1` zaznaczone, naciśnij klawisze CTRL + C, aby skopiować go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="d7800-128">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
6.  <span data-ttu-id="d7800-129">Dodaj nowy formularz Windows do projektu.</span><span class="sxs-lookup"><span data-stu-id="d7800-129">Add a new Windows Form to the project.</span></span> <span data-ttu-id="d7800-130">Użyj domyślnej nazwy dla typu formularza `Form2`.</span><span class="sxs-lookup"><span data-stu-id="d7800-130">Use the default name for the form type, `Form2`.</span></span>  
  
7.  <span data-ttu-id="d7800-131">Za pomocą `Form2` Otwórz w programie Windows Forms Designer, naciśnij klawisze CTRL + V, aby wkleić kopię `elementHost1` na formularz.</span><span class="sxs-lookup"><span data-stu-id="d7800-131">With `Form2` open in the Windows Forms Designer, press CTRL+V to paste a copy of `elementHost1` onto the form.</span></span>  
  
     <span data-ttu-id="d7800-132">Kontrolki skopiowane jest również określany `elementHost1`, ponieważ jest prywatny pola `Form2` klasy.</span><span class="sxs-lookup"><span data-stu-id="d7800-132">The copied control is also named `elementHost1`, because it is a private field of the `Form2` class.</span></span> <span data-ttu-id="d7800-133">Nie ma żadnych kolizji nazw za pomocą `elementHost1` w `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="d7800-133">There is no name collision with the `elementHost1` in the `Form1` class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7800-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7800-134">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="d7800-135">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d7800-135">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="d7800-136">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="d7800-136">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="d7800-137">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7800-137">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
