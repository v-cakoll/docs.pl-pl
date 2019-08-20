---
title: 'Instrukcje: Utwórz podpisane zaprzyjaźnione zestawyC#()'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 7715726a200150b044fb8e97216fa02d0e784838
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595925"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a>Instrukcje: Utwórz podpisane zaprzyjaźnione zestawyC#()
Ten przykład pokazuje, jak używać zespołów zaprzyjaźnionych z zestawami o silnych nazwach. Oba zestawy muszą mieć silną nazwę. Chociaż oba zestawy w tym przykładzie używają tych samych kluczy, można użyć różnych kluczy dla dwóch zestawów.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Aby utworzyć podpisany zestaw i zestaw zaprzyjaźniony  
  
1. Otwórz wiersz polecenia.  
  
2. Użyj następującej sekwencji poleceń za pomocą narzędzia silnej nazwy, aby wygenerować KeyFile i wyświetlić jego klucz publiczny. Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](../../../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Wygeneruj klucz o silnej nazwie dla tego przykładu i Zapisz go w pliku FriendAssemblies. snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Wyodrębnij klucz publiczny z FriendAssemblies. snk i umieść go w FriendAssemblies. publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. Wyświetl klucz publiczny przechowywany w pliku FriendAssemblies. publickey:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Utwórz C# plik o nazwie `friend_signed_A` , który zawiera następujący kod. Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako zestaw zaprzyjaźniony.  
  
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
  
4. Kompiluj i podpisz friend_signed_A za pomocą następującego polecenia.  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5. Utwórz C# plik o nazwie `friend_signed_B` i zawiera następujący kod. Ponieważ friend_signed_A określa friend_signed_B jako zestaw zaprzyjaźniony, kod w friend_signed_B ma dostęp do `internal` typów i członków z friend_signed_A. Plik zawiera poniższy kod.  
  
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
  
6. Kompiluj i podpisz friend_signed_B za pomocą następującego polecenia.  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     Nazwa zestawu wygenerowanego przez kompilator musi być zgodna z nazwą znajomego zestawu przekazaną <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> do atrybutu. Należy jawnie określić nazwę zestawu wyjściowego (. exe lub. dll) przy użyciu `/out` opcji kompilatora.  Aby uzyskać więcej informacji, zobacz [/outC# (opcje kompilatora)](../../../language-reference/compiler-options/out-compiler-option.md).  
  
7. Uruchom plik friend_signed_B. exe.  
  
     Program drukuje ciąg "Class1. test".  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Istnieją podobieństwa między <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutem <xref:System.Security.Permissions.StrongNameIdentityPermission> a klasą. Główną różnicą jest to <xref:System.Security.Permissions.StrongNameIdentityPermission> , że może to wymagać uprawnień zabezpieczeń do uruchomienia określonej sekcji kodu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> natomiast `internal` atrybut kontroluje widoczność typów i elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
- [Przyjazne zestawy](../../../../standard/assembly/friend-assemblies.md)
- [Instrukcje: Utwórz niepodpisane zestawy zaprzyjaźnione (C#)](./how-to-create-unsigned-friend-assemblies.md)
- [/keyfile](../../../language-reference/compiler-options/keyfile-compiler-option.md)
- [Sn.exe (narzędzie silnych nazw)](../../../../framework/tools/sn-exe-strong-name-tool.md)
- [Tworzenie i używanie zestawów o silnej nazwie](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Przewodnik programowania w języku C#](../../index.md)
