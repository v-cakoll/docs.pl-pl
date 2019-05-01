---
title: 'Instrukcje: Znajdowanie elementu TreeViewItem w kontrolce TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: 034ec2e57fb3b6a9b3a81f66f6888a68e2c113d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910536"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Instrukcje: Znajdowanie elementu TreeViewItem w kontrolce TreeView
<xref:System.Windows.Controls.TreeView> Kontrola zapewnia wygodny sposób prezentują dane hierarchiczne. Jeśli Twoje <xref:System.Windows.Controls.TreeView> jest powiązana ze źródłem danych <xref:System.Windows.Controls.TreeView.SelectedItem%2A> właściwość zapewnia wygodny sposób na szybkie pobranie obiektu wybranych danych. Zazwyczaj najlepiej pracować z obiektu źródłowego danych, ale czasami konieczne może być programowe Zmienianie danych zawierające <xref:System.Windows.Controls.TreeViewItem>. Na przykład, konieczne może być programowo rozwiń <xref:System.Windows.Controls.TreeViewItem>, lub wybierz inny element w <xref:System.Windows.Controls.TreeView>.  
  
 Aby znaleźć <xref:System.Windows.Controls.TreeViewItem> zawierającą obiekt danych określonego, musi przechodzić przez każdy poziom <xref:System.Windows.Controls.TreeView>. Elementy w <xref:System.Windows.Controls.TreeView> można także zwirtualizować poprawić wydajność. W przypadku których może być zwirtualizowane elementy, możesz również należy weź pod uwagę <xref:System.Windows.Controls.TreeViewItem> do sprawdzenia, czy zawiera on obiektu danych.  
  
## <a name="example"></a>Przykład  
  
## <a name="description"></a>Opis  
 Następujące przykładowe wyszukiwania <xref:System.Windows.Controls.TreeView> dla określonego obiektu i zwraca obiekt zawierający <xref:System.Windows.Controls.TreeViewItem>. Przykład zapewnia, że każdy <xref:System.Windows.Controls.TreeViewItem> zostanie uruchomiony, tak aby jego elementy podrzędne, które mogą być wyszukiwane. W tym przykładzie działa także w przypadku <xref:System.Windows.Controls.TreeView> nie używa elementów zwirtualizowanych.  
  
> [!NOTE]
>  Poniższy przykład działa w przypadku każdej <xref:System.Windows.Controls.TreeView>, niezależnie od podstawowego modelu danych i wyszukiwań co <xref:System.Windows.Controls.TreeViewItem> aż do znalezienia obiektu. Inna technika, która ma lepszą wydajność jest wyszukiwanie modelu danych dla określonego obiektu, informacje o lokalizacji w hierarchii danych i następnie znajdź odpowiedni <xref:System.Windows.Controls.TreeViewItem> w <xref:System.Windows.Controls.TreeView>. Jednak technika, która ma lepszą wydajność wymaga wiedzy na temat modelu danych i nie mogą być uogólnione dla dowolnej podanej <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Kod  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Poprzedni kod, który opiera się na niestandardowej <xref:System.Windows.Controls.VirtualizingStackPanel> który udostępnia metodę o nazwie `BringIntoView`. Poniższy kod definiuje niestandardową <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Następujące XAML przedstawia sposób tworzenia <xref:System.Windows.Controls.TreeView> , który używa niestandardowego <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Poprawianie wydajności kontrolki TreeView](how-to-improve-the-performance-of-a-treeview.md)
