---
title: 'Instrukcje: Utwórz niepodpisane zestawy zaprzyjaźnione'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9d5699f772dba994b10408d15422faa3c5931f45
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991684"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>Instrukcje: Utwórz niepodpisane zestawy zaprzyjaźnione

Ten przykład pokazuje, jak używać zespołów zaprzyjaźnionych z zestawami, które nie są podpisane.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Tworzenie zestawu i zestawu zaprzyjaźnionego

1. Otwórz wiersz polecenia.

2. Utwórz plik C# lub Visual Basic o nazwie *friend_unsigned_A* , który zawiera poniższy kod. Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować *friend_unsigned_B* jako zestaw zaprzyjaźniony.

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

3. Kompiluj i podpisz *friend_unsigned_A* za pomocą następującego polecenia:

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Utwórz plik C# lub Visual Basic o nazwie *friend_unsigned_B* , który zawiera poniższy kod. Ponieważ *friend_unsigned_A* określa *friend_unsigned_B* jako zestaw zaprzyjaźniony, kod w *friend_unsigned_B* ma dostęp `internal` (C#) lub `Friend` (Visual Basic) typów i składowych z *friend_unsigned_A* .

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

5. Kompiluj *friend_unsigned_B* przy użyciu następującego polecenia.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   Nazwa zestawu, który jest generowany przez kompilator musi być zgodna z nazwą zestawu zaprzyjaźnionego, który jest przesyłany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Należy jawnie określić nazwę zestawu wyjściowego ( *. exe* lub *. dll*) przy użyciu `/out` opcji kompilatora. Aby uzyskać więcej informacji, zobacz [/outC# (opcje kompilatora)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..

6. Uruchom plik *friend_unsigned_B. exe* .

   Program wyprowadza dwa ciągi znaków: **Class1. test** i **'klasa. test**.

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Istnieją podobieństwa między <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutem <xref:System.Security.Permissions.StrongNameIdentityPermission> a klasą. Główną różnicą jest to <xref:System.Security.Permissions.StrongNameIdentityPermission> , że może to wymagać uprawnień zabezpieczeń do uruchomienia określonej sekcji kodu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> natomiast `internal` atrybut `Friend` kontroluje widoczność typów i składowych (Visual Basic).

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Zestawy w środowisku .NET](index.md)
- [Zaprzyjaźnione zestawy](friend.md)
- [Instrukcje: Utwórz podpisane zaprzyjaźnione zestawy](create-signed-friend.md)
- [C#Przewodnik programowania](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
