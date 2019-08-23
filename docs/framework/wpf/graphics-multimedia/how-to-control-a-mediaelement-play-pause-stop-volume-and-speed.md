---
title: 'Instrukcje: Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930161"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="4d6e0-102">Instrukcje: Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)</span><span class="sxs-lookup"><span data-stu-id="4d6e0-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="4d6e0-103">Poniższy przykład pokazuje, <xref:System.Windows.Controls.MediaElement>jak sterować odtwarzaniem multimediów przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="4d6e0-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="4d6e0-104">W przykładzie tworzony jest prosty odtwarzacz multimedialny, który umożliwia odtwarzanie, wstrzymywanie, zatrzymywanie i pomijanie oraz przechodzenie do tyłu i z powrotem na nośniku, a także dostosowanie współczynnika głośności i szybkości.</span><span class="sxs-lookup"><span data-stu-id="4d6e0-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d6e0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d6e0-105">Example</span></span>  
 <span data-ttu-id="4d6e0-106">Poniższy kod tworzy interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d6e0-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d6e0-107">Właściwość musi być ustawiona na `Manual` , aby można było interaktywnie zatrzymać, wstrzymać i odtworzyć nośnik. <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="4d6e0-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="4d6e0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d6e0-108">Example</span></span>  
 <span data-ttu-id="4d6e0-109">Poniższy kod implementuje funkcjonalność przykładowych kontrolek interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d6e0-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="4d6e0-110">Metody <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, i<xref:System.Windows.Controls.MediaElement.Stop%2A> są używane odpowiednio do odtwarzania, wstrzymywania i zatrzymywania nośnika.</span><span class="sxs-lookup"><span data-stu-id="4d6e0-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="4d6e0-111"><xref:System.Windows.Controls.MediaElement.Position%2A> Zmiana właściwości<xref:System.Windows.Controls.MediaElement> elementu umożliwia pominięcie na nośniku.</span><span class="sxs-lookup"><span data-stu-id="4d6e0-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="4d6e0-112">Na <xref:System.Windows.Controls.MediaElement.Volume%2A> koniec właściwości i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> służą do dostosowywania głośności i szybkości odtwarzania nośnika.</span><span class="sxs-lookup"><span data-stu-id="4d6e0-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4d6e0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d6e0-113">See also</span></span>

- [<span data-ttu-id="4d6e0-114">Sterowanie elementem MediaElement z użyciem scenorysu</span><span class="sxs-lookup"><span data-stu-id="4d6e0-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
