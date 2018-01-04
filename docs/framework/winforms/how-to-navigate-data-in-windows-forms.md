---
title: 'Porady: nawigowanie w danych w formularzach systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d99d794164307cb22c5dfc89d6c9c227aa457a59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-in-windows-forms"></a><span data-ttu-id="155e3-102">Porady: nawigowanie w danych w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="155e3-102">How to: Navigate Data in Windows Forms</span></span>
<span data-ttu-id="155e3-103">W aplikacji Windows, najłatwiejszym sposobem nawigowania rekordy w źródle danych jest powiązać <xref:System.Windows.Forms.BindingSource> składnika do źródła danych, a następnie powiązanie formantów <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="155e3-103">In a Windows application, the easiest way to navigate through records in a data source is to bind a <xref:System.Windows.Forms.BindingSource> component to the data source and then bind controls to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="155e3-104">Można następnie użyć metody wbudowanych nawigacji na <xref:System.Windows.Forms.BindingSource> takich <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> i <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span><span class="sxs-lookup"><span data-stu-id="155e3-104">You can then use the built-in navigation method on the <xref:System.Windows.Forms.BindingSource> such a <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> and <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span></span> <span data-ttu-id="155e3-105">Za pomocą następujących metod dostosuje <xref:System.Windows.Forms.BindingSource.Position%2A> i <xref:System.Windows.Forms.BindingSource.Current%2A> właściwości <xref:System.Windows.Forms.BindingSource> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="155e3-105">Using these methods will adjust the <xref:System.Windows.Forms.BindingSource.Position%2A> and <xref:System.Windows.Forms.BindingSource.Current%2A> properties of the <xref:System.Windows.Forms.BindingSource> appropriately.</span></span> <span data-ttu-id="155e3-106">Możesz również znaleźć elementu i ustawić go jako bieżący element przez ustawienie <xref:System.Windows.Forms.BindingSource.Position%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="155e3-106">You can also find an item and set it as the current item by setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property.</span></span>  
  
### <a name="to-increment-the-position-in-a-data-source"></a><span data-ttu-id="155e3-107">Aby zwiększyć pozycji w źródle danych</span><span class="sxs-lookup"><span data-stu-id="155e3-107">To increment the position in a data source</span></span>  
  
