---
title: Jak znaleźć TreeViewItem w TreeView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: cff931312e6bc6db5ae5f26c0db80ad2f43825f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554758"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Jak znaleźć TreeViewItem w TreeView
<xref:System.Windows.Controls.TreeView> Kontrola zapewnia wygodny sposób wyświetlania danych hierarchicznej. Jeśli Twoje <xref:System.Windows.Controls.TreeView> jest powiązany ze źródłem danych <xref:System.Windows.Controls.TreeView.SelectedItem%2A> właściwość umożliwia dogodny można szybko pobrać obiektu wybranych danych. Zazwyczaj najlepiej pracować z źródłowy obiekt danych, ale niekiedy konieczne może być programowane manipulowania zawierające dane <xref:System.Windows.Controls.TreeViewItem>. Na przykład konieczne może być programowane rozwiń <xref:System.Windows.Controls.TreeViewItem>, lub wybierz inny element w <xref:System.Windows.Controls.TreeView>.  
  
 Aby znaleźć <xref:System.Windows.Controls.TreeViewItem> zawiera obiekt określonych danych, musi przechodzić przez każdy poziom <xref:System.Windows.Controls.TreeView>. Elementy w <xref:System.Windows.Controls.TreeView> można także zwirtualizować w celu zwiększenia wydajności. W przypadku których może zwirtualizowane elementy, można również musi zrealizować <xref:System.Windows.Controls.TreeViewItem> do sprawdzenia, czy zawiera on obiektu danych.  
  
## <a name="example"></a>Przykład  
  
## <a name="description"></a>Opis  
 Następujące przykładowe wyszukiwania <xref:System.Windows.Controls.TreeView> dla określonego obiektu i zwraca obiekt zawierający <xref:System.Windows.Controls.TreeViewItem>. Przykład gwarantuje, że każdy <xref:System.Windows.Controls.TreeViewItem> zostanie uruchomiony, dzięki czemu można przeszukiwać jej elementy podrzędne. W tym przykładzie działa również wtedy, gdy <xref:System.Windows.Controls.TreeView> nie używa elementów wirtualnych.  
  
> [!NOTE]
>  Poniższy przykład działa dla każdego <xref:System.Windows.Controls.TreeView>, niezależnie od tego, czy odpowiedni model danych i wyszukiwań co <xref:System.Windows.Controls.TreeViewItem> aż do znalezienia obiektu. Innej metody, która ma większą wydajność jest wyszukiwanie modelu danych dla określonego obiektu, informacje o lokalizacji w hierarchii danych, a następnie znajdź odpowiadającego <xref:System.Windows.Controls.TreeViewItem> w <xref:System.Windows.Controls.TreeView>. Jednak tę metodę, która ma większą wydajność wymaga znajomości modelu danych i nie można uogólnić dla żadnej podanej <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Kod  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Poprzedni kod zależy od niestandardowego <xref:System.Windows.Controls.VirtualizingStackPanel> która udostępnia metodę o nazwie `BringIntoView`. Poniższy kod definiuje niestandardowe <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Następujące XAML przedstawiono sposób tworzenia <xref:System.Windows.Controls.TreeView> używającej niestandardowego <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Poprawianie wydajności kontrolki TreeView](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
