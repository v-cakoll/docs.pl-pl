---
title: 'Instrukcje: Poruszanie się w przód i wstecz w historii nawigacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: 76a78debdce14123cc465ac9abf4db906fe0a2df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961353"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Instrukcje: Poruszanie się w przód i wstecz w historii nawigacji
Ten przykład ilustruje sposób nawigowania do przodu lub z powrotem do wpisów w historii nawigacji.  
  
## <a name="example"></a>Przykład  
 Kod, który jest uruchamiany z zawartości na poniższych hostach, może przechodzić do przodu lub do tyłu przez historię przeglądania, po jednym wpisie.  
  
- <xref:System.Windows.Navigation.NavigationWindow>użyciu<xref:System.Windows.Navigation.NavigationService>  
  
- <xref:System.Windows.Controls.Frame>użyciu<xref:System.Windows.Navigation.NavigationService>  
  
- Internet Explorer  
  
 Przed przejściem do przodu jednego wpisu należy najpierw sprawdzić, czy istnieją wpisy w historii przeglądania do przodu, sprawdzając Właściwość **CanGoForward** . Aby poruszać się po jednym wpisie, należy wywołać metodę **GoForward** . Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Aby móc nawigować po jednym wpisie, musisz najpierw sprawdzić, czy istnieją wpisy w historii nawigacji wstecznej, sprawdzając Właściwość **CanGoBack** . Aby nawigować po jednym wpisie, należy wywołać metodę **GoBack** . Jest to zilustrowane w poniższym przykładzie:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
> Jeśli wywołasz **GoForward**i nie ma żadnych wpisów w historii przeglądania do przodu lub jeśli wywołasz **GoBack**i nie ma żadnych wpisów w <xref:System.InvalidOperationException> historii nawigacji wstecznej, zostanie zgłoszony.
