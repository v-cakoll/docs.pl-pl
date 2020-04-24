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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345521"
---
# <a name="playing-sounds-visual-basic"></a>Odtwarzanie dźwięków (Visual Basic)

`My.Computer.Audio` Obiekt udostępnia metody odtwarzania dźwięków.  
  
## <a name="playing-sounds"></a>Odtwarzanie dźwięków  

 Odtwarzanie w tle umożliwia aplikacji wykonywanie innych kodów podczas odtwarzania dźwięku. `My.Computer.Audio.Play` Metoda umożliwia aplikacji Jednoczesne odtwarzanie tylko jednego dźwięku w tle; gdy aplikacja odtwarza nowy dźwięk w tle, przestaje odtwarzać poprzedni dźwięk w tle. Możesz również odtworzyć dźwięk i poczekać na jego zakończenie.  
  
 W poniższym przykładzie `My.Computer.Audio.Play` Metoda odtwarza dźwięk. Gdy `AudioPlayMode.WaitToComplete` jest określony, `My.Computer.Audio.Play` czeka na zakończenie działania dźwięku przed kontynuowaniem wywoływania kodu. W przypadku korzystania z tego przykładu należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego. wav, który znajduje się na komputerze.  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 W poniższym przykładzie `My.Computer.Audio.Play` Metoda odtwarza dźwięk. W przypadku korzystania z tego przykładu należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy WAV o nazwie wodospad.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Odtwarzanie dźwięków pętli  

 W poniższym przykładzie `My.Computer.Audio.Play` Metoda odtwarza określony dźwięk w tle, gdy `PlayMode.BackgroundLoop` jest określony. W przypadku korzystania z tego przykładu należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego. wav, który znajduje się na komputerze.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 W poniższym przykładzie `My.Computer.Audio.Play` Metoda odtwarza określony dźwięk w tle, gdy `PlayMode.BackgroundLoop` jest określony. W przypadku korzystania z tego przykładu należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy WAV o nazwie wodospad.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 Poprzedni przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **Windows Forms aplikacje > dźwięk**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, powinien ostatecznie zatrzymać dźwięk.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zatrzymywanie odtwarzania dźwięków w tle  

 Użyj `My.Computer.Audio.Stop` metody, aby zatrzymać aktualnie odtwarzane tło lub dźwięk zapętlenia aplikacji.  
  
 Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, powinien zatrzymać dźwięk w pewnym momencie.  
  
 W poniższym przykładzie jest zatrzymywany dźwięk, który jest odtwarzany w tle.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 Poprzedni przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **Windows Forms aplikacje > dźwięk**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Odtwarzanie dźwięków systemowych  

 Użyj `My.Computer.Audio.PlaySystemSound` metody, aby odtworzyć określony dźwięk systemu.  
  
 `My.Computer.Audio.PlaySystemSound` Metoda przyjmuje jako parametr jeden z udostępnionych elementów członkowskich z <xref:System.Media.SystemSound> klasy. Dźwięk <xref:System.Media.SystemSounds.Asterisk%2A> systemowy zwykle oznacza błędy.  
  
 Poniższy przykład używa `My.Computer.Audio.PlaySystemSound` metody do odtwarzania dźwięku systemowego.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
