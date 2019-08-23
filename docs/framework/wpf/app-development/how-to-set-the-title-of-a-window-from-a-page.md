---
title: 'Instrukcje: Ustawianie tytułu okna z poziomu strony'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 0f618af89965822b0df96a264997dabd9cae7608
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940786"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Instrukcje: Ustawianie tytułu okna z poziomu strony
Ten przykład pokazuje, jak ustawić tytuł okna, w którym <xref:System.Windows.Controls.Page> jest hostowany.  
  
## <a name="example"></a>Przykład  
 Strona może zmienić tytuł okna, w którym jest obsługiwana przez ustawienie <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości, na przykład:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
> <xref:System.Windows.Controls.Page.Title%2A> Ustawienie właściwości strony nie powoduje zmiany wartości tytułu okna. Zamiast tego <xref:System.Windows.Controls.Page.Title%2A> określa nazwę wpisu strony w historii nawigacji.
