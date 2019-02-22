---
title: 'Przewodnik: Wykonywania typowych zadań przy użyciu inteligentnych tagów w Windows Forms, formanty'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 93a477bcaed8ebdc2c7cb4daaa1dce1651cccd12
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664318"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="ab517-102">Przewodnik: Wykonywania typowych zadań przy użyciu inteligentnych tagów w Windows Forms, formanty</span><span class="sxs-lookup"><span data-stu-id="ab517-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="ab517-103">Podczas przygotowywania formularzy i kontrolek dla aplikacji Windows Forms, istnieje wiele zadań, które należy wykonać wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="ab517-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="ab517-104">Oto niektóre z często wykonywanych zadań, które można napotkać:</span><span class="sxs-lookup"><span data-stu-id="ab517-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="ab517-105">Dodawanie lub usuwanie karty na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="ab517-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="ab517-106">Dokowanie formantu do elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ab517-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="ab517-107">Zmiana orientacji <xref:System.Windows.Forms.SplitContainer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ab517-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="ab517-108">Aby przyspieszyć rozwój, wiele kontrolek oferują tagów inteligentnych, które są menu kontekstowe, które pozwalają wykonywać typowe zadania, takie jak te przy użyciu pojedynczego gestu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="ab517-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="ab517-109">Zadania te są nazywane *zleceń tagów inteligentnych*.</span><span class="sxs-lookup"><span data-stu-id="ab517-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="ab517-110">Tagi inteligentne pozostać dołączony do wystąpienia formantu przez cały okres ich istnienia w Projektancie i są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="ab517-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="ab517-111">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="ab517-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="ab517-112">Tworzenie projektu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab517-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="ab517-113">Za pomocą tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="ab517-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="ab517-114">Włączanie i wyłączanie tagi inteligentne</span><span class="sxs-lookup"><span data-stu-id="ab517-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="ab517-115">Gdy skończysz, masz zrozumienia rolę odgrywaną przez te funkcje ważne układu.</span><span class="sxs-lookup"><span data-stu-id="ab517-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab517-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="ab517-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ab517-117">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="ab517-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ab517-118">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ab517-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="ab517-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="ab517-119">Creating the Project</span></span>  
 <span data-ttu-id="ab517-120">Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="ab517-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="ab517-121">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="ab517-121">To create the project</span></span>  
  
1.  <span data-ttu-id="ab517-122">Utwórz projekt aplikacji systemu Windows o nazwie "SmartTagsExample" (**pliku** > **New** > **projektu**  >   **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="ab517-122">Create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="ab517-123">Wybierz formularz w **Windows Forms Designer**.</span><span class="sxs-lookup"><span data-stu-id="ab517-123">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="ab517-124">Za pomocą tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="ab517-124">Using Smart Tags</span></span>  
 <span data-ttu-id="ab517-125">Tagi inteligentne są zawsze dostępne w czasie projektowania dla formantów, które oferują je.</span><span class="sxs-lookup"><span data-stu-id="ab517-125">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="ab517-126">Tagi inteligentne</span><span class="sxs-lookup"><span data-stu-id="ab517-126">To use smart tags</span></span>  
  
1.  <span data-ttu-id="ab517-127">Przeciągnij <xref:System.Windows.Forms.TabControl> z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="ab517-127">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="ab517-128">Należy pamiętać glif tagów inteligentnych (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) wyświetlany na stronie z <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="ab517-128">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="ab517-129">Kliknij symbol tagu inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="ab517-129">Click the smart-tag glyph.</span></span> <span data-ttu-id="ab517-130">W menu skrótów, która pojawia się obok glif, wybierz **Dodaj zakładkę** elementu.</span><span class="sxs-lookup"><span data-stu-id="ab517-130">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="ab517-131">Sprawdź, czy nowa strona karty zostanie dodany do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="ab517-131">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="ab517-132">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="ab517-132">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="ab517-133">Kliknij symbol tagu inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="ab517-133">Click the smart-tag glyph.</span></span> <span data-ttu-id="ab517-134">W menu skrótów, która pojawia się obok glif, wybierz **Dodaj kolumnę** elementu.</span><span class="sxs-lookup"><span data-stu-id="ab517-134">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="ab517-135">Sprawdź, czy nowa kolumna zostanie dodana do <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ab517-135">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="ab517-136">Przeciągnij <xref:System.Windows.Forms.SplitContainer> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="ab517-136">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="ab517-137">Kliknij symbol tagu inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="ab517-137">Click the smart-tag glyph.</span></span> <span data-ttu-id="ab517-138">W menu skrótów, która pojawia się obok glif, wybierz **orientacji poziomej rozdzielacza** elementu.</span><span class="sxs-lookup"><span data-stu-id="ab517-138">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="ab517-139">Zauważ, że <xref:System.Windows.Forms.SplitContainer> pasek podziału kontrolki jest teraz orientacji poziomej.</span><span class="sxs-lookup"><span data-stu-id="ab517-139">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab517-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab517-140">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- <span data-ttu-id="ab517-141">[Przewodnik: Dodawanie tagów inteligentnych do składnika Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="ab517-141">[Walkthrough: Adding Smart Tags to a Windows Forms Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span></span>
