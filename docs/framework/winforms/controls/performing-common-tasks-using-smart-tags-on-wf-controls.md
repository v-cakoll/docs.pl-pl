---
title: 'Wskazówki: przeprowadzanie typowych zadań z tagami inteligentnymi na formantach formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07fb43a711ae8b1e2e375b17b136c07f35b1cf39
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459575"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="5a085-102">Przewodnik: wykonywanie typowych zadań przy użyciu tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="5a085-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="5a085-103">Podczas konstruowania formularzy i kontrolek dla aplikacji Windows Forms istnieje wiele zadań, które będą wykonywane wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="5a085-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="5a085-104">Poniżej przedstawiono niektóre z najczęściej wykonywanych zadań:</span><span class="sxs-lookup"><span data-stu-id="5a085-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="5a085-105">Dodawanie lub usuwanie karty na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="5a085-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="5a085-106">Dokowanie kontrolki do jej elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5a085-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="5a085-107">Zmiana orientacji kontrolki <xref:System.Windows.Forms.SplitContainer>.</span><span class="sxs-lookup"><span data-stu-id="5a085-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="5a085-108">Aby przyspieszyć programowanie, wiele formantów oferuje Tagi inteligentne, które są menu kontekstowe, które umożliwiają wykonywanie typowych zadań, takich jak te w jednym gestie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="5a085-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="5a085-109">Te zadania są nazywane *czasownikami tagów inteligentnych*.</span><span class="sxs-lookup"><span data-stu-id="5a085-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="5a085-110">Tagi inteligentne pozostają dołączone do wystąpienia kontroli dla jego okresu istnienia w Projektancie i są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="5a085-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="5a085-111">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="5a085-111">Create the project</span></span>

<span data-ttu-id="5a085-112">Pierwszym krokiem jest utworzenie projektu i skonfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="5a085-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="5a085-113">W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie **SmartTagsExample**.</span><span class="sxs-lookup"><span data-stu-id="5a085-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="5a085-114">Wybierz formularz w **Projektant formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="5a085-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="5a085-115">Użyj tagów inteligentnych</span><span class="sxs-lookup"><span data-stu-id="5a085-115">Use smart tags</span></span>

<span data-ttu-id="5a085-116">Tagi inteligentne są zawsze dostępne w czasie projektowania na kontrolkach, które je oferują.</span><span class="sxs-lookup"><span data-stu-id="5a085-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="5a085-117">Przeciągnij <xref:System.Windows.Forms.TabControl> z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="5a085-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="5a085-118">Zanotuj symbol inteligentny-tag (![symbol taga inteligentnego](./media/vs-winformsmttagglyph.gif)), który pojawia się po stronie <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="5a085-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="5a085-119">Kliknij symbol inteligentny-tag.</span><span class="sxs-lookup"><span data-stu-id="5a085-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="5a085-120">W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kartę** .</span><span class="sxs-lookup"><span data-stu-id="5a085-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="5a085-121">Zwróć uwagę, że nowa strona karty zostanie dodana do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="5a085-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="5a085-122">Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="5a085-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="5a085-123">Kliknij symbol inteligentny-tag.</span><span class="sxs-lookup"><span data-stu-id="5a085-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="5a085-124">W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kolumnę** .</span><span class="sxs-lookup"><span data-stu-id="5a085-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="5a085-125">Zwróć uwagę, że nowa kolumna jest dodawana do kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="5a085-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="5a085-126">Przeciągnij kontrolkę <xref:System.Windows.Forms.SplitContainer> z **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="5a085-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="5a085-127">Kliknij symbol inteligentny-tag.</span><span class="sxs-lookup"><span data-stu-id="5a085-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="5a085-128">W menu skrótów, które pojawia się obok glifu, wybierz pozycję **pozioma orientacja rozdzielacza** .</span><span class="sxs-lookup"><span data-stu-id="5a085-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="5a085-129">Należy zauważyć, że pasek rozdzielacza kontrolki <xref:System.Windows.Forms.SplitContainer> jest teraz zorientowany w poziomie.</span><span class="sxs-lookup"><span data-stu-id="5a085-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a085-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a085-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
