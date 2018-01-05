---
title: "Jak wstawić element do tekstu za pomocą programowania"
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
- Text Animation sample [WPF]
- elements [WPF], inserting into text
- inserting elements into text [WPF]
- TextPointer objects [WPF]
- text [WPF], inserting elements
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b200489c4b7fb06f2eb98c0ec9c84da42f18a395
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a>Jak wstawić element do tekstu za pomocą programowania
Poniższy przykład przedstawia użycie dwóch <xref:System.Windows.Documents.TextPointer> obiektów, aby określić zakres tekstu do zastosowania <xref:System.Windows.Documents.Span> elementu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono, jak wygląda w tym przykładzie.  
  
 ![Element Span zastosowany do zakresu tekstu](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd dokumentu przepływu](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
