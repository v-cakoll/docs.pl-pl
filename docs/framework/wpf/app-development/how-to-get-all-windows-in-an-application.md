---
title: 'Porady: uzyskiwanie wszystkich okien aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 476905899f5f7d573a16ba876c72f28ea34bbf9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545494"
---
# <a name="how-to-get-all-windows-in-an-application"></a>Porady: uzyskiwanie wszystkich okien aplikacji
W tym przykładzie pokazano, jak pobrać wszystkie <xref:System.Windows.Window> obiektów w aplikacji.  
  
## <a name="example"></a>Przykład  
 Co wystąpienia <xref:System.Windows.Window> obiektu, czy jest widoczny czy nie, zostanie automatycznie dodany do kolekcji odwołań do okna, które jest zarządzane przez <xref:System.Windows.Application>i narażonych z <xref:System.Windows.Application.Windows%2A>.  
  
 Można wyliczyć <xref:System.Windows.Application.Windows%2A> można pobrać wszystkich wystąpień systemu windows, używając następującego kodu:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
