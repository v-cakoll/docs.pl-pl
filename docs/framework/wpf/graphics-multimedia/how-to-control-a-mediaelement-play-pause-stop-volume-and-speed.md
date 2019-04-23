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
ms.openlocfilehash: bb7319fc7ccec0220cbd79a32d5d015f9f2422d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182861"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="efd72-102">Instrukcje: Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)</span><span class="sxs-lookup"><span data-stu-id="efd72-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="efd72-103">Poniższy przykład pokazuje, jak kontrolować odtwarzanie multimediów za pomocą <xref:System.Windows.Controls.MediaElement>.</span><span class="sxs-lookup"><span data-stu-id="efd72-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="efd72-104">Ten przykład tworzy prostą media player, który umożliwia odtwarzanie, wstrzymywanie, zatrzymać i przejdź do i z powrotem na nośniku, a także dostosować współczynnik wielkość i szybkość.</span><span class="sxs-lookup"><span data-stu-id="efd72-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efd72-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="efd72-105">Example</span></span>  
 <span data-ttu-id="efd72-106">Poniższy kod tworzy interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="efd72-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efd72-107"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Właściwość <xref:System.Windows.Controls.MediaElement> musi być równa `Manual` aby można było interaktywnie zatrzymać, wstrzymać, a odtwarzanie nośnika.</span><span class="sxs-lookup"><span data-stu-id="efd72-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="efd72-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="efd72-108">Example</span></span>  
 <span data-ttu-id="efd72-109">Poniższy kod implementuje funkcje przykładowe kontrolek interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="efd72-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="efd72-110"><xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, I <xref:System.Windows.Controls.MediaElement.Stop%2A> metody są używane do odpowiednio odtwarzania, wstrzymać lub zatrzymać nośnika.</span><span class="sxs-lookup"><span data-stu-id="efd72-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="efd72-111">Zmiana <xref:System.Windows.Controls.MediaElement.Position%2A> właściwość <xref:System.Windows.Controls.MediaElement> umożliwia pomijanie na nośniku.</span><span class="sxs-lookup"><span data-stu-id="efd72-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="efd72-112">Na koniec <xref:System.Windows.Controls.MediaElement.Volume%2A> i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> właściwości są używane, aby dostosować szybkość woluminu i odtwarzanie nośnika.</span><span class="sxs-lookup"><span data-stu-id="efd72-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="efd72-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efd72-113">See also</span></span>

- [<span data-ttu-id="efd72-114">Sterowanie elementem MediaElement z użyciem scenorysu</span><span class="sxs-lookup"><span data-stu-id="efd72-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
