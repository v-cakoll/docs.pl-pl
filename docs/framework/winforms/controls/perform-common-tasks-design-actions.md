---
title: Wykonywanie typowych zadań przy użyciu akcji projektanta na kontrolkach
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634884"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a><span data-ttu-id="aece8-102">Przewodnik: wykonywanie typowych zadań przy użyciu akcji projektanta</span><span class="sxs-lookup"><span data-stu-id="aece8-102">Walkthrough: Perform common tasks using designer actions</span></span>

<span data-ttu-id="aece8-103">Podczas konstruowania formularzy i kontrolek dla aplikacji Windows Forms istnieje wiele zadań, które będą wykonywane wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="aece8-103">As you construct forms and controls for your Windows Forms application, there are many tasks you'll perform repeatedly.</span></span> <span data-ttu-id="aece8-104">Na poniższej liście przedstawiono niektóre z najczęściej wykonywanych zadań:</span><span class="sxs-lookup"><span data-stu-id="aece8-104">The following list shows some of the commonly performed tasks you'll come across:</span></span>

- <span data-ttu-id="aece8-105">Dodawanie lub usuwanie karty na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="aece8-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>
- <span data-ttu-id="aece8-106">Dokowanie kontrolki do jej elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="aece8-106">Docking a control to its parent.</span></span>
- <span data-ttu-id="aece8-107">Zmiana orientacji kontrolki <xref:System.Windows.Forms.SplitContainer>.</span><span class="sxs-lookup"><span data-stu-id="aece8-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="aece8-108">Aby przyspieszyć programowanie, wiele formantów oferuje akcje projektanta, które są kontekstowymi menu, które umożliwiają wykonywanie typowych zadań, takich jak te w jednym gestie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="aece8-108">To speed development, many controls offer designer actions, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="aece8-109">Te zadania są nazywane *zleceniami akcji projektanta*.</span><span class="sxs-lookup"><span data-stu-id="aece8-109">These tasks are called *designer actions verbs*.</span></span>

<span data-ttu-id="aece8-110">Akcje projektanta pozostają dołączone do wystąpienia kontroli dla jego okresu istnienia w Projektancie i są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="aece8-110">Designer actions remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="aece8-111">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="aece8-111">Create the project</span></span>

<span data-ttu-id="aece8-112">Pierwszym krokiem jest utworzenie projektu i skonfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="aece8-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="aece8-113">W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie **DesignerActionsExample**.</span><span class="sxs-lookup"><span data-stu-id="aece8-113">In Visual Studio, create a Windows-based application project called **DesignerActionsExample**.</span></span>

2. <span data-ttu-id="aece8-114">Wybierz formularz w **Projektant formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="aece8-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-designer-actions"></a><span data-ttu-id="aece8-115">Korzystanie z akcji projektanta</span><span class="sxs-lookup"><span data-stu-id="aece8-115">Use designer actions</span></span>

<span data-ttu-id="aece8-116">Akcje projektanta są zawsze dostępne w czasie projektowania na kontrolkach, które je oferują.</span><span class="sxs-lookup"><span data-stu-id="aece8-116">Designer actions are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="aece8-117">Przeciągnij <xref:System.Windows.Forms.TabControl> z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="aece8-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="aece8-118">Zwróć uwagę na to, że glif akcji projektanta (![małą czarną strzałką](./media/designer-actions-glyph.gif)) pojawia się po stronie <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="aece8-118">Note the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="aece8-119">Kliknij symbol akcji projektanta.</span><span class="sxs-lookup"><span data-stu-id="aece8-119">Click the designer actions glyph.</span></span> <span data-ttu-id="aece8-120">W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kartę** .</span><span class="sxs-lookup"><span data-stu-id="aece8-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="aece8-121">Zwróć uwagę, że nowa strona karty zostanie dodana do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="aece8-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="aece8-122">Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="aece8-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="aece8-123">Kliknij symbol akcji projektanta.</span><span class="sxs-lookup"><span data-stu-id="aece8-123">Click the designer actions glyph.</span></span> <span data-ttu-id="aece8-124">W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kolumnę** .</span><span class="sxs-lookup"><span data-stu-id="aece8-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="aece8-125">Zwróć uwagę, że nowa kolumna jest dodawana do kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="aece8-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="aece8-126">Przeciągnij kontrolkę <xref:System.Windows.Forms.SplitContainer> z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="aece8-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="aece8-127">Kliknij symbol akcji projektanta.</span><span class="sxs-lookup"><span data-stu-id="aece8-127">Click the designer actions glyph.</span></span> <span data-ttu-id="aece8-128">W menu skrótów, które pojawia się obok glifu, wybierz pozycję **pozioma orientacja rozdzielacza** .</span><span class="sxs-lookup"><span data-stu-id="aece8-128">In the shortcut menu that appears next to the glyph, select the **Horizontal Splitter Orientation** item.</span></span> <span data-ttu-id="aece8-129">Należy zauważyć, że pasek rozdzielacza kontrolki <xref:System.Windows.Forms.SplitContainer> jest teraz zorientowany w poziomie.</span><span class="sxs-lookup"><span data-stu-id="aece8-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="aece8-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aece8-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
