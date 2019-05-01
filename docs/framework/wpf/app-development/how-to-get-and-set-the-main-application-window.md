---
title: 'Instrukcje: Pobieranie i ustawianie okna głównego aplikacji'
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
ms.openlocfilehash: ea8333aa82f1159afb438215940ee1e7c2605e96
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947800"
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="7ddef-102">Instrukcje: Pobieranie i ustawianie okna głównego aplikacji</span><span class="sxs-lookup"><span data-stu-id="7ddef-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="7ddef-103">Ten przykład pokazuje, jak pobieranie i Ustawianie okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7ddef-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ddef-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ddef-104">Example</span></span>  
 <span data-ttu-id="7ddef-105">Pierwszy <xref:System.Windows.Window> , zostanie uruchomiony w ramach Windows Presentation Foundation (WPF) aplikacji jest automatycznie ustawiana przez <xref:System.Windows.Application> jako okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7ddef-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="7ddef-106">Pierwszy <xref:System.Windows.Window> być wystąpieniami będzie najczęściej być okna, który jest określony jako startowy [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (zobacz <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="7ddef-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="7ddef-107">Pierwszy <xref:System.Windows.Window> również mogła zostać utworzona przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="7ddef-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="7ddef-108">Przykładem jest otwarcie okna podczas uruchamiania aplikacji, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="7ddef-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="7ddef-109">Czasami pierwszego wystąpienia <xref:System.Windows.Window> jest rzeczywiście okna głównego aplikacji, np. ekran powitalny.</span><span class="sxs-lookup"><span data-stu-id="7ddef-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="7ddef-110">W takim przypadku można określić w głównym oknie aplikacji przy użyciu znaczników, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="7ddef-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="7ddef-111">Czy okno główne jest określony, automatycznie lub ręcznie, możesz uzyskać głównego okna z <xref:System.Windows.Application.MainWindow%2A> używając następującego kodu, podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="7ddef-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
