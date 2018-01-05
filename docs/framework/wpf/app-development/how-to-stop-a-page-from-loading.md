---
title: "Porady: zatrzymać ładowanie strony"
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
- pages [WPF], stopping from loading
- methods [WPF], Stoploading
- events [WPF], NavigationStopped
- NavigationStopped properties [WPF]
- stopping pages from loading [WPF]
- loading [WPF], stopping
ms.assetid: e2b695b0-517e-462c-8ccf-90cc8d6ba864
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6109a45f885a6a94a5785329d10bce52a0090802
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-stop-a-page-from-loading"></a><span data-ttu-id="5326a-102">Porady: zatrzymać ładowanie strony</span><span class="sxs-lookup"><span data-stu-id="5326a-102">How to: Stop a Page from Loading</span></span>
<span data-ttu-id="5326a-103">W tym przykładzie przedstawiono sposób wywoływania <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> metodę, aby zatrzymać nawigacji do zawartości, zanim zakończyło się w trakcie pobierania.</span><span class="sxs-lookup"><span data-stu-id="5326a-103">This example shows how to call the <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> method to stop navigation to content before it has finished being downloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5326a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5326a-104">Example</span></span>  
 <span data-ttu-id="5326a-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A>Zatrzymuje pobieranie żądanej zawartości i powoduje, że <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> się zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5326a-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> stops the download of the requested content, and causes the <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> event to be raised.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
