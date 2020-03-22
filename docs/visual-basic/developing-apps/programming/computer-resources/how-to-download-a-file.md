---
title: 'Porady: pobieranie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 4923feb46ff638de9514a4d70fc00367491a6f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345622"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Porady: pobieranie pliku w Visual Basic

Metoda <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> ta może służyć do pobierania pliku zdalnego i przechowywania go w określonej lokalizacji. Jeśli `ShowUI` parametr jest `True`ustawiony na , zostanie wyświetlone okno dialogowe pokazujące postęp pobierania i umożliwiające użytkownikom anulowanie operacji. Domyślnie istniejące pliki o tej samej nazwie nie są zastępowane; jeśli chcesz zastąpić istniejące pliki, ustaw `overwrite` parametr `True`na .

Następujące warunki mogą spowodować wyjątek:

- Nazwa dysku jest<xref:System.ArgumentException>nieprawidłowa ( ).

- Nie dostarczono niezbędnego<xref:System.UnauthorizedAccessException> <xref:System.Security.SecurityException>uwierzytelnienia ( lub ).

- Serwer nie odpowiada w `connectionTimeout` ramach<xref:System.TimeoutException>określonego ( ).

- Żądanie jest odrzucane przez<xref:System.Net.WebException>witrynę sieci Web ( ).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plikiem źródłowym języka Visual Basic. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.

### <a name="to-download-a-file"></a>Aby pobrać plik

- Użyj `DownloadFile` metody, aby pobrać plik, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w której ma być przechowywany plik. W tym przykładzie `WineList.txt` `http://www.cohowinery.com/downloads` plik jest pobierany i zapisywany w: `C:\Documents and Settings\All Users\Documents`

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Aby pobrać plik, określanie przedziału przesuwu

- Użyj `DownloadFile` metody, aby pobrać plik, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI, określając lokalizację, w której plik ma być przechowywany, i określając przedział limitów czasu w milisekundach (wartość domyślna to 1000). W tym przykładzie `WineList.txt` `http://www.cohowinery.com/downloads` pobiera plik i `C:\Documents and Settings\All Users\Documents`zapisuje go do , określając przedział limit czasu 500 milisekund:

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Aby pobrać plik, podając nazwę użytkownika i hasło

- Użyj `DownLoadFile` metody, aby pobrać plik, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w której ma być przechowywany plik, nazwę użytkownika i hasło. W tym przykładzie `WineList.txt` `http://www.cohowinery.com/downloads` pobiera plik i `C:\Documents and Settings\All Users\Documents`zapisuje go `anonymous` do , z nazwą użytkownika i pustym hasłem.

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > Protokół FTP stosowany `DownLoadFile` w tej metodzie wysyła informacje, w tym hasła, w postaci zwykłego tekstu i nie powinien być używany do przekazywania informacji poufnych.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Instrukcje: przekazywanie pliku](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [Porady: analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
