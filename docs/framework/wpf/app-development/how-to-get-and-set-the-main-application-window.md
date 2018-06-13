---
title: 'Porady: pobieranie i ustawianie w głównym oknie aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
ms.openlocfilehash: ae70b482eba8fb4e0bf587def06bb90d751a4312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547985"
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="98641-102">Porady: pobieranie i ustawianie w głównym oknie aplikacji</span><span class="sxs-lookup"><span data-stu-id="98641-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="98641-103">W tym przykładzie pokazano, jak pobrać i ustawić w głównym oknie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98641-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98641-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="98641-104">Example</span></span>  
 <span data-ttu-id="98641-105">Pierwszy <xref:System.Windows.Window> który zostanie uruchomiony w systemie Windows Presentation Foundation (WPF) aplikacji zostanie automatycznie ustawione przez <xref:System.Windows.Application> jako okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98641-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="98641-106">Pierwszy <xref:System.Windows.Window> być skonkretyzowanym najprawdopodobniej będzie można okna jest określony jako początkową [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (zobacz <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="98641-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="98641-107">Pierwszy <xref:System.Windows.Window> również mogła zostać utworzona przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="98641-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="98641-108">Przykładem jest otwarcie okna podczas uruchamiania aplikacji, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="98641-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="98641-109">Czasami pierwszego wystąpienia <xref:System.Windows.Window> jest rzeczywiście w głównym oknie aplikacji, np. ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="98641-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="98641-110">W takim przypadku można określić w głównym oknie aplikacji przy użyciu znaczników, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="98641-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="98641-111">Czy okno główne określono automatycznie lub ręcznie, możesz uzyskać okno główne z <xref:System.Windows.Application.MainWindow%2A> przy użyciu następującego kodu, podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="98641-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
