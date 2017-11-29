---
title: "BindingNavigator — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 932223a48500d8a0df5be6ae1ca08e1f333fc711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bindingnavigator-control-overview-windows-forms"></a><span data-ttu-id="bb444-102">BindingNavigator — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="bb444-102">BindingNavigator Control Overview (Windows Forms)</span></span>
<span data-ttu-id="bb444-103">Można użyć <xref:System.Windows.Forms.BindingNavigator> formantu, aby utworzyć standardowych środków użytkownikom wyszukiwanie i zmienić danych na formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb444-103">You can use the <xref:System.Windows.Forms.BindingNavigator> control to create a standardized means for users to search and change data on a Windows Form.</span></span> <span data-ttu-id="bb444-104">Często używane <xref:System.Windows.Forms.BindingNavigator> z <xref:System.Windows.Forms.BindingSource> składnik, aby umożliwić użytkownikom przechodzenie między rekordów danych w formularzu i interakcję z rekordów.</span><span class="sxs-lookup"><span data-stu-id="bb444-104">You frequently use <xref:System.Windows.Forms.BindingNavigator> with the <xref:System.Windows.Forms.BindingSource> component to enable users to move through data records on a form and interact with the records.</span></span>  
  
## <a name="how-the-bindingnavigator-works"></a><span data-ttu-id="bb444-105">Jak działa BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="bb444-105">How the BindingNavigator Works</span></span>  
 <span data-ttu-id="bb444-106"><xref:System.Windows.Forms.BindingNavigator> Kontroli składa się z <xref:System.Windows.Forms.ToolStrip> z serii <xref:System.Windows.Forms.ToolStripItem> obiektów większość typowych akcji związanych z danymi: Dodawanie danych, usuwanie danych ani nawigować przez dane.</span><span class="sxs-lookup"><span data-stu-id="bb444-106">The <xref:System.Windows.Forms.BindingNavigator> control is composed of a <xref:System.Windows.Forms.ToolStrip> with a series of <xref:System.Windows.Forms.ToolStripItem> objects for most of the common data-related actions: adding data, deleting data, and navigating through data.</span></span> <span data-ttu-id="bb444-107">Domyślnie <xref:System.Windows.Forms.BindingNavigator> formant zawiera tych przycisków standardowa.</span><span class="sxs-lookup"><span data-stu-id="bb444-107">By default, the <xref:System.Windows.Forms.BindingNavigator> control contains these standard buttons.</span></span> <span data-ttu-id="bb444-108">Następujący ekran zrzut pokazuje <xref:System.Windows.Forms.BindingNavigator> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="bb444-108">The following screen shot shows the <xref:System.Windows.Forms.BindingNavigator> control on a form.</span></span>  
  
 <span data-ttu-id="bb444-109">![BindingNavigator — kontrolka](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")</span><span class="sxs-lookup"><span data-stu-id="bb444-109">![BindingNavigator Control](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")</span></span>  
  
 <span data-ttu-id="bb444-110">Poniższa tabela zawiera listę formantów oraz opis ich funkcji.</span><span class="sxs-lookup"><span data-stu-id="bb444-110">The following table lists the controls and describes their functions.</span></span>  
  
|<span data-ttu-id="bb444-111">Formant</span><span class="sxs-lookup"><span data-stu-id="bb444-111">Control</span></span>|<span data-ttu-id="bb444-112">Funkcja</span><span class="sxs-lookup"><span data-stu-id="bb444-112">Function</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="bb444-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A>przycisk</span><span class="sxs-lookup"><span data-stu-id="bb444-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> button</span></span>|<span data-ttu-id="bb444-114">Wstawia nowy wiersz w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bb444-114">Inserts a new row into the underlying data source.</span></span>|  
|<span data-ttu-id="bb444-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A>przycisk</span><span class="sxs-lookup"><span data-stu-id="bb444-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button</span></span>|<span data-ttu-id="bb444-116">Usuwa bieżący wiersz w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bb444-116">Deletes the current row from the underlying data source.</span></span>|  
|<span data-ttu-id="bb444-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A>przycisk</span><span class="sxs-lookup"><span data-stu-id="bb444-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button</span></span>|<span data-ttu-id="bb444-118">Przenosi do pierwszego elementu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bb444-118">Moves to the first item in the underlying data source.</span></span>|  
|<span data-ttu-id="bb444-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A>przycisk</span><span class="sxs-lookup"><span data-stu-id="bb444-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> button</span></span>|<span data-ttu-id="bb444-120">Przenosi do ostatniego elementu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bb444-120">Moves to the last item in the underlying data source.</span></span>|  
|<span data-ttu-id="bb444-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A>przycisk</span><span class="sxs-lookup"><span data-stu-id="bb444-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> button</span></span>|<span data-ttu-id="bb444-122">Przechodzi do następnego elementu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bb444-122">Moves to the next item in the underlying data source.</span></span>|  
|<span data-ttu-id="bb444-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A>przycisk</span><span class="sxs-lookup"><span data-stu-id="bb444-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> button</span></span>|<span data-ttu-id="bb444-124">Przenosi do poprzedniego elementu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bb444-124">Moves to the previous item in the underlying data source.</span></span>|  
|<span data-ttu-id="bb444-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A>pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="bb444-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> text box</span></span>|<span data-ttu-id="bb444-126">Zwraca bieżącą pozycję w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bb444-126">Returns the current position within the underlying data source.</span></span>|  
|<span data-ttu-id="bb444-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A>pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="bb444-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A> text box</span></span>|<span data-ttu-id="bb444-128">Zwraca całkowitą liczbę elementów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bb444-128">Returns the total number of items in the underlying data source.</span></span>|  
  
 <span data-ttu-id="bb444-129">Dla każdego formantu w tej kolekcji jest elementem członkowskim odpowiedniego <xref:System.Windows.Forms.BindingSource> składnik, który programowo zapewnia te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="bb444-129">For each control in this collection, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically provides the same functionality.</span></span> <span data-ttu-id="bb444-130">Na przykład <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> przycisk odpowiada <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metody <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> przycisk odpowiada <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> — metoda i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="bb444-130">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span>  
  
 <span data-ttu-id="bb444-131">Jeśli domyślnych przycisków nie są odpowiednie do aplikacji lub jeśli potrzebujesz dodatkowych przycisków do obsługi innych funkcji, możesz podać własne <xref:System.Windows.Forms.ToolStrip> przycisków.</span><span class="sxs-lookup"><span data-stu-id="bb444-131">If the default buttons are not suited to your application, or if you require additional buttons to support other types of functionality, you can supply your own <xref:System.Windows.Forms.ToolStrip> buttons.</span></span> <span data-ttu-id="bb444-132">Zobacz też [porady: Dodawanie obciążenia, Zapisz i Anuluj przycisków do formantu BindingNavigator formularzy systemu Windows](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="bb444-132">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb444-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb444-133">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="bb444-134">BindingNavigator — formant</span><span class="sxs-lookup"><span data-stu-id="bb444-134">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
