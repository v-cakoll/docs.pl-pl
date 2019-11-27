---
title: 'Rozwiązywanie problemów: odczytywanie z plików tekstowych i zapisywanie do nich'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: dbc53ca3cc9ae9b2d14b925f891d0409b2b7debd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333797"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Rozwiązywanie problemów: odczytywanie z plików tekstowych i zapisywanie do nich (Visual Basic)

W tym temacie omówiono typowe problemy występujące podczas pracy z plikami tekstowymi i sugerujemy podejście do każdego z nich.  
  
## <a name="common-problems"></a>Typowe problemy  

 Najczęstsze problemy występujące podczas pracy z plikami tekstowymi obejmują wyjątki zabezpieczeń, kodowanie plików lub nieprawidłowe ścieżki.  
  
### <a name="security-exceptions"></a>Wyjątki zabezpieczeń  

 <xref:System.Security.SecurityException> jest generowany w przypadku wystąpienia błędu zabezpieczeń. Jest to często wynikiem braku potrzebnych uprawnień przez użytkownika, które mogą zostać rozwiązane przez dodanie uprawnień lub praca z plikami w izolowanym magazynie.  
  
### <a name="file-encodings"></a>Kodowanie plików  

 Kodowanie plików, znane także jako kodowania znaków, określają sposób reprezentowania znaków podczas przetwarzania tekstu. Nieoczekiwane znaki w pliku tekstowym mogą wynikać z nieprawidłowego kodowania. W przypadku większości plików jedno kodowanie może być preferowane przez inne warunki języka, które może lub nie może obsłużyć, chociaż standard Unicode jest zazwyczaj preferowany. Aby uzyskać więcej informacji, zobacz [kodowanie plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) i <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Nieprawidłowe ścieżki  

 Podczas analizowania ścieżek plików, szczególnie ścieżek względnych, można łatwo dostarczać błędne dane. Wiele problemów można poprawić, upewniając się, że jest dostarczana poprawna ścieżka. Aby uzyskać więcej informacji, zobacz [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
