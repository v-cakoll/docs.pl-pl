---
title: 'Instrukcje: Odtwarzanie dźwięku systemowego za pomocą formularza Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing for system events
- playing sounds [Windows Forms], Windows Forms
- system sounds [Windows Forms], playing from Windows Forms
- playing sounds [Windows Forms], system
- SoundPlayer class [Windows Forms], system sounds
- sounds [Windows Forms], playing
- examples [Windows Forms], sounds
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
ms.openlocfilehash: 1883e73f3b1937e8568b751d1cb9f3b57548c010
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649508"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a><span data-ttu-id="469dc-102">Instrukcje: Odtwarzanie dźwięku systemowego za pomocą formularza Windows</span><span class="sxs-lookup"><span data-stu-id="469dc-102">How to: Play a System Sound from a Windows Form</span></span>
<span data-ttu-id="469dc-103">Poniższy kod przykładowy odtwarza `Exclamation` dźwięku systemowego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="469dc-103">The following code example plays the `Exclamation` system sound at run time.</span></span> <span data-ttu-id="469dc-104">Aby uzyskać więcej informacji na temat dźwięki systemu, zobacz <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="469dc-104">For more information about system sounds, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="469dc-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="469dc-105">Example</span></span>  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="469dc-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="469dc-106">Compiling the Code</span></span>  
 <span data-ttu-id="469dc-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="469dc-107">This example requires:</span></span>  
  
-   <span data-ttu-id="469dc-108">Odwołanie do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="469dc-108">A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469dc-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="469dc-109">See also</span></span>
- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [<span data-ttu-id="469dc-110">Instrukcje: Odtwórz sygnał dźwiękowy z formularza Windows</span><span class="sxs-lookup"><span data-stu-id="469dc-110">How to: Play a Beep from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)
- [<span data-ttu-id="469dc-111">Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows</span><span class="sxs-lookup"><span data-stu-id="469dc-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
