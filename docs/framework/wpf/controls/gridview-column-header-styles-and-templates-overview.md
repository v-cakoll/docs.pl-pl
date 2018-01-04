---
title: "Przegląd Style nagłówka kolumn i szablonów GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 996d6d5f531a866d4fc80acc3848cdf264901032
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a><span data-ttu-id="590af-102">Przegląd Style nagłówka kolumn i szablonów GridView</span><span class="sxs-lookup"><span data-stu-id="590af-102">GridView Column Header Styles and Templates Overview</span></span>
<span data-ttu-id="590af-103">To omówienie omówiono kolejność pierwszeństwa dla właściwości, które służy do dostosowywania nagłówka kolumny w <xref:System.Windows.Controls.GridView> tryb widoku <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="590af-103">This overview discusses the order of precedence for properties that you use to customize a column header in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="customizing-a-column-header-in-a-gridview"></a><span data-ttu-id="590af-104">Dostosowywanie nagłówek kolumny w widoku GridView</span><span class="sxs-lookup"><span data-stu-id="590af-104">Customizing a Column Header in a GridView</span></span>  
 <span data-ttu-id="590af-105">Właściwości definiujące zawartość, układ i styl nagłówka kolumny w <xref:System.Windows.Controls.GridView> znajdują się na wielu klas pokrewnych.</span><span class="sxs-lookup"><span data-stu-id="590af-105">The properties that define the content, layout, and style of a column header in a <xref:System.Windows.Controls.GridView> are found on many related classes.</span></span> <span data-ttu-id="590af-106">Niektóre z tych właściwości mają funkcjonalność podobną lub taka sama.</span><span class="sxs-lookup"><span data-stu-id="590af-106">Some of these properties have functionality that is similar or the same.</span></span>  
  
 <span data-ttu-id="590af-107">Wiersze w poniższej tabeli przedstawiono grup właściwości, które wykonują tę samą funkcję.</span><span class="sxs-lookup"><span data-stu-id="590af-107">The rows in the following table show groups of properties that perform the same function.</span></span> <span data-ttu-id="590af-108">Te właściwości można użyć do dostosowywania nagłówków kolumn w <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="590af-108">You can use these properties to customize the column headers in a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="590af-109">Kolejność pierwszeństwa powiązane właściwości jest od prawej do lewej, gdy właściwość w najdalej z prawej kolumnie ma najwyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="590af-109">The order of precedence for related properties is from right to left where the property in the farthest right column has the highest precedence.</span></span> <span data-ttu-id="590af-110">Na przykład jeśli <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> jest ustawiona na <xref:System.Windows.Controls.GridViewColumnHeader> obiektu i <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> jest ustawiony na skojarzonym <xref:System.Windows.Controls.GridViewColumn>, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="590af-110">For example, if a <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> is set on the <xref:System.Windows.Controls.GridViewColumnHeader> object and the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> is set on the associated <xref:System.Windows.Controls.GridViewColumn>, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> takes precedence.</span></span> <span data-ttu-id="590af-111">W tym scenariuszu <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="590af-111">In this scenario, the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> has no effect.</span></span>  
  
 <span data-ttu-id="590af-112">**Powiązane właściwości dla nagłówków kolumn w widoku GridView**</span><span class="sxs-lookup"><span data-stu-id="590af-112">**Related properties for column headers in a GridView**</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="590af-113">**Klasy**</span><span class="sxs-lookup"><span data-stu-id="590af-113">**Classes**</span></span>|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|<span data-ttu-id="590af-114">**Właściwości Menu kontekstowego**</span><span class="sxs-lookup"><span data-stu-id="590af-114">**Context Menu Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|<span data-ttu-id="590af-115">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="590af-115">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|<span data-ttu-id="590af-116">**Etykietka narzędzia**</span><span class="sxs-lookup"><span data-stu-id="590af-116">**ToolTip**</span></span><br /><br /> <span data-ttu-id="590af-117">**Właściwości**</span><span class="sxs-lookup"><span data-stu-id="590af-117">**Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|<span data-ttu-id="590af-118">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="590af-118">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|<span data-ttu-id="590af-119">**Szablon nagłówka**</span><span class="sxs-lookup"><span data-stu-id="590af-119">**Header Template**</span></span><br /><br /> <span data-ttu-id="590af-120">**Właściwości**</span><span class="sxs-lookup"><span data-stu-id="590af-120">**Properties**</span></span>|<span data-ttu-id="590af-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="590af-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<span data-ttu-id="590af-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="590af-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<span data-ttu-id="590af-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="590af-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|<span data-ttu-id="590af-124">**Właściwości stylu**</span><span class="sxs-lookup"><span data-stu-id="590af-124">**Style Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <span data-ttu-id="590af-125"><sup>1</sup>dla **właściwości szablonu nagłówka**, jeśli zostanie ustawiona, szablon i właściwości selektor szablonu, pierwszeństwo ma właściwości szablonu.</span><span class="sxs-lookup"><span data-stu-id="590af-125"><sup>1</sup>For **Header Template Properties**, if you set both the template and template selector properties, the template property takes precedence.</span></span> <span data-ttu-id="590af-126">Na przykład, jeśli wartość <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> i <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> właściwości <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwości ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="590af-126">For example, if you set both the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590af-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="590af-127">See Also</span></span>  
 [<span data-ttu-id="590af-128">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="590af-128">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="590af-129">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="590af-129">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="590af-130">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="590af-130">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
