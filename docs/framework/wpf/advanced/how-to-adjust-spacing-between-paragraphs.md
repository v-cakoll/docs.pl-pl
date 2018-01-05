---
title: "Jak dopasować odstępy między akapitami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b2d02e1513a0d8a3c31e4a13c9599666a4122a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>Jak dopasować odstępy między akapitami
W tym przykładzie przedstawiono sposób dostosować lub wyeliminowanie odstępy między akapitów w dowolnej zawartości.  
  
 W zawartości przepływu odstępu między akapitów jest wynikiem marginesy ustawić te akapitów; w związku z tym odstępów między akapitów można kontrolować przez dostosowanie wartości właściwości marginesy na tych akapitów.  Aby całkowicie wyeliminować dodatkowy odstęp między dwoma akapitów, Ustaw marginesy akapitów do **0**.  Do osiągnięcia uniform odstępy między akapitów w całym cały <xref:System.Windows.Documents.FlowDocument>, użyj stylów, aby ustawić wartość uniform margines dla wszystkich akapitów <xref:System.Windows.Documents.FlowDocument>.  
  
 Należy pamiętać, czy marginesy dwóch sąsiadujących ze sobą akapitów zostanie "collapse" do większych dwóch marginesu zamiast podwojenia się. Jeśli więc dwóch sąsiadujących ze sobą akapitów mają odpowiednio marginesy 20 pikseli i 40 pikseli, wynikowy odstęp między akapity 40 pikseli, większy margines dwóch wartości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto stylów, aby ustawić margines dla wszystkich <xref:System.Windows.Documents.Paragraph> elementów w <xref:System.Windows.Documents.FlowDocument> do **0**, co eliminuje skutecznie dodatkowy odstęp między akapitów <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
