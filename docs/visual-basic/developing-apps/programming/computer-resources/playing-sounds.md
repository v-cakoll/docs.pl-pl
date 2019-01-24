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
ms.openlocfilehash: f303687fb86e23191727df769af52811a93fe71e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715793"
---
# <a name="playing-sounds-visual-basic"></a>Odtwarzanie dźwięków (Visual Basic)
`My.Computer.Audio` Obiekt zapewnia metody do odtwarzania dźwięku.  
  
## <a name="playing-sounds"></a>Odtwarzanie dźwięków  
 Odtwarzanie tła umożliwia aplikacji wykonywanie innego kodu, podczas odtwarzania dźwięku. `My.Computer.Audio.Play` Metody umożliwia aplikacji Odtwórz tylko jedno tło dźwięk w czasie; gdy aplikacja odtwarza dźwięk nowe tło, zatrzymuje odtwarzanie dźwięku poprzedniego tła. Możesz odtwarzać dźwięk i poczekaj na jej zakończenie.  
  
 W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk. Gdy `AudioPlayMode.WaitToComplete` jest określony, `My.Computer.Audio.Play` oczekuje na zakończenie przed kontynuowaniem wywoływanie kodu dźwięku. Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego .wav, która znajduje się na komputerze  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk. Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy wav, o nazwie wykres kaskadowy.  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>Odtwarzanie dźwięków pętli  
 W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk określony w tle podczas `PlayMode.BackgroundLoop` jest określony. Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odwołuje się do pliku dźwiękowego .wav, która znajduje się na komputerze.  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk określony w tle podczas `PlayMode.BackgroundLoop` jest określony. Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji obejmują plik dźwiękowy wav, o nazwie wykres kaskadowy.  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 W poprzednim przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **aplikacji z formularzem Windows > dźwięk**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Ogólnie rzecz biorąc gdy aplikacja odtwarza zapętlony dźwięk, powinien po pewnym czasie zatrzymał dźwięku.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zatrzymywanie odtwarzanie dźwięku w tle  
 Użyj `My.Computer.Audio.Stop` metodę, aby zatrzymać aplikacji obecnie odtwarzanie w tle lub odtwarzanie dźwięku w pętli.  
  
 Ogólnie rzecz biorąc gdy aplikacja odtwarza zapętlony dźwięk, należy zatrzymać dźwięk w pewnym momencie.  
  
 Poniższy przykład powoduje zatrzymanie dźwięk jest odtwarzany w tle.  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 W poprzednim przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **aplikacji z formularzem Windows > dźwięk**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Odtwarzanie dźwięków systemu  
 Użyj `My.Computer.Audio.PlaySystemSound` metodę, aby odtworzyć dźwięk określonego systemu.  
  
 `My.Computer.Audio.PlaySystemSound` Metoda przyjmuje jako parametr, jedną z udostępnionych elementów członkowskich z <xref:System.Media.SystemSound> klasy. Dźwięku systemowego <xref:System.Media.SystemSounds.Asterisk%2A> zwykle wskazuje błędy.  
  
 W poniższym przykładzie użyto `My.Computer.Audio.PlaySystemSound` metodę, aby odtworzyć dźwięk systemu.  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
