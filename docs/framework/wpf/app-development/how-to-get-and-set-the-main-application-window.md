---
title: 'Porady: pobieranie i ustawianie w głównym oknie aplikacji'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
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
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bdc96c509f88650edd93ba4a7f595e2b161db39
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Porady: pobieranie i ustawianie w głównym oknie aplikacji
W tym przykładzie pokazano, jak pobrać i ustawić w głównym oknie aplikacji.  
  
## <a name="example"></a>Przykład  
 Pierwszy <xref:System.Windows.Window> który zostanie uruchomiony w systemie Windows Presentation Foundation (WPF) aplikacji zostanie automatycznie ustawione przez <xref:System.Windows.Application> jako okna głównego aplikacji. Pierwszy <xref:System.Windows.Window> być skonkretyzowanym najprawdopodobniej będzie można okna jest określony jako początkową [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (zobacz <xref:System.Windows.Application.StartupUri%2A>).  
  
 Pierwszy <xref:System.Windows.Window> również mogła zostać utworzona przy użyciu kodu. Przykładem jest otwarcie okna podczas uruchamiania aplikacji, takie jak następujące:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Czasami pierwszego wystąpienia <xref:System.Windows.Window> jest rzeczywiście w głównym oknie aplikacji, np. ekranu powitalnego. W takim przypadku można określić w głównym oknie aplikacji przy użyciu znaczników, takie jak następujące:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Czy okno główne określono automatycznie lub ręcznie, możesz uzyskać okno główne z <xref:System.Windows.Application.MainWindow%2A> przy użyciu następującego kodu, podobnie do następującej:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
