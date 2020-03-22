---
title: 'Porady: tworzenie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348797"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Porady: tworzenie pliku w Visual Basic

W tym przykładzie tworzy pusty plik <xref:System.IO.File.Create%2A> tekstowy <xref:System.IO.File> w określonej ścieżce przy użyciu metody w klasie.  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 Użyj `file` zmiennej, aby zapisać do pliku.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Jeśli plik już istnieje, zostanie zastąpiony.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa ścieżki jest zniekształcona. Na przykład zawiera nielegalne znaki lub jest<xref:System.ArgumentException>tylko biały znak ( ).  
  
- Ścieżka jest tylko do<xref:System.IO.IOException>odczytu ( ).  
  
- Nazwa ścieżki `Nothing` to<xref:System.ArgumentNullException>( ).  
  
- Nazwa ścieżki jest za<xref:System.IO.PathTooLongException>długa ( ).  
  
- Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException>).  
  
- Ścieżka jest tylko dwukropek ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 A <xref:System.Security.SecurityException> może być rzucony w środowiskach częściowego zaufania.  
  
 Wywołanie <xref:System.IO.File.Create%2A> metody wymaga <xref:System.Security.Permissions.FileIOPermission>.  
  
 Jest <xref:System.UnauthorizedAccessException> generowany, jeśli użytkownik nie ma uprawnień do tworzenia pliku.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Używanie bibliotek pochodzących z częściowo zaufanego kodu](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md)
