---
title: 'Instrukcje: Odtwórz sygnał dźwiękowy z formularza Windows'
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
ms.openlocfilehash: d04bf4bd45aa6ba5dfe231d5f69c2b2a13765373
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710436"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="40161-102">Instrukcje: Odtwórz sygnał dźwiękowy z formularza Windows</span><span class="sxs-lookup"><span data-stu-id="40161-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="40161-103">W tym przykładzie odtwarza sygnał dźwiękowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40161-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40161-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="40161-104">Example</span></span>  
  
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
>  <span data-ttu-id="40161-105">Dźwięk w C# przykładowy kod jest określany przez <xref:System.Media.SystemSounds.Beep%2A> dźwięku ustawienia systemowego.</span><span class="sxs-lookup"><span data-stu-id="40161-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="40161-106">Aby uzyskać więcej informacji, zobacz <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="40161-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40161-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="40161-107">Compiling the Code</span></span>  
 <span data-ttu-id="40161-108">Aby uzyskać C#, w tym przykładzie wymaga odwołania do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="40161-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40161-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40161-109">See also</span></span>
- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="40161-110">Instrukcje: Odtwarzanie dźwięku systemowego za pomocą formularza Windows</span><span class="sxs-lookup"><span data-stu-id="40161-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="40161-111">Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows</span><span class="sxs-lookup"><span data-stu-id="40161-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
