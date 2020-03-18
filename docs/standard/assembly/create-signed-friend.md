---
title: 'Jak: Tworzenie podpisanych zestawów znajomych'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159497"
---
# <a name="how-to-create-signed-friend-assemblies"></a>Jak: Tworzenie podpisanych zestawów znajomych
W tym przykładzie pokazano, jak używać zestawów znajomych z zestawami, które mają silne nazwy. Oba zestawy muszą być silne nazwane. Chociaż oba zestawy w tym przykładzie używają tych samych kluczy, można użyć różnych kluczy dla dwóch zestawów.  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a>Tworzenie podpisanego zestawu i zestawu znajomych  
  
1. Otwórz wiersz polecenia.  
  
2. Użyj następującej sekwencji poleceń za pomocą narzędzia Silna nazwa, aby wygenerować plik klucza i wyświetlić jego klucz publiczny. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie Silna nazwa)](../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Wygeneruj klucz o silnej nazwie dla tego przykładu i zapisz go w pliku *FriendAssemblies.snk:*  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Wyodrębnij klucz publiczny z *FriendAssemblies.snk* i umieścić go w *FriendAssemblies.publickey:*  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. Wyświetlanie klucza publicznego przechowywanego w pliku *FriendAssemblies.publickey:*  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Utwórz plik Języka C# lub Visual Basic o nazwie *friend_signed_A* zawierający następujący kod. Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu do deklarowania *friend_signed_B* jako zestawu znajomego.  

   Narzędzie Silna nazwa generuje nowy klucz publiczny za każdym razem, gdy jest uruchamiany. W związku z tym należy zastąpić klucz publiczny w poniższym kodzie kluczem publicznym, który właśnie wygenerowałeś, jak pokazano w poniższym przykładzie.  

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

4. Skompiluj i podpisuj *friend_signed_A* przy użyciu następującego polecenia.  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. Utwórz plik Języka C# lub Visual Basic o nazwie *friend_signed_B* zawierający następujący kod. Ponieważ *friend_signed_A* określa *friend_signed_B* jako zestaw znajomego, kod w *friend_signed_B* można uzyskać `internal` dostęp (C#) lub `Friend` (Visual Basic) typów i elementów członkowskich z *friend_signed_A*. Plik zawiera następujący kod.  

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

6. Skompiluj i podpisz *friend_signed_B* przy użyciu następującego polecenia.  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   Nazwa zestawu generowanego przez kompilator musi odpowiadać nazwie <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zestawu znajomego przekazanej do atrybutu. Należy jawnie określić nazwę zestawu wyjściowego (*.exe* lub *.dll*) przy użyciu opcji kompilatora. `-out` Aby uzyskać więcej informacji, zobacz [-out (opcje kompilatora Języka C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [-out (Visual Basic).](../../visual-basic/reference/command-line-compiler/out.md)  

7. Uruchom plik *friend_signed_B.exe.*  

   Program wyprowadza ciąg **Class1.Test**.  
  
## <a name="net-security"></a>Zabezpieczenia .NET  
 Istnieją podobieństwa między <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutem <xref:System.Security.Permissions.StrongNameIdentityPermission> a klasą. Główną różnicą <xref:System.Security.Permissions.StrongNameIdentityPermission> jest to, że może żądać uprawnień zabezpieczeń <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> do uruchamiania `internal` określonej sekcji kodu, podczas gdy atrybut kontroluje widoczność (C#) lub `Friend` (Visual Basic) typów i elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Zestawy w środowisku .NET](index.md)
- [Przyjazne zestawy](friend.md)
- [Jak: Tworzenie niepodpisanych zestawów znajomych](create-unsigned-friend.md)
- [-keyfile (C#)](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [-keyfile (Visual Basic)](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn.exe (narzędzie Silna nazwa)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
