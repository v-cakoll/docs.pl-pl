---
title: 'Instrukcje: Nadaj styl wierszowi w ListView, który implementuje GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 0c8806c399959fdc1466e0839ba469881718092b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361632"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="97fd7-102">Instrukcje: Nadaj styl wierszowi w ListView, który implementuje GridView</span><span class="sxs-lookup"><span data-stu-id="97fd7-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="97fd7-103">W tym przykładzie pokazano, jak styl wierszowi w <xref:System.Windows.Controls.ListView> formant, który implementuje <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> trybu.</span><span class="sxs-lookup"><span data-stu-id="97fd7-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97fd7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="97fd7-104">Example</span></span>  
 <span data-ttu-id="97fd7-105">Można styl wierszowi w <xref:System.Windows.Controls.ListView> kontroli przez ustawienie <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> na <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="97fd7-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="97fd7-106">Ustaw styl dla jego elementów, które są reprezentowane jako <xref:System.Windows.Controls.ListViewItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="97fd7-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="97fd7-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odwołania <xref:System.Windows.Controls.ControlTemplate> obiekty, które są używane do wyświetlania zawartości wiersza.</span><span class="sxs-lookup"><span data-stu-id="97fd7-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="97fd7-108">Pełny przykład, poniższe przykłady są wyodrębniane z, wyświetla zbiór informacji utworu, która jest przechowywana w [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bazy danych.</span><span class="sxs-lookup"><span data-stu-id="97fd7-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="97fd7-109">Każdy utwór w bazie danych znajduje się pole klasyfikacji i wartość tego pola określa sposób wyświetlania wiersz utworu informacji.</span><span class="sxs-lookup"><span data-stu-id="97fd7-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="97fd7-110">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> dla <xref:System.Windows.Controls.ListViewItem> obiekty reprezentujące utworów muzycznych w kolekcji utworu.</span><span class="sxs-lookup"><span data-stu-id="97fd7-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="97fd7-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odwołania <xref:System.Windows.Controls.ControlTemplate> obiekty, które określają sposób wyświetlania wiersz utworu informacji.</span><span class="sxs-lookup"><span data-stu-id="97fd7-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="97fd7-112">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.ControlTemplate> dodająca ciąg tekstowy `"Strongly Recommended"` do wiersza.</span><span class="sxs-lookup"><span data-stu-id="97fd7-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="97fd7-113">Ten szablon jest przywoływany w <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> i wyświetla gdy utwór ocena ma wartość 5 (pięć).</span><span class="sxs-lookup"><span data-stu-id="97fd7-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="97fd7-114"><xref:System.Windows.Controls.ControlTemplate> Obejmuje <xref:System.Windows.Controls.GridViewRowPresenter> obiekt, który układa zawartość wiersza w kolumnach, zgodnie z definicją <xref:System.Windows.Controls.GridView> trybu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="97fd7-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="97fd7-115">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="97fd7-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="97fd7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97fd7-116">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="97fd7-117">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="97fd7-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="97fd7-118">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="97fd7-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="97fd7-119">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="97fd7-119">Styling and Templating</span></span>](styling-and-templating.md)
