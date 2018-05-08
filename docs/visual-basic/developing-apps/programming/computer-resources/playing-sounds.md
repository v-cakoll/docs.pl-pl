---
title: Odtwarzanie dźwięków (Visual Basic)
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
ms.openlocfilehash: decd845fde5bd4fad702cfe05fd63fcc180b63a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="playing-sounds-visual-basic"></a>Odtwarzanie dźwięków (Visual Basic)
`My.Computer.Audio` Obiektu zapewnia metody odtwarzanie dźwięków.  
  
## <a name="playing-sounds"></a>Odtwarzanie dźwięków  
 Odtwarzanie tła umożliwia aplikacji wykonanie innych kodu podczas odtwarzania dźwięku. `My.Computer.Audio.Play` Metody umożliwia aplikacji Odtwórz tylko jedno tło dźwięk w czasie; gdy aplikacja odtwarza dźwięk nowe tło, zatrzymuje odtwarzanie dźwięku poprzedniej tła. Można także odtwarzanie dźwięku i poczekaj na jej zakończenie.  
  
 W poniższym przykładzie `My.Computer.Audio.Play` metody odtwarza dźwięk. Gdy `AudioPlayMode.WaitToComplete` jest określony, `My.Computer.Audio.Play` czeka, aż do zakończenia dźwięk, przed kontynuowaniem wywołanie kodu. Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego .wav znajduje się na komputerze  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 W poniższym przykładzie `My.Computer.Audio.Play` metody odtwarza dźwięk. Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy wav o nazwie wykresu kaskadowego.  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>Odtwarzanie dźwięków pętli  
 W poniższym przykładzie `My.Computer.Audio.Play` metody odtwarza dźwięk określony w tle podczas `PlayMode.BackgroundLoop` jest określona. Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego .wav znajduje się na tym komputerze.  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 W poniższym przykładzie `My.Computer.Audio.Play` metody odtwarza dźwięk określony w tle podczas `PlayMode.BackgroundLoop` jest określona. Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy wav o nazwie wykresu kaskadowego.  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 W poprzednim przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense. Selektor wstawek kodu, znajduje się się w **aplikacjach formularzy systemu Windows > dźwięk**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
 Ogólnie rzecz biorąc gdy aplikacja odtwarza zapętlony dźwięk, powinien po pewnym czasie zatrzymał dźwięku.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zatrzymuje odtwarzanie dźwięków w tle  
 Użyj `My.Computer.Audio.Stop` metodę, aby zatrzymać aplikacji aktualnie odtwarzanie tło lub odtwarzanie dźwięku w pętli.  
  
 Ogólnie rzecz biorąc gdy aplikacja odtwarza zapętlony dźwięk, należy zatrzymać dźwięk w pewnym momencie.  
  
 Poniższy przykład powoduje zatrzymanie dźwięk jest odtwarzany w tle.  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 W poprzednim przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense. Selektor wstawek kodu, znajduje się się w **aplikacjach formularzy systemu Windows > dźwięk**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Odtwarzanie dźwięków systemu  
 Użyj `My.Computer.Audio.PlaySystemSound` metodę, aby odtwarzać dźwięk do określonego systemu.  
  
 `My.Computer.Audio.PlaySystemSound` Metoda przyjmuje jako parametr jedną udostępniane elementy członkowskie z <xref:System.Media.SystemSound> klasy. Dźwięku systemowego <xref:System.Media.SystemSounds.Asterisk%2A> zazwyczaj oznacza błędy.  
  
 W poniższym przykładzie użyto `My.Computer.Audio.PlaySystemSound` metodę, aby odtwarzać dźwięk systemu.  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Devices.Audio>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>  
 <xref:Microsoft.VisualBasic.AudioPlayMode>
