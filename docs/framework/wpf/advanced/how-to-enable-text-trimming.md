---
title: "Jak włączyć przycinanie tekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdaafa62815c75d8ab364a18d909d867f90052c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-text-trimming"></a>Jak włączyć przycinanie tekstu
Przykładzie przedstawiono sposób użycia i skutków dostępnymi w wartości <xref:System.Windows.TextTrimming> wyliczenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.TextBlock> element z <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> atrybut.  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a>Przykład  
 Ustawienie odpowiadającego <xref:System.Windows.TextTrimming> właściwości w kodzie przedstawiono poniżej.  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 Dostępne są obecnie trzy opcje przycinanie tekstu: **CharacterEllipsis**, **WordEllipsis**, i **Brak**.  
  
 Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **CharacterEllipsis**, tekst jest ograniczona i nadal z wielokropkiem na najbliższą krawędzią przycinanie znaków.  To ustawienie zwykle przycinany tekst, który lepiej dopasowania do granicy przycinanie, ale może spowodować wyrazy, gdzie są obcinane częściowo.  Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> podobny do zdefiniowanych powyżej.  
  
 ![Przykład: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")  
  
 Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ustawiono **WordEllipsis**, tekst jest ograniczona i nadal z wielokropkiem na końcu pierwszego pełnego wyrazu najbliższą krawędzią przycinania.  To ustawienie nie zostanie wyświetlone częściowo wycięte wyrazów, ale nie powoduje przycinany tekst używanemu do krawędzi przycinanie jako **CharacterEllipsis** ustawienie.  Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> zdefiniowanych powyżej.  
  
 ![Przykład: Opcja TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")  
  
 Gdy <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ma ustawioną wartość **Brak**, przycinanie tekstu, nie jest wykonywana.  W takim przypadku tekst jest po prostu przycięty do granicy kontenera nadrzędnego tekstu.  Na poniższej ilustracji przedstawiono efekt tego ustawienia na <xref:System.Windows.Controls.TextBlock> podobny do zdefiniowanych powyżej.  
  
 ![Przykład: Opcja TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")
