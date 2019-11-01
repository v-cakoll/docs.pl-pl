---
title: 'Nie można zapisać do pliku wyjściowego „<filename>”: <error>'
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 087735722fcd4dd789e25aacf6eeefffb490dac5
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198190"
---
# <a name="unable-to-write-to-output-file-filename-error"></a>Nie można zapisać do pliku wyjściowego "\<filename >": błąd \<
Wystąpił problem podczas tworzenia pliku.  
  
 Nie można otworzyć pliku wyjściowego do zapisu. Plik (lub folder zawierający plik) może być otwarty do wyłącznego użytku przez inny proces lub może mieć ustawiony atrybut tylko do odczytu.  
  
 Typowe sytuacje, w których plik jest otwierany wyłącznie:  
  
- Aplikacja jest już uruchomiona i używa jej plików. Aby rozwiązać ten problem, upewnij się, że aplikacja nie jest uruchomiona.  
  
- Inna aplikacja otworzyła plik. Aby rozwiązać ten problem, upewnij się, że żadne inne aplikacje nie uzyskują dostępu do plików. Nie zawsze jest oczywiste, która aplikacja uzyskuje dostęp do Twoich plików; w takim przypadku ponowne uruchomienie komputera może być Najprostszym sposobem na zakończenie działania aplikacji.  
  
 Jeśli nawet jeden z plików wyjściowych projektu jest oznaczony jako tylko do odczytu, zostanie zgłoszony ten wyjątek.  
  
 **Identyfikator błędu:** BC31019  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Skompiluj ponownie program, aby zobaczyć, czy błąd jest powtarzany.  
  
2. Jeśli błąd będzie nadal występował, Zapisz swoją pracę i ponownie uruchom program Visual Studio.  
  
3. Jeśli błąd będzie się powtarzać, uruchom ponownie komputer.  
  
4. Jeśli błąd się powtarza, zainstaluj ponownie Visual Basic.  
  
5. Jeśli błąd będzie się powtarzać po ponownej instalacji, powiadom firmę Microsoft o pomocy technicznej.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Aby sprawdzić atrybuty plików w Eksploratorze plików  
  
1. Otwórz folder, który Cię interesuje.  
  
2. Kliknij ikonę **widoki** i wybierz pozycję **szczegóły**.  
  
3. Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie wybierz z listy rozwijanej **atrybuty** .  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Aby zmienić atrybuty pliku lub folderu  
  
1. W **Eksploratorze plików**kliknij prawym przyciskiem myszy plik lub folder, a następnie wybierz polecenie **Właściwości**.  
  
2. W sekcji **atrybuty** karty **Ogólne** wyczyść pole **tylko do odczytu** .  
  
3. Naciśnij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz także

- [Porozmawiaj z nami](/visualstudio/ide/feedback-options)
