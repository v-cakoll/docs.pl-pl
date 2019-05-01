---
title: 'Instrukcje: Ustawianie tytułu okna z poziomu strony'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 55444de6c61107979307b94910ba944e7001cf9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054006"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Instrukcje: Ustawianie tytułu okna z poziomu strony
W tym przykładzie przedstawiono sposób ustawiania tytuł okna, w którym <xref:System.Windows.Controls.Page> jest obsługiwana.  
  
## <a name="example"></a>Przykład  
 Strony można zmienić tytuł okna, który jest hostem, ustawiając <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości w następujący sposób:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Ustawienie <xref:System.Windows.Controls.Page.Title%2A> właściwości strony nie zmienia wartość tytułu okna. Zamiast tego <xref:System.Windows.Controls.Page.Title%2A> Określa nazwę wpisu strony w historii nawigacji.
