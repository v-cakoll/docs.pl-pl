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
ms.openlocfilehash: 5650298da99f8bc9a25c7d7ceea11a8a5bf968fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587534"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych (Visual Basic)
W tym temacie omówiono typowe problemy występujące podczas pracy z tekstem pliki, a także sugeruje podejście do każdego.  
  
## <a name="common-problems"></a>Typowe problemy  
 Najczęściej występujących problemów podczas pracy z plikami tekstowymi zawierać wyjątki zabezpieczeń, kodowania pliku lub nieprawidłowa ścieżki.  
  
### <a name="security-exceptions"></a>Wyjątki zabezpieczeń  
 A <xref:System.Security.SecurityException> jest generowany, gdy wystąpi błąd zabezpieczeń. Często jest to wynik użytkownika, których nie ma wystarczających uprawnień, które mogą zostać rozwiązane przez dodanie uprawnień lub Praca z plikami w magazynie izolowanym.  
  
### <a name="file-encodings"></a>Kodowanie pliku  
 Kodowanie pliku, znanej także jako kodowanie znaków, określ sposób wyświetlania znaków podczas przetwarzania tekstu. Nieoczekiwane znaki w pliku tekstowym może spowodować niepoprawne kodowania. Dla większości plików kodowań może być preferowane zamiast innego pod względem znaków języków, które mogą lub nie może obsłużyć, mimo że Unicode jest zwykle preferowany. Aby uzyskać więcej informacji, zobacz [kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) i <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Nieprawidłowe ścieżki  
 Podczas analizowania ścieżki plików, szczególnie względnych ścieżek, jest bardzo proste dostarczają nieprawidłowe dane. Wiele problemów można usunąć, upewniając się, że są podając prawidłową ścieżkę. Aby uzyskać więcej informacji, zobacz [porady: przeanalizować ścieżki plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
