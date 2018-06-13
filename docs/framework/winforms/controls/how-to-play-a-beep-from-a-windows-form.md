---
title: 'Porady: odtwarzanie sygnału dźwiękowego za pomocą formularza systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
ms.openlocfilehash: 460309d853f2b3b423d14a820771e0230358e3c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531225"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="6d1a7-102">Porady: odtwarzanie sygnału dźwiękowego za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6d1a7-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="6d1a7-103">W tym przykładzie odtwarza dźwięk w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6d1a7-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d1a7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d1a7-104">Example</span></span>  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="6d1a7-105">Dźwięk odtwarzane w przykładowym kodzie C# jest określany przez <xref:System.Media.SystemSounds.Beep%2A> ustawienia dźwięku systemowego.</span><span class="sxs-lookup"><span data-stu-id="6d1a7-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="6d1a7-106">Aby uzyskać więcej informacji, zobacz <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="6d1a7-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6d1a7-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6d1a7-107">Compiling the Code</span></span>  
 <span data-ttu-id="6d1a7-108">Język C#, w tym przykładzie wymaga odwołania do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6d1a7-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1a7-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d1a7-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="6d1a7-110">Instrukcje: odtwarzanie dźwięku systemowego za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6d1a7-110">How to: Play a System Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [<span data-ttu-id="6d1a7-111">Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6d1a7-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
