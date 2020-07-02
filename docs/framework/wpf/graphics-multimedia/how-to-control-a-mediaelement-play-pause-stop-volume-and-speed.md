---
title: Jak kontrolować MediaElement (odtwórz, pauza, zatrzymaj, głośność i prędkość)
description: Sterowanie odtwarzaniem multimediów w programie Windows Presentation Foundation (WPF). Uruchamianie, zatrzymywanie, wstrzymywanie, pomijanie z tyłu i do przodu oraz dostosowywanie głośności i szybkości.
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
ms.openlocfilehash: da846299eaa1e36b6e5caab08bc1f861e9f9c46d
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853597"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="cddf1-104">Jak kontrolować MediaElement (odtwórz, pauza, zatrzymaj, głośność i prędkość)</span><span class="sxs-lookup"><span data-stu-id="cddf1-104">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="cddf1-105">Poniższy przykład pokazuje, jak sterować odtwarzaniem multimediów przy użyciu <xref:System.Windows.Controls.MediaElement> .</span><span class="sxs-lookup"><span data-stu-id="cddf1-105">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="cddf1-106">W przykładzie tworzony jest prosty odtwarzacz multimedialny, który umożliwia odtwarzanie, wstrzymywanie, zatrzymywanie i pomijanie oraz przechodzenie do tyłu i z powrotem na nośniku, a także dostosowanie współczynnika głośności i szybkości.</span><span class="sxs-lookup"><span data-stu-id="cddf1-106">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cddf1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="cddf1-107">Example</span></span>  
 <span data-ttu-id="cddf1-108">Poniższy kod tworzy interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cddf1-108">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cddf1-109"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>Właściwość <xref:System.Windows.Controls.MediaElement> musi być ustawiona na, aby `Manual` można było interaktywnie zatrzymać, wstrzymać i odtworzyć nośnik.</span><span class="sxs-lookup"><span data-stu-id="cddf1-109">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="cddf1-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="cddf1-110">Example</span></span>  
 <span data-ttu-id="cddf1-111">Poniższy kod implementuje funkcjonalność przykładowych kontrolek interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cddf1-111">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="cddf1-112"><xref:System.Windows.Controls.MediaElement.Play%2A>Metody, <xref:System.Windows.Controls.MediaElement.Pause%2A> , i <xref:System.Windows.Controls.MediaElement.Stop%2A> są używane odpowiednio do odtwarzania, wstrzymywania i zatrzymywania nośnika.</span><span class="sxs-lookup"><span data-stu-id="cddf1-112">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="cddf1-113">Zmiana <xref:System.Windows.Controls.MediaElement.Position%2A> właściwości elementu <xref:System.Windows.Controls.MediaElement> umożliwia pominięcie na nośniku.</span><span class="sxs-lookup"><span data-stu-id="cddf1-113">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="cddf1-114">Na koniec <xref:System.Windows.Controls.MediaElement.Volume%2A> właściwości i służą <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> do dostosowywania głośności i szybkości odtwarzania nośnika.</span><span class="sxs-lookup"><span data-stu-id="cddf1-114">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="cddf1-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cddf1-115">See also</span></span>

- [<span data-ttu-id="cddf1-116">Sterowanie elementem MediaElement z użyciem scenorysu</span><span class="sxs-lookup"><span data-stu-id="cddf1-116">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
