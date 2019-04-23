---
title: 'Instrukcje: Wyszukiwanie scenorysu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
ms.openlocfilehash: a57272c17a5bc6f5baaa21fb77233fc5693d1914
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131667"
---
# <a name="how-to-seek-a-storyboard"></a>Instrukcje: Wyszukiwanie scenorysu
Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody <xref:System.Windows.Media.Animation.Storyboard> aby przejść do dowolnego położenia w animacji scenorysu.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się kod XAML znaczników dla przykładu.  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono kod używany za pomocą powyższego kodu XAML.  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Synchroniczne wyszukiwanie scenorysu](how-to-seek-a-storyboard-synchronously.md)
