---
title: 'Instrukcje: Otwórz okno dialogowe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 0ed41d212eee74d0c3eed1d3341d64a6abc876a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638148"
---
# <a name="how-to-open-a-dialog-box"></a>Instrukcje: Otwórz okno dialogowe
Ten przykład przedstawia sposób otworzyć okno dialogowe.  
  
## <a name="example"></a>Przykład  
 Okno dialogowe jest oknem, która została otwarta przez utworzenie wystąpienia <xref:System.Windows.Window> i wywoływać metodę <xref:System.Windows.Window.ShowDialog%2A> metody. <xref:System.Windows.Window.ShowDialog%2A> Otwiera okno i nie zwraca, aż nowe okno dialogowe zostało zamknięte. Ten typ okna jest także znana jako *modalne* oknie oraz ogranicza dane wejściowe użytkownika.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywoływanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnień do używania wszystkich okien i zdarzenia wejściowe użytkownika bez ograniczeń.  
  
## <a name="see-also"></a>Zobacz także
- [Zwracanie wyniku okna dialogowego](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
