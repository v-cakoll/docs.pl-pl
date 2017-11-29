---
title: "Jak wyszukiwać scenorys"
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
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c76236d8497936500989b56c816f8fe50efcc238
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="34e2b-102">Jak wyszukiwać scenorys</span><span class="sxs-lookup"><span data-stu-id="34e2b-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="34e2b-103">Poniższy przykład przedstawia użycie <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody <xref:System.Windows.Media.Animation.Storyboard> aby przejść do każdej pozycji w animacji scenorysu.</span><span class="sxs-lookup"><span data-stu-id="34e2b-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34e2b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="34e2b-104">Example</span></span>  
 <span data-ttu-id="34e2b-105">Poniżej znajduje się kod znaczników XAML przykładowej.</span><span class="sxs-lookup"><span data-stu-id="34e2b-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="34e2b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="34e2b-106">Example</span></span>  
 <span data-ttu-id="34e2b-107">Oto kod używany z powyższym kodzie XAML.</span><span class="sxs-lookup"><span data-stu-id="34e2b-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="34e2b-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34e2b-108">See Also</span></span>  
 [<span data-ttu-id="34e2b-109">Wyszukiwanie scenorysu synchronicznie</span><span class="sxs-lookup"><span data-stu-id="34e2b-109">Seek a Storyboard Synchronously</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)
