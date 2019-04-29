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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651223"
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="7d0f8-102">Instrukcje: Wyszukiwanie scenorysu</span><span class="sxs-lookup"><span data-stu-id="7d0f8-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="7d0f8-103">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody <xref:System.Windows.Media.Animation.Storyboard> aby przejść do dowolnego położenia w animacji scenorysu.</span><span class="sxs-lookup"><span data-stu-id="7d0f8-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d0f8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d0f8-104">Example</span></span>  
 <span data-ttu-id="7d0f8-105">Poniżej znajduje się kod XAML znaczników dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="7d0f8-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="7d0f8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d0f8-106">Example</span></span>  
 <span data-ttu-id="7d0f8-107">Poniżej przedstawiono kod używany za pomocą powyższego kodu XAML.</span><span class="sxs-lookup"><span data-stu-id="7d0f8-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7d0f8-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d0f8-108">See also</span></span>

- [<span data-ttu-id="7d0f8-109">Synchroniczne wyszukiwanie scenorysu</span><span class="sxs-lookup"><span data-stu-id="7d0f8-109">Seek a Storyboard Synchronously</span></span>](how-to-seek-a-storyboard-synchronously.md)
