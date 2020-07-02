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
# <a name="how-to-get-and-set-the-main-application-window"></a>Instrukcje: pobieranie i Ustawianie głównego okna aplikacji
Ten przykład pokazuje, jak uzyskać i ustawić główne okno aplikacji.  
  
## <a name="example"></a>Przykład  
 Pierwsze <xref:System.Windows.Window> wystąpienie w aplikacji Windows Presentation Foundation (WPF) jest automatycznie ustawiane przez program <xref:System.Windows.Application> jako główne okno aplikacji. Pierwszy <xref:System.Windows.Window> do utworzenia wystąpienia będzie najprawdopodobniej oknem określonym jako początkowy identyfikator URI (zobacz <xref:System.Windows.Application.StartupUri%2A> ).  
  
 Pierwsze <xref:System.Windows.Window> można również utworzyć wystąpienie przy użyciu kodu. Jeden przykład otwiera okno podczas uruchamiania aplikacji, tak jak w następujących przypadkach:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Czasami pierwsze wystąpienie <xref:System.Windows.Window> nie jest w rzeczywistości głównym oknem aplikacji, np. ekran powitalny. W takim przypadku można określić główne okno aplikacji przy użyciu znacznika, tak jak poniżej:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Niezależnie od tego, czy okno główne jest określone automatycznie, czy ręcznie, można uzyskać główne okno, <xref:System.Windows.Application.MainWindow%2A> korzystając z poniższego kodu, takiego jak:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
