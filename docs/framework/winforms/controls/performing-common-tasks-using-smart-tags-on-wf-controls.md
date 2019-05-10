---
title: 'Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 1cc854d735ba88a301d6e2f6a83fe5c8bf881380
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211416"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="d0444-102">Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d0444-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>

<span data-ttu-id="d0444-103">Podczas przygotowywania formularzy i kontrolek dla aplikacji Windows Forms, istnieje wiele zadań, które należy wykonać wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="d0444-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="d0444-104">Oto niektóre z często wykonywanych zadań, które można napotkać:</span><span class="sxs-lookup"><span data-stu-id="d0444-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="d0444-105">Dodawanie lub usuwanie karty na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="d0444-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="d0444-106">Dokowanie formantu do elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d0444-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="d0444-107">Zmiana orientacji <xref:System.Windows.Forms.SplitContainer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d0444-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="d0444-108">Aby przyspieszyć rozwój, wiele kontrolek oferują tagów inteligentnych, które są menu kontekstowe, które pozwalają wykonywać typowe zadania, takie jak te przy użyciu pojedynczego gestu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="d0444-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="d0444-109">Zadania te są nazywane *zleceń tagów inteligentnych*.</span><span class="sxs-lookup"><span data-stu-id="d0444-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="d0444-110">Tagi inteligentne pozostać dołączony do wystąpienia formantu przez cały okres ich istnienia w Projektancie i są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="d0444-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

<span data-ttu-id="d0444-111">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="d0444-111">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="d0444-112">Tworzenie projektu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0444-112">Creating a Windows Forms project</span></span>

- <span data-ttu-id="d0444-113">Za pomocą tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="d0444-113">Using smart tags</span></span>

- <span data-ttu-id="d0444-114">Włączanie i wyłączanie tagi inteligentne</span><span class="sxs-lookup"><span data-stu-id="d0444-114">Enabling and Disabling Smart Tags</span></span>

<span data-ttu-id="d0444-115">Gdy skończysz, masz zrozumienia rolę odgrywaną przez te funkcje ważne układu.</span><span class="sxs-lookup"><span data-stu-id="d0444-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="d0444-116">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="d0444-116">Create the project</span></span>

<span data-ttu-id="d0444-117">Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="d0444-117">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="d0444-118">W programie Visual Studio Utwórz projekt aplikacji systemu Windows o nazwie "SmartTagsExample" (**pliku** > **New** > **projektu**  >  **Visual C#**  lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms Aplikacja**).</span><span class="sxs-lookup"><span data-stu-id="d0444-118">In Visual Studio, create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="d0444-119">Wybierz formularz w **Windows Forms Designer**.</span><span class="sxs-lookup"><span data-stu-id="d0444-119">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="d0444-120">Za pomocą tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="d0444-120">Use smart tags</span></span>

<span data-ttu-id="d0444-121">Tagi inteligentne są zawsze dostępne w czasie projektowania dla formantów, które oferują je.</span><span class="sxs-lookup"><span data-stu-id="d0444-121">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="d0444-122">Przeciągnij <xref:System.Windows.Forms.TabControl> z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="d0444-122">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="d0444-123">Należy pamiętać glif tagów inteligentnych (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) wyświetlany na stronie z <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="d0444-123">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="d0444-124">Kliknij symbol tagu inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="d0444-124">Click the smart-tag glyph.</span></span> <span data-ttu-id="d0444-125">W menu skrótów, która pojawia się obok glif, wybierz **Dodaj zakładkę** elementu.</span><span class="sxs-lookup"><span data-stu-id="d0444-125">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="d0444-126">Sprawdź, czy nowa strona karty zostanie dodany do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="d0444-126">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="d0444-127">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="d0444-127">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="d0444-128">Kliknij symbol tagu inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="d0444-128">Click the smart-tag glyph.</span></span> <span data-ttu-id="d0444-129">W menu skrótów, która pojawia się obok glif, wybierz **Dodaj kolumnę** elementu.</span><span class="sxs-lookup"><span data-stu-id="d0444-129">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="d0444-130">Sprawdź, czy nowa kolumna zostanie dodana do <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d0444-130">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="d0444-131">Przeciągnij <xref:System.Windows.Forms.SplitContainer> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="d0444-131">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="d0444-132">Kliknij symbol tagu inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="d0444-132">Click the smart-tag glyph.</span></span> <span data-ttu-id="d0444-133">W menu skrótów, która pojawia się obok glif, wybierz **orientacji poziomej rozdzielacza** elementu.</span><span class="sxs-lookup"><span data-stu-id="d0444-133">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="d0444-134">Zauważ, że <xref:System.Windows.Forms.SplitContainer> pasek podziału kontrolki jest teraz orientacji poziomej.</span><span class="sxs-lookup"><span data-stu-id="d0444-134">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0444-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0444-135">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- <span data-ttu-id="d0444-136">[Przewodnik: Dodawanie tagów inteligentnych do składnika Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="d0444-136">[Walkthrough: Adding Smart Tags to a Windows Forms Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span></span>
