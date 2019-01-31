---
title: 'Nie można zapisać do pliku wyjściowego „<filename>”: <error>'
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 0f7580c53535c28c97213a5a0488c3fc0365c4ac
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274111"
---
# <a name="unable-to-write-to-output-file-filename-error"></a>Nie można zapisać do pliku wyjściowego "\<nazwa pliku >": \<błąd >
Wystąpił problem podczas tworzenia pliku.  
  
 Nie można otworzyć pliku wyjściowego do zapisu. Plik (lub folder zawierający plik) może być otwarty do wyłącznego użytku przez inny proces lub może być jej ustawiony atrybut tylko do odczytu.  
  
 Typowe sytuacje, gdy plik jest otwarty w trybie wyłączności są następujące:  
  
-   Aplikacja jest już uruchomiona i korzystania z jego plików. Aby rozwiązać ten problem, upewnij się, że aplikacja nie jest uruchomiony.  
  
-   Plik został otwarty w innej aplikacji. Aby rozwiązać ten problem, upewnij się, że żadna inna aplikacja uzyskuje dostęp do plików. Nie zawsze jest oczywiste która aplikacja uzyskuje dostęp do plików. w takim przypadku ponowne uruchomienie komputera może być Najprostszym sposobem, aby zakończyć tę aplikację.  
  
 Jeśli jeszcze jeden z plików wyjściowych projektu jest oznaczony jako tylko do odczytu, ten wyjątek zostanie zgłoszony.  
  
 **Identyfikator błędu:** BC31019  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Skompiluj program ponownie, aby zobaczyć, jeśli błąd będzie się powtarzać.  
  
2.  Jeśli błąd będzie się powtarzał, Zapisz swoją pracę i uruchom ponownie program Visual Studio.  
  
3.  Jeśli błąd będzie się powtarzać, uruchom ponownie komputer.  
  
4.  Jeśli ten błąd wystąpi, zainstaluj ponownie Visual Basic.  
  
5.  Jeśli ten błąd będzie występował po ponownej instalacji, powiadom pomoc techniczna firmy Microsoft.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Aby sprawdzić atrybutów plików w Eksploratorze plików  
  
1.  Otwórz folder, który Cię interesuje.  
  
2.  Kliknij przycisk **widoków** ikonę i wybierz polecenie **szczegóły**.  
  
3.  Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie wybierz **atrybuty** z listy rozwijanej.  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Do zmiany atrybutów pliku lub folderu  
  
1.  W **Eksploratora plików**, kliknij prawym przyciskiem myszy plik lub folder i wybierz polecenie **właściwości**.  
  
2.  W **atrybuty** części **ogólne** kartę, usuń zaznaczenie **tylko do odczytu** pole.  
  
3.  Naciśnij klawisz **OK**.  
  
## <a name="see-also"></a>Zobacz także
- [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
