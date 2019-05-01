---
title: 'Instrukcje: Dopasowywanie odstępów między akapitami'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777016"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>Instrukcje: Dopasowywanie odstępów między akapitami
Ten przykład pokazuje, jak dostosować lub wyeliminowania odstępów między akapitami w zawartości przepływu.  
  
 W zawartości przepływu dodatkowe miejsce, który pojawia się między akapitami jest wynikiem marginesy nastavit te akapitów; w związku z tym odstępów między akapitami można kontrolować, dostosowując marginesy w tych akapitach.  Aby całkowicie wyeliminować dodatkowe odstępy między akapitami dwóch ustawić marginesy akapitów do **0**.  Aby osiągnąć jednolitego odstępy między akapitami w całym cały <xref:System.Windows.Documents.FlowDocument>, użyj stylu, aby ustawić wartości jednolitego margines wszystkich akapitów <xref:System.Windows.Documents.FlowDocument>.  
  
 Należy zauważyć, że marginesy dla dwóch sąsiadujących akapitów "zwijane" większą z dwóch marginesów zamiast podwojenia się jest. Dlatego jeśli dwóch sąsiadujących akapitów marginesy 20 pikseli i 40 pikseli odpowiednio, wynikowy odstępy między akapitami jest 40 pikseli, większe wartości dwóch margines.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto stylów można ustawić na marginesie dla wszystkich <xref:System.Windows.Documents.Paragraph> elementów w <xref:System.Windows.Documents.FlowDocument> do **0**, co skutecznie eliminuje dodatkowe odstępy między akapitami w <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
