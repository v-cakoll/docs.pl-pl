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
ms.openlocfilehash: 6eec13ec1bac864376fcdf5417cc4be68f16dd46
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-open-a-window"></a>Porady: otwieranie okna
Ten przykład przedstawia sposób otwierania okna.  
  
## <a name="example"></a>Przykład  
 Okno jest otwarty przez utworzenie wystąpienia <xref:System.Windows.Window> i wywoływania <xref:System.Windows.Window.Show%2A> metody. <xref:System.Windows.Window.Show%2A>Otwiera okno i zwraca natychmiast bez oczekiwania na nowe okno, aby zamknąć. Okno tego typu jest nazywana *niemodalne* okna i nie stanowi ograniczenia danych wejściowych użytkownika.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Tworzenie wystąpień <xref:System.Windows.Window> wymaga uprawnienia do wywoływania metod natywnych unsafe (zobacz <xref:System.Windows.Window.%23ctor%2A>).
