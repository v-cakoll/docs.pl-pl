---
title: 'Instrukcje: Zdefiniuj tabelę przy użyciu XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 7398af6fddae56238e1af3ee4e726420c01ab7ea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376926"
---
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="4624f-102">Instrukcje: Zdefiniuj tabelę przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="4624f-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="4624f-103">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Documents.Table> przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4624f-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="4624f-104">Przykładowa tabela ma cztery kolumny (reprezentowane przez <xref:System.Windows.Documents.TableColumn> elementy) i kilka wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> elementy) zawierające dane, a także jako title, nagłówek i informacje w stopce.</span><span class="sxs-lookup"><span data-stu-id="4624f-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="4624f-105">Wierszy musi być zawarty w <xref:System.Windows.Documents.TableRowGroup> elementu.</span><span class="sxs-lookup"><span data-stu-id="4624f-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="4624f-106">Każdy wiersz w tabeli składa się z co najmniej jedna komórka (reprezentowane przez <xref:System.Windows.Documents.TableCell> elementów).</span><span class="sxs-lookup"><span data-stu-id="4624f-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="4624f-107">Zawartość komórki tabeli muszą być zawarte w <xref:System.Windows.Documents.Block> elementu; w takim przypadku <xref:System.Windows.Documents.Paragraph> elementy są używane.</span><span class="sxs-lookup"><span data-stu-id="4624f-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="4624f-108">Tabela hostuje również hiperłącze (reprezentowane przez <xref:System.Windows.Documents.Hyperlink> elementu) w wierszu stopki.</span><span class="sxs-lookup"><span data-stu-id="4624f-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4624f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="4624f-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="4624f-110">Na poniższej ilustracji przedstawiono, jak renderuje tabeli zdefiniowane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4624f-110">The following figure shows how the table defined in this example renders.</span></span>  
  
 <span data-ttu-id="4624f-111">![Tabela renderowany. ](./media/tableeg.png "TableEG")</span><span class="sxs-lookup"><span data-stu-id="4624f-111">![Rendered table.](./media/tableeg.png "TableEG")</span></span>
