---
title: "Porady: Ustawianie tytułu okna ze strony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 412771e3f43bc3755bdf9236743310ac8060165c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Porady: Ustawianie tytułu okna ze strony
W tym przykładzie przedstawiono sposób ustawiania tytuł okna, w którym <xref:System.Windows.Controls.Page> jest obsługiwana.  
  
## <a name="example"></a>Przykład  
 Strona można zmienić tytuł okna, który jest hostem przez ustawienie <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości, w następujący sposób:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Ustawienie <xref:System.Windows.Controls.Page.Title%2A> właściwości strony nie zmienia wartość tytuł okna. Zamiast tego <xref:System.Windows.Controls.Page.Title%2A> Określa nazwę wpisu strony w historii nawigacji.
