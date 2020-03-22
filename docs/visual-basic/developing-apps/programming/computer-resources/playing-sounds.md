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

Obiekt `My.Computer.Audio` udostępnia metody odtwarzania dźwięków.  
  
## <a name="playing-sounds"></a>Odtwarzanie dźwięków  

 Odtwarzanie w tle umożliwia aplikacji wykonywanie innego kodu podczas odtwarzania dźwięku. Metoda `My.Computer.Audio.Play` pozwala aplikacji odtwarzać tylko jeden dźwięk tła naraz; gdy aplikacja odtwarza nowy dźwięk tła, przestaje odtwarzać poprzedni dźwięk tła. Możesz również odtworzyć dźwięk i poczekać na jego zakończenie.  
  
 W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk. Po `AudioPlayMode.WaitToComplete` określeniu, czeka, `My.Computer.Audio.Play` aż dźwięk zostanie ukończony przed wywołaniem kodu będzie kontynuowany. Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odnosi się do pliku dźwiękowego .wav znajdującego się na komputerze  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza dźwięk. Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji zawierają plik dźwiękowy .wav o nazwie Waterfall.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Odtwarzanie zapętlania dźwięków  

 W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza określony dźwięk `PlayMode.BackgroundLoop` w tle, gdy jest określony. Korzystając z tego przykładu, należy upewnić się, że nazwa pliku odnosi się do pliku dźwiękowego .wav, który znajduje się na komputerze.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 W poniższym przykładzie `My.Computer.Audio.Play` metoda odtwarza określony dźwięk `PlayMode.BackgroundLoop` w tle, gdy jest określony. Korzystając z tego przykładu, należy upewnić się, że zasoby aplikacji zawierają plik dźwiękowy .wav o nazwie Waterfall.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 W poprzednim przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **aplikacji windows formularzy > dźwięku**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, należy ostatecznie zatrzymać dźwięk.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Zatrzymywanie odtwarzania dźwięków w tle  

 Użyj `My.Computer.Audio.Stop` tej metody, aby zatrzymać aktualnie odtwarzany dźwięk tła lub pętli aplikacji.  
  
 Ogólnie rzecz biorąc, gdy aplikacja odtwarza dźwięk pętli, należy zatrzymać dźwięk w pewnym momencie.  
  
 Poniższy przykład zatrzymuje dźwięk odtwarzany w tle.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 W poprzednim przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **aplikacji windows formularzy > dźwięku**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Odtwarzanie dźwięków systemowych  

 Użyj `My.Computer.Audio.PlaySystemSound` tej metody, aby odtworzyć określony dźwięk systemu.  
  
 Metoda `My.Computer.Audio.PlaySystemSound` przyjmuje jako parametr jeden z elementów członkowskich udostępnionych <xref:System.Media.SystemSound> z klasy. Dźwięk <xref:System.Media.SystemSounds.Asterisk%2A> systemu zazwyczaj oznacza błędy.  
  
 W poniższym przykładzie `My.Computer.Audio.PlaySystemSound` użyto tej metody odtwarzania dźwięku systemowego.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
