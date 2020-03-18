---
title: 'Jak: Tworzenie niepodpisanych zestawów znajomych'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: f8fec064507553b8208083578165965de2303a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352434"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>Jak: Tworzenie niepodpisanych zestawów znajomych

W tym przykładzie pokazano, jak używać zestawów znajomych z zestawami, które są niepodpisane.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Tworzenie złożenia i złożenia znajomego

1. Otwórz wiersz polecenia.

2. Utwórz plik Języka C# lub Visual Basic o nazwie *friend_unsigned_A* zawierający następujący kod. Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu do deklarowania *friend_unsigned_B* jako zestawu znajomego.

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

3. Skompiluj i podpisuj *friend_unsigned_A* za pomocą następującego polecenia:

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Utwórz plik Języka C# lub Visual Basic o nazwie *friend_unsigned_B* zawierający następujący kod. Ponieważ *friend_unsigned_A* określa *friend_unsigned_B* jako zestaw znajomego, kod w *friend_unsigned_B* można uzyskać `internal` dostęp (C#) lub `Friend` (Visual Basic) typów i elementów członkowskich z *friend_unsigned_A*.

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

5. Skompiluj *friend_unsigned_B* przy użyciu następującego polecenia.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   Nazwa zestawu, który jest generowany przez kompilator musi odpowiadać nazwę <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zestawu znajomego, który jest przekazywany do atrybutu. Należy jawnie określić nazwę zestawu wyjściowego (*.exe* lub *.dll*) przy użyciu opcji kompilatora. `-out` Aby uzyskać więcej informacji, zobacz [-out (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [-out (Visual Basic).](../../visual-basic/reference/command-line-compiler/out.md)

6. Uruchom plik *friend_unsigned_B.exe.*

   Program wyprowadza dwa ciągi: **Class1.Test** i **Class2.Test**.

## <a name="net-security"></a>Zabezpieczenia .NET

Istnieją podobieństwa między <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutem <xref:System.Security.Permissions.StrongNameIdentityPermission> a klasą. Główną różnicą <xref:System.Security.Permissions.StrongNameIdentityPermission> jest to, że może żądać uprawnień zabezpieczeń <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> do uruchamiania `internal` określonej `Friend` sekcji kodu, podczas gdy atrybut kontroluje widoczność lub (Visual Basic) typy i elementy członkowskie.

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Zestawy w środowisku .NET](index.md)
- [Przyjazne zestawy](friend.md)
- [Jak: Tworzenie podpisanych zestawów znajomych](create-signed-friend.md)
- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
