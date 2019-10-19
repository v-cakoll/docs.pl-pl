---
title: 'Instrukcje: pobieranie i Ustawianie głównego okna aplikacji'
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
ms.openlocfilehash: 5894761c4b6258cbf90d369a722ffc5abca51885
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582557"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Instrukcje: pobieranie i Ustawianie głównego okna aplikacji
Ten przykład pokazuje, jak uzyskać i ustawić główne okno aplikacji.  
  
## <a name="example"></a>Przykład  
 Pierwsze <xref:System.Windows.Window>, które są tworzone w ramach aplikacji Windows Presentation Foundation (WPF), są automatycznie ustawiane przez <xref:System.Windows.Application> jako główne okno aplikacji. Pierwszy <xref:System.Windows.Window>, który ma zostać utworzony, będzie prawdopodobnie oknem określonym jako początkowy identyfikator URI (zobacz <xref:System.Windows.Application.StartupUri%2A>).  
  
 Pierwsze <xref:System.Windows.Window> można również utworzyć przy użyciu kodu. Jeden przykład otwiera okno podczas uruchamiania aplikacji, tak jak w następujących przypadkach:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Czasami pierwsze wystąpienie <xref:System.Windows.Window> nie jest faktycznie głównym oknem aplikacji, na przykład ekran powitalny. W takim przypadku można określić główne okno aplikacji przy użyciu znacznika, tak jak poniżej:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Niezależnie od tego, czy okno główne jest określone automatycznie, czy ręcznie, można uzyskać główne okno z <xref:System.Windows.Application.MainWindow%2A> przy użyciu poniższego kodu, takiego jak następujące:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
