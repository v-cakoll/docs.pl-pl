---
title: "Porady: ustawianie tła panelu formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 451fa6433a53255f5fe45557c2d8b03ac319de71
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="1465c-102">Porady: ustawianie tła panelu formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="1465c-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="1465c-103">Formularze systemu Windows <xref:System.Windows.Forms.Panel> formant może wyświetlać zarówno kolor tła i obraz tła.</span><span class="sxs-lookup"><span data-stu-id="1465c-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="1465c-104"><xref:System.Windows.Forms.Control.BackColor%2A> Właściwość określa kolor tła dla kontrolek, które są zawarte w panelu, takich jak etykiety i przyciski radiowe.</span><span class="sxs-lookup"><span data-stu-id="1465c-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="1465c-105">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie ustawiono właściwości <xref:System.Windows.Forms.Control.BackColor%2A> wyboru spowoduje wypełnienie wszystkich panelu.</span><span class="sxs-lookup"><span data-stu-id="1465c-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="1465c-106">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obrazu będzie wyświetlany za formantów, które są zawarte w panelu.</span><span class="sxs-lookup"><span data-stu-id="1465c-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="1465c-107">Poniższa procedura wymaga **aplikacji systemu Windows** projektu z formularza, który zawiera <xref:System.Windows.Forms.Panel> formantu.</span><span class="sxs-lookup"><span data-stu-id="1465c-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="1465c-108">Informacje dotyczące sposobu konfigurowania tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1465c-108">For information about how to set up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1465c-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="1465c-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1465c-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="1465c-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1465c-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1465c-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="1465c-112">Aby ustawić tła w narzędziu Projektant dla formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1465c-112">To set the background in the Windows Forms Designer</span></span>  
  
1.  <span data-ttu-id="1465c-113">Wybierz <xref:System.Windows.Forms.Panel> formantu.</span><span class="sxs-lookup"><span data-stu-id="1465c-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2.  <span data-ttu-id="1465c-114">W **właściwości** , kliknij strzałkę przycisk Dalej, aby <xref:System.Windows.Forms.Control.BackColor%2A> właściwość, aby wyświetlić okno z trzema kartami.</span><span class="sxs-lookup"><span data-stu-id="1465c-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3.  <span data-ttu-id="1465c-115">Wybierz **niestandardowy** kartę, aby wyświetlić paletę kolorów.</span><span class="sxs-lookup"><span data-stu-id="1465c-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4.  <span data-ttu-id="1465c-116">Wybierz **Web** lub **systemu** karty, aby wyświetlić listę wstępnie zdefiniowane nazwy kolorów, a następnie wybierz kolor.</span><span class="sxs-lookup"><span data-stu-id="1465c-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5.  <span data-ttu-id="1465c-117">W **właściwości** , kliknij strzałkę przycisk Dalej, aby <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1465c-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6.  <span data-ttu-id="1465c-118">W **Otwórz** oknie dialogowym Wybierz plik, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="1465c-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1465c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1465c-119">See Also</span></span>  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [<span data-ttu-id="1465c-120">Panel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="1465c-120">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="1465c-121">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="1465c-121">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="1465c-122">Instrukcje: grupowanie kontrolek za pomocą kontrolki Panel formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="1465c-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
