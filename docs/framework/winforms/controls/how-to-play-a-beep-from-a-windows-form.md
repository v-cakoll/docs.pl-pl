---
title: 'Instrukcje: odtwarzanie sygnału dźwiękowego z formularza systemu Windows'
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
ms.openlocfilehash: 1a72f88c05fb21c11864058ffbe81c1957525375
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966509"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Instrukcje: odtwarzanie sygnału dźwiękowego z formularza systemu Windows
Ten przykład odtwarza sygnał dźwiękowy w czasie wykonywania.  
  
## <a name="example"></a>Przykład  
  
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
> Dźwięk odtwarzany w przykładzie C# kodu jest określany na <xref:System.Media.SystemSounds.Beep%2A> podstawie ustawienia dźwięku systemowego. Aby uzyskać więcej informacji, zobacz <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W C#przypadku, ten przykład wymaga odwołania do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [Instrukcje: Odtwórz dźwięk systemowy z formularza systemu Windows](how-to-play-a-system-sound-from-a-windows-form.md)
- [Instrukcje: Odtwórz dźwięk z formularza systemu Windows](how-to-play-a-sound-from-a-windows-form.md)
