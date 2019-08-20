---
title: 'Instrukcje: Utwórz niepodpisane zestawy zaprzyjaźnione (C#)'
ms.date: 07/20/2015
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
ms.openlocfilehash: 5dadd725234048c4b6a4f9a0fa9b38dbf92671aa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595919"
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>Instrukcje: Utwórz niepodpisane zestawy zaprzyjaźnione (C#)
Ten przykład pokazuje, jak używać zespołów zaprzyjaźnionych z zestawami, które nie są podpisane.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Aby utworzyć zestaw i zestaw zaprzyjaźniony  
  
1. Otwórz wiersz polecenia.  
  
2. Utwórz C# plik o nazwie `friend_unsigned_A.` , który zawiera następujący kod. Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_unsigned_B jako zestaw zaprzyjaźniony.  
  
    ```csharp  
    // friend_unsigned_A.cs  
    // Compile with:   
    // csc /target:library friend_unsigned_A.cs  
    using System.Runtime.CompilerServices;  
    using System;  
  
    [assembly: InternalsVisibleTo("friend_unsigned_B")]  
  
    // Type is internal by default.  
    class Class1  
    {  
        public void Test()  
        {  
            Console.WriteLine("Class1.Test");  
        }  
    }  
  
    // Public type with internal member.  
    public class Class2  
    {  
        internal void Test()  
        {  
            Console.WriteLine("Class2.Test");  
        }  
    }  
    ```  
  
3. Kompiluj i podpisz friend_unsigned_A za pomocą następującego polecenia.  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4. Utwórz C# plik o nazwie `friend_unsigned_B` , który zawiera następujący kod. Ponieważ friend_unsigned_A określa friend_unsigned_B jako zestaw zaprzyjaźniony, kod w friend_unsigned_B ma dostęp do `internal` typów i członków z friend_unsigned_A.  
  
    ```csharp  
    // friend_unsigned_B.cs  
    // Compile with:   
    // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            // Access an internal type.  
            Class1 inst1 = new Class1();  
            inst1.Test();  
  
            Class2 inst2 = new Class2();  
            // Access an internal member of a public type.  
            inst2.Test();  
  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
5. Kompiluj friend_unsigned_B przy użyciu następującego polecenia.  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     Nazwa zestawu, który jest generowany przez kompilator musi być zgodna z nazwą zestawu zaprzyjaźnionego, który jest przesyłany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Należy jawnie określić nazwę zestawu wyjściowego (. exe lub. dll) przy użyciu `/out` opcji kompilatora. Aby uzyskać więcej informacji, zobacz [/outC# (opcje kompilatora)](../../../language-reference/compiler-options/out-compiler-option.md).  
  
6. Uruchom plik friend_unsigned_B. exe.  
  
     Program drukuje dwa ciągi: "Class1. test" i "'Klasa. test".  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Istnieją podobieństwa między <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutem <xref:System.Security.Permissions.StrongNameIdentityPermission> a klasą. Główną różnicą jest to <xref:System.Security.Permissions.StrongNameIdentityPermission> , że może to wymagać uprawnień zabezpieczeń do uruchomienia określonej sekcji kodu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> natomiast `internal` atrybut kontroluje widoczność typów i elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
- [Przyjazne zestawy](../../../../standard/assembly/friend-assemblies.md)
- [Instrukcje: Utwórz podpisane zaprzyjaźnione zestawyC#()](./how-to-create-signed-friend-assemblies.md)
- [Przewodnik programowania w języku C#](../../index.md)
