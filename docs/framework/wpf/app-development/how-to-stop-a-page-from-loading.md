---
title: 'Instrukcje: Zatrzymywanie ładowania strony'
ms.date: 03/30/2017
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
ms.openlocfilehash: c5694bb2cb6c618cd84bad3dc893ae3855e44892
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006684"
---
# <a name="how-to-stop-a-page-from-loading"></a><span data-ttu-id="5c575-102">Instrukcje: Zatrzymywanie ładowania strony</span><span class="sxs-lookup"><span data-stu-id="5c575-102">How to: Stop a Page from Loading</span></span>
<span data-ttu-id="5c575-103">W tym przykładzie przedstawiono sposób wywoływania <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> metodę, aby zatrzymać nawigacji do zawartości, zanim została zakończona, pobierania.</span><span class="sxs-lookup"><span data-stu-id="5c575-103">This example shows how to call the <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> method to stop navigation to content before it has finished being downloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c575-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c575-104">Example</span></span>  
 <span data-ttu-id="5c575-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> Zatrzymuje pobieranie żądanej zawartości i powoduje, że <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5c575-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> stops the download of the requested content, and causes the <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> event to be raised.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
