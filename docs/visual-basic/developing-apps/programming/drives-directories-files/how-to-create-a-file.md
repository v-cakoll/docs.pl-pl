---
title: 'Porady: tworzenie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348797"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Porady: tworzenie pliku w Visual Basic

Ten przykład umożliwia utworzenie pustego pliku tekstowego w określonej ścieżce przy użyciu metody <xref:System.IO.File.Create%2A> w klasie <xref:System.IO.File>.  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 Użyj zmiennej `file` do zapisu w pliku.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Jeśli plik już istnieje, zostanie zastąpiony.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa ścieżki jest źle sformułowana. Na przykład zawiera niedozwolone znaki lub jest tylko białym znakiem (<xref:System.ArgumentException>).  
  
- Ścieżka jest tylko do odczytu (<xref:System.IO.IOException>).  
  
- Nazwa ścieżki to `Nothing` (<xref:System.ArgumentNullException>).  
  
- Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).  
  
- Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException>).  
  
- Ścieżka ma tylko dwukropek ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 <xref:System.Security.SecurityException> może być zgłaszane w środowiskach częściowego zaufania.  
  
 Wywołanie metody <xref:System.IO.File.Create%2A> wymaga <xref:System.Security.Permissions.FileIOPermission>.  
  
 Zostanie wygenerowany <xref:System.UnauthorizedAccessException>, jeśli użytkownik nie ma uprawnienia do tworzenia pliku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Korzystanie z bibliotek z częściowo zaufanego kodu](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Podstawowe informacje o zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md)
