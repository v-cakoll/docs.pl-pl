---
title: Jak wyszukiwać scenorys synchronicznie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- seeking Storyboards synchronously [WPF]
- Storyboards [WPF], seeking synchronously
ms.assetid: 03e06271-a946-4810-88ea-3fb4cfa9e0f1
ms.openlocfilehash: 9557563dc1ae0392ad6a47063e43a8949e5f9922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-seek-a-storyboard-synchronously"></a><span data-ttu-id="cedd3-102">Jak wyszukiwać scenorys synchronicznie</span><span class="sxs-lookup"><span data-stu-id="cedd3-102">How to: Seek a Storyboard Synchronously</span></span>
<span data-ttu-id="cedd3-103">Poniższy przykład przedstawia użycie <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> metody <xref:System.Windows.Media.Animation.Storyboard> do wyszukania do każdej pozycji w animacji scenorysu synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="cedd3-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to seek to any position in a storyboard animation synchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cedd3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cedd3-104">Example</span></span>  
 <span data-ttu-id="cedd3-105">Poniżej znajduje się kod znaczników XAML przykładowej.</span><span class="sxs-lookup"><span data-stu-id="cedd3-105">The following is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardSynchronouslyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml#seekstoryboardsynchronouslyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="cedd3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cedd3-106">Example</span></span>  
 <span data-ttu-id="cedd3-107">Poniżej znajduje się kod używany z powyższym kodzie XAML.</span><span class="sxs-lookup"><span data-stu-id="cedd3-107">The following is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml.cs#seekstoryboardsynchronouslycodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardSynchronouslyExample.xaml.vb#seekstoryboardsynchronouslycodebehindexamplewholepage)]
