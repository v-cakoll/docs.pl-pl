---
title: Odtwarzanie dźwięków
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: 416fedd011ff35d2b32d1b64932e3908a73ed14e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345521"
---
# <a name="playing-sounds-visual-basic"></a>Odtwarzanie dźwięków (Visual Basic)

Obiekt `My.Computer.Audio` zapewnia metody odtwarzania dźwięków.  
  
## <a name="playing-sounds"></a>Odtwarzanie dźwięków  

 Odtwarzanie w tle umożliwia aplikacji wykonywanie innych kodów podczas odtwarzania dźwięku. Metoda `My.Computer.Audio.Play` umożliwia aplikacji Jednoczesne odtwarzanie tylko jednego dźwięku w tle; gdy aplikacja odtwarza nowy dźwięk w tle, przestaje odtwarzać poprzedni dźwięk w tle. Możesz również odtworzyć dźwięk i poczekać na jego zakończenie.  
  
 W poniższym przykładzie metoda `My.Computer.Audio.Play` odtwarza dźwięk. Gdy `AudioPlayMode.WaitToComplete` jest określony, `My.Computer.Audio.Play` czeka na zakończenie działania dźwięku przed kontynuowaniem kodu. W przypadku korzystania z tego przykładu należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego. wav, który znajduje się na komputerze.  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 W poniższym przykładzie metoda `My.Computer.Audio.Play` odtwarza dźwięk. W przypadku korzystania z tego przykładu należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy WAV o nazwie wodospad.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Odtwarzanie dźwięków pętli  

 W poniższym przykładzie metoda `My.Computer.Audio.Play` odtwarza określony dźwięk w tle, gdy `PlayMode.BackgroundLoop` jest określony. W przypadku korzystania z tego przykładu należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego. wav, który znajduje się na komputerze.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 W poniższym przykładzie metoda `My.Computer.Audio.Play` odtwarza określony dźwięk w tle, gdy `PlayMode.BackgroundLoop` jest określony. W przypadku korzystania z tego przykładu należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy WAV o nazwie wodospad.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 Poprzedni przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **Windows Forms aplikacje > dźwięk**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, powinien ostatecznie zatrzymać dźwięk.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zatrzymywanie odtwarzania dźwięków w tle  

 Użyj metody `My.Computer.Audio.Stop`, aby zatrzymać aktualnie odtwarzane tło lub podkład dźwiękowy aplikacji.  
  
 Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, powinien zatrzymać dźwięk w pewnym momencie.  
  
 W poniższym przykładzie jest zatrzymywany dźwięk, który jest odtwarzany w tle.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 Poprzedni przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **Windows Forms aplikacje > dźwięk**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Odtwarzanie dźwięków systemowych  

 Użyj metody `My.Computer.Audio.PlaySystemSound`, aby odtworzyć określony dźwięk systemu.  
  
 Metoda `My.Computer.Audio.PlaySystemSound` przyjmuje jako parametr jeden z udostępnionych elementów członkowskich z klasy <xref:System.Media.SystemSound>. Dźwięk systemowy <xref:System.Media.SystemSounds.Asterisk%2A> zwykle oznacza błędy.  
  
 W poniższym przykładzie zastosowano metodę `My.Computer.Audio.PlaySystemSound`, aby odtworzyć dźwięk systemowy.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
