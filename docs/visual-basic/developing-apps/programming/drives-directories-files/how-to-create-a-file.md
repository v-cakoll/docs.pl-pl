---
title: 'Instrukcje: Utwórz plik w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: a05e73a2096c82c9299e4483bbaf69e560fc2e45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038067"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Instrukcje: Utwórz plik w języku Visual Basic
W tym przykładzie tworzy pusty plik tekstowy w określonej ścieżki przy użyciu <xref:System.IO.File.Create%2A> method in Class metoda <xref:System.IO.File> klasy.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Użyj `file` zmiennej można zapisać do pliku.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli plik już istnieje, zostanie zastąpiona.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa ścieżki jest nieprawidłowo sformułowany. Na przykład zawiera niedozwolone znaki lub jest tylko spacją (<xref:System.ArgumentException>).  
  
- Ścieżka jest tylko do odczytu (<xref:System.IO.IOException>).  
  
- Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException>).  
  
- Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).  
  
- Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException>).  
  
- Ścieżka jest tylko dwukropek ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 A <xref:System.Security.SecurityException> mogą być generowane w środowisku częściowego zaufania.  
  
 Wywołanie <xref:System.IO.File.Create%2A> metoda wymaga <xref:System.Security.Permissions.FileIOPermission>.  
  
 <xref:System.UnauthorizedAccessException> Jest generowany, jeśli użytkownik nie ma uprawnień do utworzenia pliku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Używanie bibliotek pochodzących z częściowo zaufanego kodu](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md)
