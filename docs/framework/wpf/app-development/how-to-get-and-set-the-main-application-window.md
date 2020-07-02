---
title: 'Instrukcje: pobieranie i Ustawianie głównego okna aplikacji'
description: Postępuj zgodnie z tym przykładem, aby uzyskać i ustawić główne okno aplikacji w aplikacji Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 9bb5bce9b90482796acd8c62e77dc8bd9a850eeb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622682"
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="5a442-103">Instrukcje: pobieranie i Ustawianie głównego okna aplikacji</span><span class="sxs-lookup"><span data-stu-id="5a442-103">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="5a442-104">Ten przykład pokazuje, jak uzyskać i ustawić główne okno aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a442-104">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a442-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a442-105">Example</span></span>  
 <span data-ttu-id="5a442-106">Pierwsze <xref:System.Windows.Window> wystąpienie w aplikacji Windows Presentation Foundation (WPF) jest automatycznie ustawiane przez program <xref:System.Windows.Application> jako główne okno aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a442-106">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="5a442-107">Pierwszy <xref:System.Windows.Window> do utworzenia wystąpienia będzie najprawdopodobniej oknem określonym jako początkowy identyfikator URI (zobacz <xref:System.Windows.Application.StartupUri%2A> ).</span><span class="sxs-lookup"><span data-stu-id="5a442-107">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup uniform resource identifier (URI) (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="5a442-108">Pierwsze <xref:System.Windows.Window> można również utworzyć wystąpienie przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="5a442-108">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="5a442-109">Jeden przykład otwiera okno podczas uruchamiania aplikacji, tak jak w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="5a442-109">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="5a442-110">Czasami pierwsze wystąpienie <xref:System.Windows.Window> nie jest w rzeczywistości głównym oknem aplikacji, np. ekran powitalny.</span><span class="sxs-lookup"><span data-stu-id="5a442-110">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="5a442-111">W takim przypadku można określić główne okno aplikacji przy użyciu znacznika, tak jak poniżej:</span><span class="sxs-lookup"><span data-stu-id="5a442-111">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="5a442-112">Niezależnie od tego, czy okno główne jest określone automatycznie, czy ręcznie, można uzyskać główne okno, <xref:System.Windows.Application.MainWindow%2A> korzystając z poniższego kodu, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="5a442-112">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
