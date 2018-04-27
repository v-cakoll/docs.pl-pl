---
title: 'Nie można zapisać do pliku wyjściowego &#39; &lt;filename&gt;&#39;: &lt;błąd&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a183f81a73c3c8034d9ba7366be8b36d425263da
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a>Nie można zapisać do pliku wyjściowego &#39; &lt;filename&gt;&#39;: &lt;błąd&gt;
Wystąpił problem podczas tworzenia pliku.  
  
 Nie można otworzyć pliku wyjściowego do zapisu. Plik (lub folderu zawierającego plik) może być otwarty w trybie wyłączności przez inny proces lub może mieć jego ustawiony atrybut tylko do odczytu.  
  
 Typowe sytuacje, gdy plik jest otwarty w trybie wyłączności są:  
  
-   Aplikacja jest już uruchomiona i korzystania z jego plików. Aby rozwiązać ten problem, upewnij się, że aplikacja nie jest uruchomiony.  
  
-   Plik został otwarty w innej aplikacji. Aby rozwiązać ten problem, upewnij się, że żadna inna aplikacja uzyskuje dostęp do plików. Nie jest zawsze oczywiste, która aplikacja uzyskuje dostęp do plików. w takim przypadku ponowne uruchomienie komputera może być Najprostszym sposobem, aby zakończyć tę aplikację.  
  
 Jeśli nawet jednego z plików wyjściowych projektu jest oznaczona jako tylko do odczytu, to zostanie wygenerowany wyjątek.  
  
 **Identyfikator błędu:** BC31019  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Skompiluj program, aby zobaczyć, jeśli ten błąd wystąpi ponownie.  
  
2.  Jeśli błąd będzie się powtarzał, Zapisz swoją pracę i ponownie uruchom [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].  
  
3.  Jeśli błąd będzie nadal występował, uruchom ponownie komputer.  
  
4.  Jeśli błąd będzie się powtarzał, zainstaluj ponownie Visual Basic.  
  
5.  Jeśli błąd będzie nadal występować po ponownej instalacji, powiadamia pomocy technicznej firmy Microsoft.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Aby sprawdzić atrybutów plików w Eksploratorze plików  
  
1.  Otwórz folder, który chcesz.  
  
2.  Kliknij przycisk **widoków** ikonę i wybierz polecenie **szczegóły**.  
  
3.  Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie wybierz pozycję **atrybuty** z listy rozwijanej.  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Do zmiany atrybutów pliku lub folderu  
  
1.  W **Eksploratora plików**, kliknij prawym przyciskiem myszy plik lub folder i wybierz **właściwości**.  
  
2.  W **atrybuty** sekcji **ogólne** kartę, wyczyść **tylko do odczytu** pole.  
  
3.  Press **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
