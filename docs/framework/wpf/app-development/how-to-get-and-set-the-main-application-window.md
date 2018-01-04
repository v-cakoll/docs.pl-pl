---
title: "Porady: pobieranie i ustawianie w głównym oknie aplikacji"
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
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9aa02b0d5ff4456cf5ef86fa0d4f8431fe3d846b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="43775-102">Porady: pobieranie i ustawianie w głównym oknie aplikacji</span><span class="sxs-lookup"><span data-stu-id="43775-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="43775-103">W tym przykładzie pokazano, jak pobrać i ustawić w głównym oknie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43775-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43775-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="43775-104">Example</span></span>  
 <span data-ttu-id="43775-105">Pierwszy <xref:System.Windows.Window> który zostanie uruchomiony w ramach [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikacji zostanie automatycznie ustawione <xref:System.Windows.Application> jako okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43775-105">The first <xref:System.Windows.Window> that is instantiated within a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="43775-106">Pierwszy <xref:System.Windows.Window> być skonkretyzowanym najprawdopodobniej będzie można okna jest określony jako początkową [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (zobacz <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="43775-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="43775-107">Pierwszy <xref:System.Windows.Window> również mogła zostać utworzona przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="43775-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="43775-108">Przykładem jest otwarcie okna podczas uruchamiania aplikacji, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="43775-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="43775-109">Czasami pierwszego wystąpienia <xref:System.Windows.Window> jest rzeczywiście w głównym oknie aplikacji, np. ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="43775-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="43775-110">W takim przypadku można określić w głównym oknie aplikacji przy użyciu znaczników, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="43775-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="43775-111">Czy okno główne określono automatycznie lub ręcznie, możesz uzyskać okno główne z <xref:System.Windows.Application.MainWindow%2A> przy użyciu następującego kodu, podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="43775-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
