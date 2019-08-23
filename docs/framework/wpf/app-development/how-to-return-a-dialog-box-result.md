---
title: 'Instrukcje: Zwracanie wyniku okna dialogowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 5e3670006762bcd09634b29314ecf2d05b1a44da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968231"
---
# <a name="how-to-return-a-dialog-box-result"></a>Instrukcje: Zwracanie wyniku okna dialogowego
Ten przykład pokazuje, jak pobrać wynik okna dialogowego dla okna, które jest otwierane przez <xref:System.Windows.Window.ShowDialog%2A>wywołanie.  
  
## <a name="example"></a>Przykład  
 Przed zamknięciem okna dialogowego, jego <xref:System.Windows.Window.DialogResult%2A> właściwość powinna być ustawiona <xref:System.Nullable%601> <xref:System.Boolean> z, która wskazuje, jak użytkownik zamknął okno dialogowe. Ta wartość jest zwracana przez <xref:System.Windows.Window.ShowDialog%2A> program, aby umożliwić kodowi klienta ustalenie, jak okno dialogowe zostało zamknięte, i w związku z tym, jak przetworzyć wynik.  
  
> [!NOTE]
> <xref:System.Windows.Window.DialogResult%2A>można ustawić tylko wtedy, gdy okno zostało otwarte przez wywołanie <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywołanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnień do używania wszystkich zdarzeń systemu Windows i danych wejściowych użytkownika bez ograniczeń.
