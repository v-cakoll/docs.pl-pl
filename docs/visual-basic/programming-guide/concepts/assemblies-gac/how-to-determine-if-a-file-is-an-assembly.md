---
title: "Porady: Określanie, czy plik jest zestawem (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9b69a40bd11425b7e481dc28fddc560c41df3962
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>Porady: Określanie, czy plik jest zestawem (Visual Basic)
Plik jest zestawem tylko wtedy, gdy jest zarządzana i wpis zestawu w metadanych. Aby uzyskać więcej informacji dotyczących metadanych i zestawy, zobacz temat [manifestu zestawu](https://msdn.microsoft.com/library/1w45z383).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Jak ręcznie ustalić, czy plik jest zestawem  
  
1.  Uruchom [Ildasm.exe (dezasembler IL)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Załaduj plik, który chcesz przetestować.  
  
3.  Jeśli **narzędzia ILDASM** raporty, że plik nie jest plikiem przenośny plik wykonywalny (PE), a następnie nie jest zestawem. Aby uzyskać więcej informacji, zobacz temat [porady: wyświetlanie zawartości zestawu](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programowo ustalić, czy plik jest zestawem  
  
1.  Wywołanie <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> jest metoda pełną ścieżkę i nazwę pliku podczas testowania.  
  
2.  Jeśli <xref:System.BadImageFormatException> wyjątku, plik nie jest zestawem.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie testy bibliotekę DLL, aby zobaczyć, czy jest on zestawem.  
  
```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metody ładuje plik testu, a następnie zwalnia, gdy jest do odczytu informacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.AssemblyName>  
 [Koncepcje programowania](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](index.md)
