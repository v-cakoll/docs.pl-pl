---
title: 'Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 3db82db502c7404ce235c5824b58046fbd4dbe7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705433"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a>Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (C#)
W tym przykładzie pokazano, jak przyjaznych zestawów za pomocą zestawów o silnych nazwach. Oba zestawy muszą silnej nazwy. Mimo że oba zestawy w tym przykładzie użyć tych samych kluczy, można użyć różnych kluczy dla dwóch zestawów.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Tworzenie zestawu podpisanego za pomocą i zestaw przyjazny  
  
1.  Otwórz wiersz polecenia.  
  
2.  Za pomocą następującej sekwencji poleceń narzędzie silnych nazw do wygenerowania pliku klucza i wyświetlić swój klucz publiczny. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnych nazw)](../../../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1.  Wygeneruj klucz silnej nazwy dla tego przykładu i zapisz go w pliku FriendAssemblies.snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Wyodrębnij klucz publiczny z FriendAssemblies.snk i umieścić go w FriendAssemblies.publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Wyświetl klucz publiczny, przechowywane w pliku FriendAssemblies.publickey:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Utwórz plik języka C# o nazwie `friend_signed_A` zawierający poniższy kod. Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.  
  
     Narzędzie silnych nazw generuje nowy klucz publiczny, za każdym razem, gdy działa. W związku z tym jak pokazano w poniższym przykładzie, za pomocą klucza publicznego, który zostanie wygenerowany, musisz zastąpić klucza publicznego w poniższym kodzie.  
  
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
  
4.  Skompiluj i podpisać friend_signed_A przy użyciu następującego polecenia.  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  Utwórz plik języka C# o nazwie `friend_signed_B` i zawiera następujący kod. Ponieważ friend_signed_A określa friend_signed_B jako zestaw przyjazny, kod w friend_signed_B mogą uzyskiwać dostęp do `internal` typów i elementów członkowskich z friend_signed_A. Plik zawiera następujący kod.  
  
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
  
6.  Skompiluj i podpisać friend_signed_B przy użyciu następującego polecenia.  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     Nazwa zestawu, który został wygenerowany przez kompilator musi odpowiadać przekazany do nazwy przyjaznego zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Należy jawnie określić nazwę zestawu wyjściowego (.exe lub .dll), za pomocą `/out` — opcja kompilatora.  Aby uzyskać więcej informacji, zobacz [/out (opcje kompilatora C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
7.  Uruchom plik friend_signed_B.exe.  
  
     Program wyświetla ciąg "Class1.Test".  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Istnieją podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy. Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> może wymagać uprawnienia zabezpieczeń do uruchamiania w określonej sekcji kodu, natomiast <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `internal` typów i elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Zestawy i Globalna pamięć podręczna zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
- [Przyjazne zestawy (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)
- [Instrukcje: Tworzenie nieoznaczonych przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [/keyfile](../../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [Sn.exe (narzędzie silnych nazw)](../../../../framework/tools/sn-exe-strong-name-tool.md)
- [Tworzenie i używanie zestawów o silnej nazwie](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
