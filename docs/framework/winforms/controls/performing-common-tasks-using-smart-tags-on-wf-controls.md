---
title: 'Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015766"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="4a48b-102">Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="4a48b-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="4a48b-103">Podczas konstruowania formularzy i kontrolek dla aplikacji Windows Forms istnieje wiele zadań, które będą wykonywane wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="4a48b-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="4a48b-104">Poniżej przedstawiono niektóre z najczęściej wykonywanych zadań:</span><span class="sxs-lookup"><span data-stu-id="4a48b-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="4a48b-105">Dodawanie lub usuwanie karty w <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="4a48b-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="4a48b-106">Dokowanie kontrolki do jej elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4a48b-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="4a48b-107">Zmiana orientacji <xref:System.Windows.Forms.SplitContainer> formantu.</span><span class="sxs-lookup"><span data-stu-id="4a48b-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="4a48b-108">Aby przyspieszyć programowanie, wiele formantów oferuje Tagi inteligentne, które są menu kontekstowe, które umożliwiają wykonywanie typowych zadań, takich jak te w jednym gestie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="4a48b-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="4a48b-109">Te zadania są nazywane *czasownikami tagów inteligentnych*.</span><span class="sxs-lookup"><span data-stu-id="4a48b-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="4a48b-110">Tagi inteligentne pozostają dołączone do wystąpienia kontroli dla jego okresu istnienia w Projektancie i są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="4a48b-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="4a48b-111">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="4a48b-111">Create the project</span></span>

<span data-ttu-id="4a48b-112">Pierwszym krokiem jest utworzenie projektu i skonfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="4a48b-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="4a48b-113">W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie **SmartTagsExample**.</span><span class="sxs-lookup"><span data-stu-id="4a48b-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="4a48b-114">Wybierz formularz w **Projektant formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="4a48b-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="4a48b-115">Użyj tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="4a48b-115">Use smart tags</span></span>

<span data-ttu-id="4a48b-116">Tagi inteligentne są zawsze dostępne w czasie projektowania na kontrolkach, które je oferują.</span><span class="sxs-lookup"><span data-stu-id="4a48b-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="4a48b-117">Przeciągnij z <xref:System.Windows.Forms.TabControl> przybornika do formularza.</span><span class="sxs-lookup"><span data-stu-id="4a48b-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="4a48b-118">Zanotuj symbol inteligentny (![symbol](./media/vs-winformsmttagglyph.gif)tagu inteligentnego), który pojawia się po stronie <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="4a48b-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="4a48b-119">Kliknij symbol inteligentny-tag.</span><span class="sxs-lookup"><span data-stu-id="4a48b-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="4a48b-120">W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kartę** .</span><span class="sxs-lookup"><span data-stu-id="4a48b-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="4a48b-121">Zwróć uwagę, że nowa strona karty jest dodawana <xref:System.Windows.Forms.TabControl>do.</span><span class="sxs-lookup"><span data-stu-id="4a48b-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="4a48b-122">Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="4a48b-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="4a48b-123">Kliknij symbol inteligentny-tag.</span><span class="sxs-lookup"><span data-stu-id="4a48b-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="4a48b-124">W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kolumnę** .</span><span class="sxs-lookup"><span data-stu-id="4a48b-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="4a48b-125">Zwróć uwagę, że nowa kolumna jest dodawana <xref:System.Windows.Forms.TableLayoutPanel> do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4a48b-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="4a48b-126">Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="4a48b-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="4a48b-127">Kliknij symbol inteligentny-tag.</span><span class="sxs-lookup"><span data-stu-id="4a48b-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="4a48b-128">W menu skrótów, które pojawia się obok glifu, wybierz pozycję **pozioma orientacja rozdzielacza** .</span><span class="sxs-lookup"><span data-stu-id="4a48b-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="4a48b-129">Należy zauważyć, <xref:System.Windows.Forms.SplitContainer> że pasek rozdzielacza kontrolki jest teraz zorientowany w poziomie.</span><span class="sxs-lookup"><span data-stu-id="4a48b-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a48b-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a48b-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
