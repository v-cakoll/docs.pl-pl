---
title: 'Wskazówki: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a558f6d274f260fc91fd140e9dae2c740b1ae00d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="696c2-102">Wskazówki: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="696c2-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="696c2-103">Podczas przygotowywania formularzy i formantów w aplikacji formularzy systemu Windows, istnieje wiele zadań, które będą wykonywane wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="696c2-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="696c2-104">Oto niektóre z najczęściej wykonywanych zadań, które wystąpią:</span><span class="sxs-lookup"><span data-stu-id="696c2-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="696c2-105">Dodawanie lub usuwanie karty na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="696c2-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="696c2-106">Dokowanie formantu do elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="696c2-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="696c2-107">Zmiana orientacji <xref:System.Windows.Forms.SplitContainer> formantu.</span><span class="sxs-lookup"><span data-stu-id="696c2-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="696c2-108">Aby przyspieszyć programowanie, wielu formantów oferują tagi inteligentne, które są menu kontekstowe, które umożliwiają wykonywanie typowych zadań, takich jak te w jednym gestu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="696c2-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="696c2-109">Zadania te są nazywane *zleceń tagów inteligentnych*.</span><span class="sxs-lookup"><span data-stu-id="696c2-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="696c2-110">Tagi inteligentne być dołączony do wystąpienia formantu przez jego okres istnienia w Projektancie i są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="696c2-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="696c2-111">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="696c2-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="696c2-112">Tworzenie projektu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="696c2-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="696c2-113">Z tagami inteligentnymi</span><span class="sxs-lookup"><span data-stu-id="696c2-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="696c2-114">Włączanie i wyłączanie tagi inteligentne</span><span class="sxs-lookup"><span data-stu-id="696c2-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="696c2-115">Gdy skończysz, konieczne będzie zrozumienia rolę odgrywaną przez te funkcje ważne układu.</span><span class="sxs-lookup"><span data-stu-id="696c2-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="696c2-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="696c2-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="696c2-117">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="696c2-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="696c2-118">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="696c2-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="696c2-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="696c2-119">Creating the Project</span></span>  
 <span data-ttu-id="696c2-120">Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="696c2-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="696c2-121">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="696c2-121">To create the project</span></span>  
  
1.  <span data-ttu-id="696c2-122">Utwórz projekt aplikacji systemu Windows o nazwie "SmartTagsExample".</span><span class="sxs-lookup"><span data-stu-id="696c2-122">Create a Windows-based application project called "SmartTagsExample".</span></span> <span data-ttu-id="696c2-123">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="696c2-123">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="696c2-124">Wybierz formularza w **Projektant formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="696c2-124">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="696c2-125">Z tagami inteligentnymi</span><span class="sxs-lookup"><span data-stu-id="696c2-125">Using Smart Tags</span></span>  
 <span data-ttu-id="696c2-126">Tagi inteligentne są zawsze dostępne w czasie projektowania w formantach, które oferują je.</span><span class="sxs-lookup"><span data-stu-id="696c2-126">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="696c2-127">Aby użyć tagi inteligentne</span><span class="sxs-lookup"><span data-stu-id="696c2-127">To use smart tags</span></span>  
  
1.  <span data-ttu-id="696c2-128">Przeciągnij <xref:System.Windows.Forms.TabControl> z **przybornika** na formularzu.</span><span class="sxs-lookup"><span data-stu-id="696c2-128">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="696c2-129">Należy zwrócić uwagę symbolu tagów inteligentnych (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) wyświetlany na stronie z <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="696c2-129">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="696c2-130">Kliknij symbol tagów inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="696c2-130">Click the smart-tag glyph.</span></span> <span data-ttu-id="696c2-131">Wybierz z menu skrótów wyświetlane obok symbolu **Dodaj kartę** elementu.</span><span class="sxs-lookup"><span data-stu-id="696c2-131">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="696c2-132">Sprawdź, czy nowa strona karty została dodana do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="696c2-132">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="696c2-133">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.</span><span class="sxs-lookup"><span data-stu-id="696c2-133">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="696c2-134">Kliknij symbol tagów inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="696c2-134">Click the smart-tag glyph.</span></span> <span data-ttu-id="696c2-135">Wybierz z menu skrótów wyświetlane obok symbolu **Dodaj kolumnę** elementu.</span><span class="sxs-lookup"><span data-stu-id="696c2-135">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="696c2-136">Sprawdź, czy nowa kolumna została dodana do <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="696c2-136">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="696c2-137">Przeciągnij <xref:System.Windows.Forms.SplitContainer> kontrolować z **przybornika** na formularzu.</span><span class="sxs-lookup"><span data-stu-id="696c2-137">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="696c2-138">Kliknij symbol tagów inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="696c2-138">Click the smart-tag glyph.</span></span> <span data-ttu-id="696c2-139">Wybierz z menu skrótów wyświetlane obok symbolu **orientacji poziomej rozdzielacza** elementu.</span><span class="sxs-lookup"><span data-stu-id="696c2-139">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="696c2-140">Że <xref:System.Windows.Forms.SplitContainer> pasek podziału formantu jest teraz orientacji poziomej.</span><span class="sxs-lookup"><span data-stu-id="696c2-140">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696c2-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="696c2-141">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="696c2-142">Wskazówki: Dodawanie tagów inteligentnych do składnika formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="696c2-142">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
