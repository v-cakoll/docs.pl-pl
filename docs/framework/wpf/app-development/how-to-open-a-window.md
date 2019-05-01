---
title: 'Instrukcje: Otwieranie okna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 9ce7ffb3f46dd869fda7893745b531bd02d18ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947683"
---
# <a name="how-to-open-a-window"></a>Instrukcje: Otwieranie okna
Ten przykład przedstawia sposób otworzyć okno.  
  
## <a name="example"></a>Przykład  
 Okienko jest otwierane przez utworzenie wystąpienia <xref:System.Windows.Window> i wywoływać metodę <xref:System.Windows.Window.Show%2A> metody. <xref:System.Windows.Window.Show%2A> powoduje otwarcie okna i zwraca natychmiast, bez konieczności oczekiwania na nowe okno, aby zamknąć. Tym typie okna jest także znana jako *niemodalne* okna, a nie ogranicza dane wejściowe użytkownika.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Utworzenie wystąpienia <xref:System.Windows.Window> wymaga uprawnień do wywołania metod natywnych unsafe (zobacz <xref:System.Windows.Window.%23ctor%2A>).
