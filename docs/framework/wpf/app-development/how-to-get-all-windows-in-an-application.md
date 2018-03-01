---
title: 'Porady: uzyskiwanie wszystkich okien aplikacji'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fdb1baad8b779b6ef0443a05e5f6575b552b1c19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-all-windows-in-an-application"></a>Porady: uzyskiwanie wszystkich okien aplikacji
W tym przykładzie pokazano, jak pobrać wszystkie <xref:System.Windows.Window> obiektów w aplikacji.  
  
## <a name="example"></a>Przykład  
 Co wystąpienia <xref:System.Windows.Window> obiektu, czy jest widoczny czy nie, zostanie automatycznie dodany do kolekcji odwołań do okna, które jest zarządzane przez <xref:System.Windows.Application>i narażonych z <xref:System.Windows.Application.Windows%2A>.  
  
 Można wyliczyć <xref:System.Windows.Application.Windows%2A> można pobrać wszystkich wystąpień systemu windows, używając następującego kodu:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