1.  <span data-ttu-id="155e3-108">Ustaw <xref:System.Windows.Forms.BindingSource.Position%2A> właściwość <xref:System.Windows.Forms.BindingSource> powiązane dane pozycja rekordu, aby przejść do.</span><span class="sxs-lookup"><span data-stu-id="155e3-108">Set the <xref:System.Windows.Forms.BindingSource.Position%2A> property of the <xref:System.Windows.Forms.BindingSource> for your bound data to the record position to go to.</span></span> <span data-ttu-id="155e3-109">Poniższy przykład przedstawia przy użyciu <xref:System.Windows.Forms.BindingSource.MoveNext%2A> metody <xref:System.Windows.Forms.BindingSource> przyrost <xref:System.Windows.Forms.BindingSource.Position%2A> właściwości podczas `nextButton` zostanie kliknięty.</span><span class="sxs-lookup"><span data-stu-id="155e3-109">The following example illustrates using the <xref:System.Windows.Forms.BindingSource.MoveNext%2A> method of the <xref:System.Windows.Forms.BindingSource> to increment the <xref:System.Windows.Forms.BindingSource.Position%2A> property when the `nextButton` is clicked.</span></span> <span data-ttu-id="155e3-110"><xref:System.Windows.Forms.BindingSource> Jest skojarzony z `Customers` tabeli zestawu danych `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="155e3-110">The <xref:System.Windows.Forms.BindingSource> is associated with the `Customers` table of a dataset `Northwind`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="155e3-111">Ustawienie <xref:System.Windows.Forms.BindingSource.Position%2A> właściwości na wartość poza pierwszym lub ostatnim rekordzie nie powoduje błąd jako [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie zezwoli na ustaw pozycję na wartość poza granice listy.</span><span class="sxs-lookup"><span data-stu-id="155e3-111">Setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property to a value beyond the first or last record does not result in an error, as the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] will not allow you to set the position to a value outside the bounds of the list.</span></span> <span data-ttu-id="155e3-112">Jeśli jest to ważne w aplikacji, aby dowiedzieć się czy przeszły poza pierwszym lub ostatnim rekordzie obejmują logiki, aby sprawdzić, czy zostanie przekroczona liczba elementów danych.</span><span class="sxs-lookup"><span data-stu-id="155e3-112">If it is important in your application to know whether you have gone past the first or last record, include logic to test whether you will exceed the data element count.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a><span data-ttu-id="155e3-113">Aby sprawdzić, czy przekazanego koniec lub początek</span><span class="sxs-lookup"><span data-stu-id="155e3-113">To check whether you have passed the end or beginning</span></span>  
  
1.  <span data-ttu-id="155e3-114">Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="155e3-114">Create an event handler for the <xref:System.Windows.Forms.BindingSource.PositionChanged> event.</span></span> <span data-ttu-id="155e3-115">W obsłudze można sprawdzić, czy wartość pozycji proponowanych przekroczyła licznik elementów danych rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="155e3-115">In the handler, you can test whether the proposed position value has exceeded the actual data element count.</span></span>  
  
     <span data-ttu-id="155e3-116">Poniższy przykład przedstawia, jak można sprawdzić, czy osiągnięto ostatni element danych.</span><span class="sxs-lookup"><span data-stu-id="155e3-116">The following example illustrates how you can test whether you have reached the last data element.</span></span> <span data-ttu-id="155e3-117">W tym przykładzie jest ostatnim elementem **dalej** przycisk w formularzu jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="155e3-117">In the example, if you are at the last element, the **Next** button on the form is disabled.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="155e3-118">Należy pamiętać, że można zmienić listy Nawigacja w kodzie należy ponownie włączyć **dalej** przycisku, dzięki czemu użytkownicy mogą przeglądać przez cały czas nową listę.</span><span class="sxs-lookup"><span data-stu-id="155e3-118">Be aware that, should you change the list you are navigating in code, you should re-enable the **Next** button, so that users may browse the entire length of the new list.</span></span> <span data-ttu-id="155e3-119">Ponadto należy pamiętać, że powyższe <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzeń dla konkretnych <xref:System.Windows.Forms.BindingSource> pracujesz musi być skojarzony z metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="155e3-119">Additionally, be aware that the above <xref:System.Windows.Forms.BindingSource.PositionChanged> event for the specific <xref:System.Windows.Forms.BindingSource> you are working with needs to be associated with its event-handling method.</span></span> <span data-ttu-id="155e3-120">Poniżej przedstawiono przykład metody obsługi <xref:System.Windows.Forms.BindingSource.PositionChanged> zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="155e3-120">The following is an example of a method for handling the <xref:System.Windows.Forms.BindingSource.PositionChanged> event:</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a><span data-ttu-id="155e3-121">Aby znaleźć element i ustaw go jako bieżący element</span><span class="sxs-lookup"><span data-stu-id="155e3-121">To find an item and set it as the current item</span></span>  
  
1.  <span data-ttu-id="155e3-122">Znajdź rekord, który chcesz ustawić jako bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="155e3-122">Find the record you wish to set as the current item.</span></span> <span data-ttu-id="155e3-123">Można to zrobić za pomocą <xref:System.Windows.Forms.BindingSource.Find%2A> metody <xref:System.Windows.Forms.BindingSource>, jeśli źródło danych implementuje <xref:System.ComponentModel.IBindingList>.</span><span class="sxs-lookup"><span data-stu-id="155e3-123">You can do this using the <xref:System.Windows.Forms.BindingSource.Find%2A> method of the <xref:System.Windows.Forms.BindingSource>, if your data source implements <xref:System.ComponentModel.IBindingList>.</span></span> <span data-ttu-id="155e3-124">Przykładowe dane źródeł, które implementują <xref:System.ComponentModel.IBindingList> są <xref:System.ComponentModel.BindingList%601> i <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="155e3-124">Some examples of data sources that implement <xref:System.ComponentModel.IBindingList> are <xref:System.ComponentModel.BindingList%601> and <xref:System.Data.DataView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="155e3-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="155e3-125">See Also</span></span>  
 [<span data-ttu-id="155e3-126">Źródła danych obsługiwane przez formularze Windows Forms</span><span class="sxs-lookup"><span data-stu-id="155e3-126">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [<span data-ttu-id="155e3-127">Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="155e3-127">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="155e3-128">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="155e3-128">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="155e3-129">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="155e3-129">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
