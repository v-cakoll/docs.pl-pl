---
title: Jak utworzyć niestandardowy tryb widoku dla ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243222"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Jak: Tworzenie niestandardowego trybu widoku dla widoku listview

W tym przykładzie pokazano, jak utworzyć tryb niestandardowy <xref:System.Windows.Controls.ListView.View%2A> dla formantu. <xref:System.Windows.Controls.ListView>  
  
## <a name="example"></a>Przykład  
 Należy użyć <xref:System.Windows.Controls.ViewBase> klasy podczas tworzenia widoku niestandardowego dla formantu. <xref:System.Windows.Controls.ListView> Poniższy przykład przedstawia tryb `PlainView` widoku o nazwie, <xref:System.Windows.Controls.ViewBase> który pochodzi od klasy.  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Aby zastosować styl do widoku niestandardowego, <xref:System.Windows.Style> użyj klasy. Poniższy przykład definiuje <xref:System.Windows.Style> tryb `PlainView` widoku dla widoku. W poprzednim przykładzie ten styl jest ustawiany jako wartość właściwości zdefiniowanej <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> dla `PlainView`programu .  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Aby zdefiniować układ danych w trybie <xref:System.Windows.DataTemplate> widoku niestandardowego, należy zdefiniować obiekt. Poniższy przykład <xref:System.Windows.DataTemplate> definiuje, który może służyć do `PlainView` wyświetlania danych w trybie widoku.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 W poniższym <xref:System.Windows.ResourceKey> przykładzie pokazano, `PlainView` jak zdefiniować <xref:System.Windows.DataTemplate> dla trybu widoku, który używa tego, który jest zdefiniowany w poprzednim przykładzie.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 Formant <xref:System.Windows.Controls.ListView> może użyć widoku niestandardowego, jeśli ustawisz <xref:System.Windows.Controls.ListView.View%2A> właściwość na klucz zasobu. W poniższym przykładzie `PlainView` pokazano, jak <xref:System.Windows.Controls.ListView>określić jako tryb widoku dla pliku .  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Aby uzyskać pełną próbkę, zobacz [ListView z wieloma widokami (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) lub [ListView z wieloma widokami (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [— Tematy porad](listview-how-to-topics.md)
- [ListView — omówienie](listview-overview.md)
- [GridView — omówienie](gridview-overview.md)
