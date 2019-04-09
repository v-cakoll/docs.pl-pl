---
title: 'Instrukcje: Otwieranie okna dialogowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 70ac31285dd22244b4bd6ad0d188d182eb6e6264
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084990"
---
# <a name="how-to-open-a-dialog-box"></a>Instrukcje: Otwieranie okna dialogowego
Ten przykład przedstawia sposób otworzyć okno dialogowe.  
  
## <a name="example"></a>Przykład  
 Okno dialogowe jest oknem, która została otwarta przez utworzenie wystąpienia <xref:System.Windows.Window> i wywoływać metodę <xref:System.Windows.Window.ShowDialog%2A> metody. <xref:System.Windows.Window.ShowDialog%2A> Otwiera okno i nie zwraca, aż nowe okno dialogowe zostało zamknięte. Ten typ okna jest także znana jako *modalne* oknie oraz ogranicza dane wejściowe użytkownika.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywoływanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnień do używania wszystkich okien i zdarzenia wejściowe użytkownika bez ograniczeń.  
  
## <a name="see-also"></a>Zobacz także

- [Zwracanie wyniku okna dialogowego](how-to-return-a-dialog-box-result.md)
