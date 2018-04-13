---
title: 'Porady: tworzenie oznaczonych przyjaznych zestawów (Visual Basic)'
ms.custom: ''
ms.date: 03/14/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fd9521a87a985cbdeff1616c3070c822892b6e5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>Porady: tworzenie oznaczonych przyjaznych zestawów (Visual Basic)
Ten przykład przedstawia sposób użycia przyjaznych zestawów z zestawów o silnych nazwach. Oba zestawy muszą silnej nazwy. Mimo że oba zestawy w tym przykładzie używają tych samych kluczy, można użyć różnych kluczy dla dwóch zestawów.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Aby utworzyć podpisanych zestawów i przyjaznego zestawu  
  
1.  Otwórz wiersz polecenia.  
  
2.  Aby wygenerować plik klucza i wyświetlić jego klucz publiczny, użyj następującej procedury poleceń za pomocą narzędzia silnej nazwy. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnej nazwy)][Sn.exe (narzędzie silnej nazwy)](../../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
    1.  Generowanie klucza silnej nazwy, w tym przykładzie i zapisze go w pliku FriendAssemblies.snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Wyodrębniania klucza publicznego z FriendAssemblies.snk i poddane FriendAssemblies.publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Klucz publiczny, przechowywane w pliku FriendAssemblies.publickey do wyświetlenia:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Utwórz plik języka Visual Basic, o nazwie `friend_signed_A` zawierający następujący kod. W kodzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.  
  
     Przez narzędzie Strong Name generuje nowy klucz publiczny w każdym uruchomieniu. W związku z tym musisz zastąpić klucz publiczny w poniższym kodzie klucza publicznego, który zostanie wygenerowany, jak pokazano w poniższym przykładzie.  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  Skompiluj i podpisz friend_signed_A za pomocą następującego polecenia.  
  
    ```console  
    Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  Utwórz plik języka Visual Basic, o nazwie `friend_signed_B` i zawiera następujący kod. Ponieważ friend_signed_A określa friend_signed_B jako przyjaznego zestawu, może uzyskać dostęp przez kod friend_signed_B `Friend` typów i członków z friend_signed_A. Plik zawiera następujący kod.  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  Skompiluj i podpisz friend_signed_B za pomocą następującego polecenia.  
  
    ```console  
    vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     Nazwa zestawu generowane przez kompilator musi odpowiadać przekazany do nazwy przyjaznego zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Należy jawnie określić zestaw przy użyciu `-out` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
7.  Uruchom plik friend_signed_B.exe.  
  
     To pole zawiera ciąg "Class1.Test".  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Brak podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy. Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> można zażądać uprawnienia zabezpieczeń do uruchomienia określonej części kodu, podczas gdy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `Friend` typy i składniki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Przyjazne zestawy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Porady: tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [-keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Sn.exe (narzędzie silnych nazw)] [Sn.exe (narzędzie silnych nazw)](../../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Pojęcia związane z programowaniem](../../../../visual-basic/programming-guide/concepts/index.md)
