---
title: 'Porady: tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)'
ms.custom: ''
ms.date: 03/14/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cc71a27f24c634ebadb060325df4c602b1387b0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Porady: tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)
Ten przykład przedstawia sposób użycia przyjaznych zestawów z zestawów, które nie mają znaku.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Aby utworzyć zestaw i przyjaznego zestawu  
  
1.  Otwórz wiersz polecenia.  
  
2.  Utwórz plik języka Visual Basic, o nazwie `friend_signed_A.` zawierający następujący kod. W kodzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' vbc -target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  Skompiluj i podpisz friend_signed_A za pomocą następującego polecenia.  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  Utwórz plik języka Visual Basic, o nazwie `friend_unsigned_B` zawierający następujący kod. Ponieważ friend_unsigned_A określa friend_unsigned_B jako przyjaznego zestawu, może uzyskać dostęp przez kod friend_unsigned_B `Friend` typów i członków z friend_unsigned_A.  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  Kompiluj friend_signed_B za pomocą następującego polecenia.  
  
    ```console
    vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     Nazwa zestawu, który jest generowany przez kompilator musi odpowiadać nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Należy jawnie określić zestaw przy użyciu `/out` — opcja kompilatora.  
  
6.  Uruchom plik friend_signed_B.exe.  
  
     Program wyświetla dwóch ciągów: "Class1.Test" i "Class2.Test".  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Brak podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy. Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> można zażądać uprawnienia zabezpieczeń do uruchomienia określonej części kodu, podczas gdy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `Friend` typy i składniki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Przyjazne zestawy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Porady: tworzenie oznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Koncepcje Podręcznik programowania](../../../../visual-basic/programming-guide/concepts/index.md)
