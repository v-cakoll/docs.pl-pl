---
title: 'Instrukcje: Poruszanie się wstecz w historii nawigacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 86590c2794339ac22cbc8ec5e11224736133e870
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817974"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Instrukcje: Poruszanie się wstecz w historii nawigacji
Ten przykład ilustruje sposób nawigowania do wpisów w historii nawigacji wstecznej.  
  
## <a name="example"></a>Przykład  
 Kod, który jest uruchamiany z zawartości <xref:System.Windows.Navigation.NavigationWindow>, która jest hostowana w, <xref:System.Windows.Controls.Frame> za pomocą <xref:System.Windows.Navigation.NavigationService>lub Internet Explorer, może nawigować wstecz w historii nawigacji, po jednym wpisie.  
  
 Przechodzenie do tyłu jednego wpisu wymaga wcześniejszego sprawdzenia, czy istnieją wpisy w historii nawigacji wstecznej, sprawdzając Właściwość **CanGoBack** przed przechodzeniem do tyłu jednego wpisu, wywołując metodę **GoBack** . Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** i **GoBack** są implementowane <xref:System.Windows.Navigation.NavigationWindow>przez <xref:System.Windows.Controls.Frame>,, <xref:System.Windows.Navigation.NavigationService>i.  
  
> [!NOTE]
>  Jeśli wywołasz **GoBack**i nie ma żadnych wpisów w historii nawigacji wstecznej, <xref:System.InvalidOperationException> zostanie zgłoszony.
