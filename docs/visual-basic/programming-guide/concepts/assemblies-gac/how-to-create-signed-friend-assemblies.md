---
title: 'Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
ms.openlocfilehash: 4ff32015647a565f7f68e944ae028deb7f738e28
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324672"
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (Visual Basic)
W tym przykładzie pokazano, jak przyjaznych zestawów za pomocą zestawów o silnych nazwach. Oba zestawy muszą silnej nazwy. Mimo że oba zestawy w tym przykładzie użyć tych samych kluczy, można użyć różnych kluczy dla dwóch zestawów.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Tworzenie zestawu podpisanego za pomocą i zestaw przyjazny  
  
1. Otwórz wiersz polecenia.  
  
2. Za pomocą następującej sekwencji poleceń narzędzie silnych nazw do wygenerowania pliku klucza i wyświetlić swój klucz publiczny. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnych nazw)](../../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
    1.  Wygeneruj klucz silnej nazwy dla tego przykładu i zapisz go w pliku FriendAssemblies.snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Wyodrębnij klucz publiczny z FriendAssemblies.snk i umieścić go w FriendAssemblies.publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Wyświetl klucz publiczny, przechowywane w pliku FriendAssemblies.publickey:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Utwórz plik w języku Visual Basic o nazwie `friend_signed_A` zawierający poniższy kod. Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.  
  
     Narzędzie silnych nazw generuje nowy klucz publiczny, za każdym razem, gdy działa. W związku z tym jak pokazano w poniższym przykładzie, za pomocą klucza publicznego, który zostanie wygenerowany, musisz zastąpić klucza publicznego w poniższym kodzie.  
  
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
  
4. Skompiluj i podpisać friend_signed_A przy użyciu następującego polecenia.  
  
    ```console  
    Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5. Utwórz plik w języku Visual Basic, który nosi nazwę `friend_signed_B` i zawiera następujący kod. Ponieważ friend_signed_A określa friend_signed_B jako zestaw przyjazny, kod w friend_signed_B mogą uzyskiwać dostęp do `Friend` typów i elementów członkowskich z friend_signed_A. Plik zawiera następujący kod.  
  
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
  
6. Skompiluj i podpisać friend_signed_B przy użyciu następującego polecenia.  
  
    ```console  
    vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     Nazwa zestawu, który został wygenerowany przez kompilator musi odpowiadać przekazany do nazwy przyjaznego zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Należy jawnie określić zestawu przy użyciu `-out` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
7. Uruchom plik friend_signed_B.exe.  
  
     To pole zawiera ciąg "Class1.Test".  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Istnieją podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy. Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> może wymagać uprawnienia zabezpieczeń do uruchamiania w określonej sekcji kodu, natomiast <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `Friend` typów i elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
- [Przyjazne zestawy](../../../../standard/assembly/friend-assemblies.md)
- [Instrukcje: Tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [-keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [SN.exe (narzędzie silnych nazw)](../../../../framework/tools/sn-exe-strong-name-tool.md))
- [Tworzenie i używanie zestawów o silnej nazwie](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Pojęcia związane z programowaniem](../../../../visual-basic/programming-guide/concepts/index.md)
