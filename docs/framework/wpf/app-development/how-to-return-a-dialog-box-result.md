---
title: 'Instrukcje: Zwracanie wyniku okna dialogowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: b574a5bbc08d947371837116915c2fc8c13ec81d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006718"
---
# <a name="how-to-return-a-dialog-box-result"></a>Instrukcje: Zwracanie wyniku okna dialogowego
Ten przykład pokazuje, jak można pobrać wyniku okna dialogowego okna, który jest otwierany, wywołując <xref:System.Windows.Window.ShowDialog%2A>.  
  
## <a name="example"></a>Przykład  
 Przed zamknięciem okna dialogowego, jego <xref:System.Windows.Window.DialogResult%2A> właściwość powinna być ustawiona za pomocą <xref:System.Nullable%601> <xref:System.Boolean> oznacza to, jak użytkownik zamknięte okno dialogowe. Ta wartość jest zwracana przez <xref:System.Windows.Window.ShowDialog%2A> umożliwia kod klienta określić, jak zostało zamknięte okno dialogowe i, w związku z tym, jak Przetwórz wynik.  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A> można ustawić tylko jeśli okno zostało otwarte przez wywołanie metody <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywoływanie <xref:System.Windows.Window.ShowDialog%2A> wymaga uprawnień do używania wszystkich okien i zdarzenia wejściowe użytkownika bez ograniczeń.
