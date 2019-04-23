---
title: 'Instrukcje: Programowe wstawianie elementu do tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Text Animation sample [WPF]
- elements [WPF], inserting into text
- inserting elements into text [WPF]
- TextPointer objects [WPF]
- text [WPF], inserting elements
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
ms.openlocfilehash: ea9850c8490ec37032d4565c6b3375e3116d4313
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169588"
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a>Instrukcje: Programowe wstawianie elementu do tekstu
Poniższy przykład pokazuje, jak za pomocą dwóch <xref:System.Windows.Documents.TextPointer> obiektów, aby określić zakres tekstu do zastosowania <xref:System.Windows.Documents.Span> elementu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono, jak wygląda następująco.  
  
 ![Element Span zastosowany do zakresu tekstu](./media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd dokumentu przepływu](flow-document-overview.md)
