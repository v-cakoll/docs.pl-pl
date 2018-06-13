---
title: 'Porady: tworzenie pliku w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 6167ea0850308eec4b558a47dd881476325a8ea1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584849"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Porady: tworzenie pliku w Visual Basic
Pusty plik tekstowy w tym przykładzie jest tworzona przy użyciu określonej ścieżki <xref:System.IO.File.Create%2A> metoda <xref:System.IO.File> klasy.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Użyj `file` zmienną do zapisu w pliku.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli plik już istnieje, zostanie zastąpiony.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa ścieżki jest nieprawidłowo sformułowany. Na przykład zawiera niedozwolone znaki lub jest tylko znak odstępu (<xref:System.ArgumentException>).  
  
-   Ścieżka jest tylko do odczytu (<xref:System.IO.IOException>).  
  
-   Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).  
  
-   Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Ścieżka jest tylko dwukropka ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 A <xref:System.Security.SecurityException> może zostać zgłoszony w częściowo zaufanym środowisku.  
  
 Wywołanie <xref:System.IO.File.Create%2A> metoda wymaga <xref:System.Security.Permissions.FileIOPermission>.  
  
 <xref:System.UnauthorizedAccessException> Jest generowany, jeśli użytkownik nie ma uprawnień do tworzenia pliku.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO>  
 <xref:System.IO.File.Create%2A>  
 [Używanie bibliotek pochodzących z częściowo zaufanego kodu](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)  
 [Podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md)
