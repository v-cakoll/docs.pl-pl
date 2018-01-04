---
title: "Jak utworzyć formant z kluczem dostępu i zwijaniem tekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 428d8febe5a789f22eef97301fca3aa4b22f25b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>Jak utworzyć formant z kluczem dostępu i zwijaniem tekstu
W tym przykładzie przedstawiono sposób tworzenia formant, który ma klucz dostępu i obsługuje zawijania tekstu. W przykładzie użyto <xref:System.Windows.Controls.Label> kontroli w celu zilustrowania koncepcji te.  
  
## <a name="example"></a>Przykład  
 **Dodaj zawijania tekstu do etykiety**  
  
 <xref:System.Windows.Controls.Label> Formant nie obsługuje zawijania tekstu. Etykiety, który opakowuje w wielu liniach należy można zagnieżdżać inny element, który obsługuje tekstu zawijania i umieszcza elementu w etykiecie. Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.TextBlock> aby etykiety, który powoduje błąd kilka wierszy tekstu.  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **Dodaj klucz dostępu i zawijania tekstu do etykiety**  
  
 Jeśli potrzebujesz <xref:System.Windows.Controls.Label> zawierającego klawisza dostępu (symbol), użyj <xref:System.Windows.Controls.AccessText> element, który znajduje się wewnątrz <xref:System.Windows.Controls.Label>.  
  
 Określa, takich jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, i <xref:System.Windows.Controls.GroupBox> ma domyślne szablony formantu. Te szablony zawierają <xref:System.Windows.Controls.ContentPresenter>. Jedna z właściwości, które można ustawić na <xref:System.Windows.Controls.ContentPresenter> jest <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", która służy do określania klucza dostępu dla formantu.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.Label> , który ma klucz dostępu i obsługuje zawijania tekstu. Aby włączyć zawijania tekstu, ustawia przykład <xref:System.Windows.Controls.AccessText.TextWrapping%2A> właściwości i używa podkreślenie znaku do określenia klucza dostępu. (Od razu następuje po znaku podkreślenia znak jest klucz dostępu).  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Ustaw właściwość Target etykiety](http://msdn.microsoft.com/en-us/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
