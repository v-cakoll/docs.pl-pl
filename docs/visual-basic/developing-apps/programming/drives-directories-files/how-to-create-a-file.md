---
title: 'Porady: tworzenie pliku w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e6785086f8c97f983c6dcd6fd713c01e34e258
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Podstawy zabezpieczeń dostępu kodu](https://msdn.microsoft.com/library/33tceax8)
