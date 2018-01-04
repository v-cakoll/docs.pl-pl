---
title: 'Porady: otwieranie okna'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6f3efda8257d9f7ed843438b0e9fb42e13de2c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-window"></a>Porady: otwieranie okna
Ten przykład przedstawia sposób otwierania okna.  
  
## <a name="example"></a>Przykład  
 Okno jest otwarty przez utworzenie wystąpienia <xref:System.Windows.Window> i wywoływania <xref:System.Windows.Window.Show%2A> metody. <xref:System.Windows.Window.Show%2A>Otwiera okno i zwraca natychmiast bez oczekiwania na nowe okno, aby zamknąć. Okno tego typu jest nazywana *niemodalne* okna i nie stanowi ograniczenia danych wejściowych użytkownika.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Tworzenie wystąpień <xref:System.Windows.Window> wymaga uprawnienia do wywoływania metod natywnych unsafe (zobacz <xref:System.Windows.Window.%23ctor%2A>).
