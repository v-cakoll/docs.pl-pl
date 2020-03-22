---
title: 'Rozwiązywanie problemów: czytanie z plików tekstowych i zapisywanie ich'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333797"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Rozwiązywanie problemów: czytanie i zapisywanie do plików tekstowych (Visual Basic)

W tym temacie omówiono typowe problemy napotkane podczas pracy z plikami tekstowymi i sugeruje podejście do każdego z nich.  
  
## <a name="common-problems"></a>Typowe problemy  

 Najczęstsze problemy napotkane podczas pracy z plikami tekstowymi obejmują wyjątki zabezpieczeń, kodowanie plików lub nieprawidłowe ścieżki.  
  
### <a name="security-exceptions"></a>Wyjątki zabezpieczeń  

 A <xref:System.Security.SecurityException> jest generowany, gdy wystąpi błąd zabezpieczeń. Jest to często wynikiem użytkownika brak niezbędnych uprawnień, które mogą być rozwiązane przez dodanie uprawnień lub pracy z plikami w izolowanym magazynie.  
  
### <a name="file-encodings"></a>Kodowanie plików  

 Kodowanie plików, znane również jako kodowanie znaków, określa sposób reprezentowania znaków podczas przetwarzania tekstu. Nieoczekiwane znaki w pliku tekstowym mogą wynikać z nieprawidłowego kodowania. W przypadku większości plików jedno kodowanie może być korzystnie lepsze niż inne pod względem znaków języka, które może lub nie może obsłużyć, chociaż unicode jest zwykle preferowane. Aby uzyskać więcej informacji, zobacz <xref:System.Text.Encoding> [Kodowanie plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) i .  
  
### <a name="incorrect-paths"></a>Nieprawidłowe ścieżki  

 Podczas analizowania ścieżek plików, szczególnie ścieżek względnych, łatwo jest podać niewłaściwe dane. Wiele problemów można rozwiązać, upewniając się, że dostarczasz właściwą ścieżkę. Aby uzyskać więcej informacji, zobacz [Jak: Analizować ścieżki plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
