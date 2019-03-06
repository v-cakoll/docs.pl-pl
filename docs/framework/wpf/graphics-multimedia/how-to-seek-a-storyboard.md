---
title: 'Instrukcje: Wyszukaj scenorys'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
ms.openlocfilehash: 7553550f406cc72603aa9f65e4233a13329223a9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354287"
---
# <a name="how-to-seek-a-storyboard"></a>Instrukcje: Wyszukaj scenorys
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
