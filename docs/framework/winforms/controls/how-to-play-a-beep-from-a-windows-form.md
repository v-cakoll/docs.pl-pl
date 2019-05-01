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
ms.openlocfilehash: 0aa01f600873dd8853e1c33d5443448835e11455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913435"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Instrukcje: odtwarzanie sygnału dźwiękowego z formularza systemu Windows
W tym przykładzie odtwarza sygnał dźwiękowy w czasie wykonywania.  
  
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
>  Dźwięk w C# przykładowy kod jest określany przez <xref:System.Media.SystemSounds.Beep%2A> dźwięku ustawienia systemowego. Aby uzyskać więcej informacji, zobacz <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uzyskać C#, w tym przykładzie wymaga odwołania do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [Instrukcje: Odtwarzanie dźwięku systemowego za pomocą formularza Windows](how-to-play-a-system-sound-from-a-windows-form.md)
- [Instrukcje: Odtwarzanie dźwięku za pomocą formularza Windows](how-to-play-a-sound-from-a-windows-form.md)
