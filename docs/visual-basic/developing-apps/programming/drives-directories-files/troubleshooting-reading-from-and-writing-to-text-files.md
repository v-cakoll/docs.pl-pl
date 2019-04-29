---
title: 'Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 90a04d9de2ac77c28a92d99e1fe118a1f8ecf448
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650053"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych (Visual Basic)
W tym temacie omówiono typowe problemy występujące podczas pracy z tekstem pliki i sugeruje podejścia do każdego.  
  
## <a name="common-problems"></a>Typowe problemy  
 Typowe problemy występujące podczas pracy z plikami tekstowymi obejmują wyjątki zabezpieczeń, kodowanie pliku lub nieprawidłowe ścieżki.  
  
### <a name="security-exceptions"></a>Wyjątki zabezpieczeń  
 Element <xref:System.Security.SecurityException> jest zgłaszany, gdy wystąpi błąd zabezpieczeń. Często jest to wynik użytkownika, których nie ma wymaganych uprawnień, które mogą zostać rozwiązane przez dodanie uprawnień lub Praca z plikami w wydzielonej pamięci masowej.  
  
### <a name="file-encodings"></a>Kodowanie pliku  
 Określ kodowanie pliku, znany także jako kodowanie znaków do reprezentowania znaków, kiedy przetwarzanie tekstu. Nieoczekiwane znaki w pliku tekstowym mogą wynikać z Nieprawidłowe kodowanie. Dla większości plików jednego formatu kodowania może być preferowane zamiast innego pod względem znaki języków, które mogą lub nie może obsłużyć, chociaż Unicode jest zwykle preferowany. Aby uzyskać więcej informacji, zobacz [kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) i <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Nieprawidłowe ścieżki  
 Podczas analizowania ścieżki plików, szczególnie względnej ścieżki jest łatwe przekazywanie niewłaściwej danych. Można rozwiązać wiele problemów, upewniając się, że są podawania poprawnej ścieżki. Aby uzyskać więcej informacji, zobacz [jak: Analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
