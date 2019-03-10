---
title: 'Przewodnik: Wykonywania typowych zadań przy użyciu inteligentnych tagów w Windows Forms, formanty'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 2805ebc66be5908c333e9a5db41076518ad77c1a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705860"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="2511d-102">Przewodnik: Wykonywania typowych zadań przy użyciu inteligentnych tagów w Windows Forms, formanty</span><span class="sxs-lookup"><span data-stu-id="2511d-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="2511d-103">Podczas przygotowywania formularzy i kontrolek dla aplikacji Windows Forms, istnieje wiele zadań, które należy wykonać wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="2511d-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="2511d-104">Oto niektóre z często wykonywanych zadań, które można napotkać:</span><span class="sxs-lookup"><span data-stu-id="2511d-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="2511d-105">Dodawanie lub usuwanie karty na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="2511d-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="2511d-106">Dokowanie formantu do elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2511d-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="2511d-107">Zmiana orientacji <xref:System.Windows.Forms.SplitContainer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2511d-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="2511d-108">Aby przyspieszyć rozwój, wiele kontrolek oferują tagów inteligentnych, które są menu kontekstowe, które pozwalają wykonywać typowe zadania, takie jak te przy użyciu pojedynczego gestu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="2511d-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="2511d-109">Zadania te są nazywane *zleceń tagów inteligentnych*.</span><span class="sxs-lookup"><span data-stu-id="2511d-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="2511d-110">Tagi inteligentne pozostać dołączony do wystąpienia formantu przez cały okres ich istnienia w Projektancie i są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="2511d-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="2511d-111">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="2511d-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="2511d-112">Tworzenie projektu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2511d-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="2511d-113">Za pomocą tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="2511d-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="2511d-114">Włączanie i wyłączanie tagi inteligentne</span><span class="sxs-lookup"><span data-stu-id="2511d-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="2511d-115">Gdy skończysz, masz zrozumienia rolę odgrywaną przez te funkcje ważne układu.</span><span class="sxs-lookup"><span data-stu-id="2511d-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2511d-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="2511d-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2511d-117">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="2511d-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2511d-118">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="2511d-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="2511d-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="2511d-119">Creating the Project</span></span>  
 <span data-ttu-id="2511d-120">Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="2511d-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="2511d-121">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="2511d-121">To create the project</span></span>  
  
1.  <span data-ttu-id="2511d-122">Utwórz projekt aplikacji systemu Windows o nazwie "SmartTagsExample" (**pliku** > **New** > **projektu**  >   **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="2511d-122">Create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="2511d-123">Wybierz formularz w **Windows Forms Designer**.</span><span class="sxs-lookup"><span data-stu-id="2511d-123">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="2511d-124">Za pomocą tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="2511d-124">Using Smart Tags</span></span>  
 <span data-ttu-id="2511d-125">Tagi inteligentne są zawsze dostępne w czasie projektowania dla formantów, które oferują je.</span><span class="sxs-lookup"><span data-stu-id="2511d-125">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="2511d-126">Tagi inteligentne</span><span class="sxs-lookup"><span data-stu-id="2511d-126">To use smart tags</span></span>  
  
1.  <span data-ttu-id="2511d-127">Przeciągnij <xref:System.Windows.Forms.TabControl> z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="2511d-127">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="2511d-128">Należy pamiętać glif tagów inteligentnych (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) wyświetlany na stronie z <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="2511d-128">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="2511d-129">Kliknij symbol tagu inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="2511d-129">Click the smart-tag glyph.</span></span> <span data-ttu-id="2511d-130">W menu skrótów, która pojawia się obok glif, wybierz **Dodaj zakładkę** elementu.</span><span class="sxs-lookup"><span data-stu-id="2511d-130">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="2511d-131">Sprawdź, czy nowa strona karty zostanie dodany do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="2511d-131">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="2511d-132">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="2511d-132">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="2511d-133">Kliknij symbol tagu inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="2511d-133">Click the smart-tag glyph.</span></span> <span data-ttu-id="2511d-134">W menu skrótów, która pojawia się obok glif, wybierz **Dodaj kolumnę** elementu.</span><span class="sxs-lookup"><span data-stu-id="2511d-134">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="2511d-135">Sprawdź, czy nowa kolumna zostanie dodana do <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2511d-135">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="2511d-136">Przeciągnij <xref:System.Windows.Forms.SplitContainer> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="2511d-136">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="2511d-137">Kliknij symbol tagu inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="2511d-137">Click the smart-tag glyph.</span></span> <span data-ttu-id="2511d-138">W menu skrótów, która pojawia się obok glif, wybierz **orientacji poziomej rozdzielacza** elementu.</span><span class="sxs-lookup"><span data-stu-id="2511d-138">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="2511d-139">Zauważ, że <xref:System.Windows.Forms.SplitContainer> pasek podziału kontrolki jest teraz orientacji poziomej.</span><span class="sxs-lookup"><span data-stu-id="2511d-139">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2511d-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2511d-140">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- <span data-ttu-id="2511d-141">[Przewodnik: Dodawanie tagów inteligentnych do składnika Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="2511d-141">[Walkthrough: Adding Smart Tags to a Windows Forms Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span></span>
