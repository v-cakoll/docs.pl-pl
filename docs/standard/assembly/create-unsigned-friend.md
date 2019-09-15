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
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="13d2f-102">Instrukcje: Utwórz niepodpisane zestawy zaprzyjaźnione</span><span class="sxs-lookup"><span data-stu-id="13d2f-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="13d2f-103">Ten przykład pokazuje, jak używać zespołów zaprzyjaźnionych z zestawami, które nie są podpisane.</span><span class="sxs-lookup"><span data-stu-id="13d2f-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="13d2f-104">Tworzenie zestawu i zestawu zaprzyjaźnionego</span><span class="sxs-lookup"><span data-stu-id="13d2f-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="13d2f-105">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="13d2f-105">Open a command prompt.</span></span>

2. <span data-ttu-id="13d2f-106">Utwórz plik C# lub Visual Basic o nazwie *friend_unsigned_A* , który zawiera poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="13d2f-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="13d2f-107">Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować *friend_unsigned_B* jako zestaw zaprzyjaźniony.</span><span class="sxs-lookup"><span data-stu-id="13d2f-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="13d2f-108">Kompiluj i podpisz *friend_unsigned_A* za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="13d2f-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="13d2f-109">Utwórz plik C# lub Visual Basic o nazwie *friend_unsigned_B* , który zawiera poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="13d2f-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="13d2f-110">Ponieważ *friend_unsigned_A* określa *friend_unsigned_B* jako zestaw zaprzyjaźniony, kod w *friend_unsigned_B* ma dostęp `internal` (C#) lub `Friend` (Visual Basic) typów i składowych z *friend_unsigned_A* .</span><span class="sxs-lookup"><span data-stu-id="13d2f-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="13d2f-111">Kompiluj *friend_unsigned_B* przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="13d2f-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="13d2f-112">Nazwa zestawu, który jest generowany przez kompilator musi być zgodna z nazwą zestawu zaprzyjaźnionego, który jest przesyłany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="13d2f-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="13d2f-113">Należy jawnie określić nazwę zestawu wyjściowego ( *. exe* lub *. dll*) przy użyciu `/out` opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="13d2f-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `/out` compiler option.</span></span> <span data-ttu-id="13d2f-114">Aby uzyskać więcej informacji, zobacz [/outC# (opcje kompilatora)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span><span class="sxs-lookup"><span data-stu-id="13d2f-114">For more information, see [/out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="13d2f-115">Uruchom plik *friend_unsigned_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="13d2f-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="13d2f-116">Program wyprowadza dwa ciągi znaków: **Class1. test** i **'klasa. test**.</span><span class="sxs-lookup"><span data-stu-id="13d2f-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="13d2f-117">Zabezpieczenia platformy .NET</span><span class="sxs-lookup"><span data-stu-id="13d2f-117">.NET security</span></span>

<span data-ttu-id="13d2f-118">Istnieją podobieństwa między <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutem <xref:System.Security.Permissions.StrongNameIdentityPermission> a klasą.</span><span class="sxs-lookup"><span data-stu-id="13d2f-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="13d2f-119">Główną różnicą jest to <xref:System.Security.Permissions.StrongNameIdentityPermission> , że może to wymagać uprawnień zabezpieczeń do uruchomienia określonej sekcji kodu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> natomiast `internal` atrybut `Friend` kontroluje widoczność typów i składowych (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="13d2f-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="13d2f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13d2f-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="13d2f-121">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="13d2f-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="13d2f-122">Zaprzyjaźnione zestawy</span><span class="sxs-lookup"><span data-stu-id="13d2f-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="13d2f-123">Instrukcje: Utwórz podpisane zaprzyjaźnione zestawy</span><span class="sxs-lookup"><span data-stu-id="13d2f-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="13d2f-124">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="13d2f-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="13d2f-125">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13d2f-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
