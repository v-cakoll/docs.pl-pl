---
title: 'Instrukcje: Tworzenie podpisanych zestawów zaprzyjaźnionych'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 52ecfbae11c7be125d0e60a0fce6a05182e2db9e
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774362"
---
# <a name="how-to-create-signed-friend-assemblies"></a>Instrukcje: Tworzenie podpisanych zestawów zaprzyjaźnionych
Ten przykład pokazuje, jak używać zespołów zaprzyjaźnionych z zestawami o silnych nazwach. Oba zestawy muszą mieć silną nazwę. Chociaż oba zestawy w tym przykładzie używają tych samych kluczy, można użyć różnych kluczy dla dwóch zestawów.  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a>Tworzenie podpisanego zestawu i zestawu zaprzyjaźnionego  
  
1. Otwórz wiersz polecenia.  
  
2. Użyj następującej sekwencji poleceń za pomocą narzędzia silnej nazwy, aby wygenerować KeyFile i wyświetlić jego klucz publiczny. Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Wygeneruj klucz o silnej nazwie dla tego przykładu i Zapisz go w pliku *FriendAssemblies. snk*:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Wyodrębnij klucz publiczny z *FriendAssemblies. snk* i umieść go w *FriendAssemblies. PublicKey*:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. Wyświetl klucz publiczny przechowywany w pliku *FriendAssemblies. PublicKey*:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Utwórz plik C# lub Visual Basic o nazwie *friend_signed_A* , który zawiera poniższy kod. Kod używa atrybutu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, aby zadeklarować *friend_signed_B* jako zestaw zaprzyjaźniony.  
   
   Narzędzie silnej nazwy generuje nowy klucz publiczny przy każdym uruchomieniu. W związku z tym należy zastąpić klucz publiczny w poniższym kodzie kluczem publicznym, który został właśnie wygenerowany, jak pokazano w poniższym przykładzie.  
   
   ```csharp  
   // friend_signed_A.cs  
   // Compile with:   
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  
   
   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  
   
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
   
4. Kompiluj i podpisz *friend_signed_A* za pomocą następującego polecenia.  
   
   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  
   
   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  
   
5. Utwórz plik C# lub Visual Basic o nazwie *friend_signed_B* , który zawiera poniższy kod. Ponieważ *friend_signed_A* określa *friend_signed_B* jako zestaw zaprzyjaźniony, kod w *friend_signed_B* ma dostęp do `internal` (C#) lub `Friend` (Visual Basic) typów i członków z *friend_signed_A*. Plik zawiera poniższy kod.  
   
   ```csharp  
   // friend_signed_B.cs  
   // Compile with:   
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  
   
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
   
6. Kompiluj i podpisz *friend_signed_B* za pomocą następującego polecenia.  
   
   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  
   
   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  
   
   Nazwa zestawu wygenerowanego przez kompilator musi być zgodna z nazwą znajomego zestawu przekazaną do atrybutu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Należy jawnie określić nazwę zestawu wyjściowego ( *. exe* lub *. dll*) przy użyciu opcji kompilatora `-out`. Aby uzyskać więcej informacji, zobacz [-outC# (opcje kompilatora)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).  
   
7. Uruchom plik *friend_signed_B. exe* .  
   
   Program wyprowadza ciąg **Class1. test**.  
  
## <a name="net-security"></a>Zabezpieczenia platformy .NET  
 Istnieją podobieństwa między atrybutem <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> a klasą <xref:System.Security.Permissions.StrongNameIdentityPermission>. Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> mogą wymagać uprawnień zabezpieczeń do uruchamiania określonej sekcji kodu, natomiast atrybut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> kontroluje widoczność typów i składowych `internal`C#() lub `Friend` (Visual Basic).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Zestawy w środowisku .NET](index.md)
- [Zaprzyjaźnione zestawy](friend.md)
- [Instrukcje: Tworzenie nieoznaczonych zaprzyjaźnionych zestawów](create-unsigned-friend.md)
- [-keyfile (C#)](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [-keyfile (Visual Basic)](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [SN. exe (Narzędzie silnej nazwy)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Tworzenie i używanie zestawów o silnych nazwach](create-use-strong-named.md)
- [C#Przewodnik programowania](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
