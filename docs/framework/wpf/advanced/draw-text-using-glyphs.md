---
title: Rysuj tekst z użyciem glifów
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: 55bbc50de519d6607a843fcd633f2c07db53109f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141677"
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="e73fa-102">Rysuj tekst z użyciem glifów</span><span class="sxs-lookup"><span data-stu-id="e73fa-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="e73fa-103">W tym temacie wyjaśniono, jak używać niskiego poziomu <xref:System.Windows.Documents.Glyphs> obiektu do wyświetlania tekstu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e73fa-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="e73fa-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e73fa-104">Example</span></span>  
 <span data-ttu-id="e73fa-105">W poniższych przykładach pokazano, jak zdefiniować właściwości <xref:System.Windows.Documents.Glyphs> obiektu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e73fa-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="e73fa-106"><xref:System.Windows.Documents.Glyphs> Obiekt reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e73fa-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="e73fa-107">W przykładach założono, że czcionki Arial Courier New i podzbiory są instalowane w folderze C:\WINDOWS\Fonts, na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e73fa-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="e73fa-108">Ten przykład pokazuje jak zdefiniować inne właściwości <xref:System.Windows.Documents.Glyphs> obiekty w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e73fa-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e73fa-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e73fa-109">See also</span></span>

- [<span data-ttu-id="e73fa-110">Typografia w WPF</span><span class="sxs-lookup"><span data-stu-id="e73fa-110">Typography in WPF</span></span>](typography-in-wpf.md)
