---
title: 'Instrukcje: Pobieranie i Ustawianie okna głównego aplikacji'
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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373559"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Instrukcje: Pobieranie i Ustawianie okna głównego aplikacji
Ten przykład pokazuje, jak pobieranie i Ustawianie okna głównego aplikacji.  
  
## <a name="example"></a>Przykład  
 Pierwszy <xref:System.Windows.Window> , zostanie uruchomiony w ramach Windows Presentation Foundation (WPF) aplikacji jest automatycznie ustawiana przez <xref:System.Windows.Application> jako okna głównego aplikacji. Pierwszy <xref:System.Windows.Window> być wystąpieniami będzie najczęściej być okna, który jest określony jako startowy [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (zobacz <xref:System.Windows.Application.StartupUri%2A>).  
  
 Pierwszy <xref:System.Windows.Window> również mogła zostać utworzona przy użyciu kodu. Przykładem jest otwarcie okna podczas uruchamiania aplikacji, jak pokazano poniżej:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Czasami pierwszego wystąpienia <xref:System.Windows.Window> jest rzeczywiście okna głównego aplikacji, np. ekran powitalny. W takim przypadku można określić w głównym oknie aplikacji przy użyciu znaczników, jak pokazano poniżej:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Czy okno główne jest określony, automatycznie lub ręcznie, możesz uzyskać głównego okna z <xref:System.Windows.Application.MainWindow%2A> używając następującego kodu, podobnie do poniższego:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
