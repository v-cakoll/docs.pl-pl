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
ms.openlocfilehash: cc0ec3c624fc4f47a0ef8594669ba120e6628e82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684401"
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
