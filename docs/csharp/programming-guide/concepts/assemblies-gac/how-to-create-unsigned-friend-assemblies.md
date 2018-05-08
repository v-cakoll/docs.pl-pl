---
title: 'Porady: tworzenie nieoznaczonych przyjaznych zestawów (C#)'
ms.date: 07/20/2015
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
ms.openlocfilehash: 676b9d3c641f45736af50bc2290426e261b591c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>Porady: tworzenie nieoznaczonych przyjaznych zestawów (C#)
Ten przykład przedstawia sposób użycia przyjaznych zestawów z zestawów, które nie mają znaku.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Aby utworzyć zestaw i przyjaznego zestawu  
  
1.  Otwórz wiersz polecenia.  
  
2.  Utwórz plik C# o nazwie `friend_signed_A.` zawierający następujący kod. W kodzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.  
  
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
  
3.  Skompiluj i podpisz friend_signed_A za pomocą następującego polecenia.  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  Utwórz plik C# o nazwie `friend_unsigned_B` zawierający następujący kod. Ponieważ friend_unsigned_A określa friend_unsigned_B jako przyjaznego zestawu, może uzyskać dostęp przez kod friend_unsigned_B `internal` typów i członków z friend_unsigned_A.  
  
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
  
5.  Kompiluj friend_signed_B za pomocą następującego polecenia.  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     Nazwa zestawu, który jest generowany przez kompilator musi odpowiadać nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Należy jawnie określić nazwę zestawu wyjściowego (.exe lub .dll) przy użyciu `/out` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [/out (opcje kompilatora C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
6.  Uruchom plik friend_signed_B.exe.  
  
     Program drukuje dwóch ciągów: "Class1.Test" i "Class2.Test".  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Brak podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy. Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> można zażądać uprawnienia zabezpieczeń do uruchomienia określonej części kodu, podczas gdy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `internal` typy i składniki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Zestawy i Globalna pamięć podręczna zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Przyjazne zestawy (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Porady: tworzenie oznaczonych przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
