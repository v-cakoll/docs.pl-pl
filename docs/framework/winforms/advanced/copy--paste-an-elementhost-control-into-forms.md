---
title: "Wskazówki: kopiowanie i wklejanie formantu ElementHost w oddzielnych formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65882925c6fbe3e9b393b139a937bc9a1f95ed04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a><span data-ttu-id="8dda6-102">Wskazówki: kopiowanie i wklejanie formantu ElementHost w oddzielnych formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8dda6-102">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>
<span data-ttu-id="8dda6-103">Ten przewodnik przedstawia sposób kopiowania kontrolki Windows Presentation Foundation (WPF) z jednego formularza systemu Windows na inny.</span><span class="sxs-lookup"><span data-stu-id="8dda6-103">This walkthrough shows you how to copy a Windows Presentation Foundation (WPF) control from one Windows Form to another.</span></span>  
  
 <span data-ttu-id="8dda6-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="8dda6-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="8dda6-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="8dda6-105">Create the project.</span></span>  
  
-   <span data-ttu-id="8dda6-106">Skopiuj kontrolce WPF.</span><span class="sxs-lookup"><span data-stu-id="8dda6-106">Copy a WPF Control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dda6-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="8dda6-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8dda6-108">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="8dda6-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8dda6-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8dda6-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8dda6-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8dda6-110">Prerequisites</span></span>  
 <span data-ttu-id="8dda6-111">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="8dda6-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="8dda6-112">.</span><span class="sxs-lookup"><span data-stu-id="8dda6-112">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="8dda6-113">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="8dda6-113">Creating the Project</span></span>  
 <span data-ttu-id="8dda6-114">Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8dda6-114">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dda6-115">Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.</span><span class="sxs-lookup"><span data-stu-id="8dda6-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="8dda6-116">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="8dda6-116">To create the project</span></span>  
  
-   <span data-ttu-id="8dda6-117">Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `CopyElementHost`.</span><span class="sxs-lookup"><span data-stu-id="8dda6-117">Create a new Windows Forms Application project in Visual Basic or Visual C# named `CopyElementHost`.</span></span>  
  
## <a name="copying-a-wpf-control"></a><span data-ttu-id="8dda6-118">Kopiowanie kontrolce WPF</span><span class="sxs-lookup"><span data-stu-id="8dda6-118">Copying a WPF Control</span></span>  
 <span data-ttu-id="8dda6-119">Po dodaniu formantu WPF do projektu, skopiuj go do innych formularzy w projekcie.</span><span class="sxs-lookup"><span data-stu-id="8dda6-119">After you add a WPF control to the project, you can copy it to other forms in the project.</span></span>  
  
#### <a name="to-copy-a-wpf-control"></a><span data-ttu-id="8dda6-120">Aby skopiować kontrolce WPF</span><span class="sxs-lookup"><span data-stu-id="8dda6-120">To copy a WPF control</span></span>  
  
1.  <span data-ttu-id="8dda6-121">Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8dda6-121">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="8dda6-122">Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="8dda6-122">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="8dda6-123">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="8dda6-123">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="8dda6-124">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="8dda6-124">Build the project.</span></span>  
  
3.  <span data-ttu-id="8dda6-125">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8dda6-125">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="8dda6-126">Z **przybornika**, przeciągnij wystąpienia `UserControl1` na formularzu.</span><span class="sxs-lookup"><span data-stu-id="8dda6-126">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="8dda6-127">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="8dda6-127">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
5.  <span data-ttu-id="8dda6-128">Z `elementHost1` zaznaczone, naciśnij klawisze CTRL + C, aby skopiować go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="8dda6-128">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
6.  <span data-ttu-id="8dda6-129">Dodaj nowego formularza systemu Windows do projektu.</span><span class="sxs-lookup"><span data-stu-id="8dda6-129">Add a new Windows Form to the project.</span></span> <span data-ttu-id="8dda6-130">Użyj domyślnej nazwy dla typu formularza `Form2`.</span><span class="sxs-lookup"><span data-stu-id="8dda6-130">Use the default name for the form type, `Form2`.</span></span>  
  
7.  <span data-ttu-id="8dda6-131">Z `Form2` Otwórz w narzędziu Projektant dla formularzy systemu Windows, naciśnij klawisze CTRL + V Aby wkleić kopię `elementHost1` na formularzu.</span><span class="sxs-lookup"><span data-stu-id="8dda6-131">With `Form2` open in the Windows Forms Designer, press CTRL+V to paste a copy of `elementHost1` onto the form.</span></span>  
  
     <span data-ttu-id="8dda6-132">Formancie skopiowanego nosi również `elementHost1`, ponieważ jest prywatny pole `Form2` klasy.</span><span class="sxs-lookup"><span data-stu-id="8dda6-132">The copied control is also named `elementHost1`, because it is a private field of the `Form2` class.</span></span> <span data-ttu-id="8dda6-133">Nie istnieje żadne kolizję nazw z `elementHost1` w `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="8dda6-133">There is no name collision with the `elementHost1` in the `Form1` class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dda6-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dda6-134">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="8dda6-135">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="8dda6-135">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="8dda6-136">Korzystanie z formantów WPF</span><span class="sxs-lookup"><span data-stu-id="8dda6-136">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="8dda6-137">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="8dda6-137">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
