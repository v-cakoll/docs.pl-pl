---
title: 'Instrukcje: Ustawianie tytułu okna z poziomu strony'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 55444de6c61107979307b94910ba944e7001cf9e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357511"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a><span data-ttu-id="57ae7-102">Instrukcje: Ustawianie tytułu okna z poziomu strony</span><span class="sxs-lookup"><span data-stu-id="57ae7-102">How to: Set the Title of a Window from a Page</span></span>
<span data-ttu-id="57ae7-103">W tym przykładzie przedstawiono sposób ustawiania tytuł okna, w którym <xref:System.Windows.Controls.Page> jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="57ae7-103">This example shows how to set the title of the window in which a <xref:System.Windows.Controls.Page> is hosted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57ae7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="57ae7-104">Example</span></span>  
 <span data-ttu-id="57ae7-105">Strony można zmienić tytuł okna, który jest hostem, ustawiając <xref:System.Windows.Controls.Page.WindowTitle%2A> właściwości w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="57ae7-105">A page can change the title of the window that is hosting it by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, like so:</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  <span data-ttu-id="57ae7-106">Ustawienie <xref:System.Windows.Controls.Page.Title%2A> właściwości strony nie zmienia wartość tytułu okna.</span><span class="sxs-lookup"><span data-stu-id="57ae7-106">Setting the <xref:System.Windows.Controls.Page.Title%2A> property of a page does not change the value of the window title.</span></span> <span data-ttu-id="57ae7-107">Zamiast tego <xref:System.Windows.Controls.Page.Title%2A> Określa nazwę wpisu strony w historii nawigacji.</span><span class="sxs-lookup"><span data-stu-id="57ae7-107">Instead, <xref:System.Windows.Controls.Page.Title%2A> specifies the name of a page entry in navigation history.</span></span>
