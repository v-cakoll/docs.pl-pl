---
title: 'Instrukcje: Tworzenie nieoznaczonych zaprzyjaźnionych zestawów'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: f8fec064507553b8208083578165965de2303a33
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352434"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="c86ad-102">Instrukcje: Tworzenie nieoznaczonych zaprzyjaźnionych zestawów</span><span class="sxs-lookup"><span data-stu-id="c86ad-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="c86ad-103">Ten przykład pokazuje, jak używać zespołów zaprzyjaźnionych z zestawami, które nie są podpisane.</span><span class="sxs-lookup"><span data-stu-id="c86ad-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="c86ad-104">Tworzenie zestawu i zestawu zaprzyjaźnionego</span><span class="sxs-lookup"><span data-stu-id="c86ad-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="c86ad-105">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="c86ad-105">Open a command prompt.</span></span>

2. <span data-ttu-id="c86ad-106">Utwórz plik C# lub Visual Basic o nazwie *friend_unsigned_A* , który zawiera poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="c86ad-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="c86ad-107">Kod używa atrybutu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, aby zadeklarować *friend_unsigned_B* jako zestaw zaprzyjaźniony.</span><span class="sxs-lookup"><span data-stu-id="c86ad-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="c86ad-108">Kompiluj i podpisz *friend_unsigned_A* przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c86ad-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="c86ad-109">Utwórz plik C# lub Visual Basic o nazwie *friend_unsigned_B* , który zawiera poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="c86ad-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="c86ad-110">Ponieważ *friend_unsigned_A* określa *friend_unsigned_B* jako zestaw zaprzyjaźniony, kod w *friend_unsigned_B* może uzyskać dostęp do `internal`C#() lub `Friend` (Visual Basic) typów i członków z *friend_unsigned_A*.</span><span class="sxs-lookup"><span data-stu-id="c86ad-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="c86ad-111">Kompiluj *friend_unsigned_B* przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c86ad-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="c86ad-112">Nazwa zestawu, który jest generowany przez kompilator musi być zgodna z nazwą zestawu zaprzyjaźnionego, która jest przesyłana do atrybutu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c86ad-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="c86ad-113">Należy jawnie określić nazwę zestawu wyjściowego ( *. exe* lub *. dll*) przy użyciu opcji kompilatora `-out`.</span><span class="sxs-lookup"><span data-stu-id="c86ad-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="c86ad-114">Aby uzyskać więcej informacji, zobacz [-outC# (opcje kompilatora)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span><span class="sxs-lookup"><span data-stu-id="c86ad-114">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="c86ad-115">Uruchom plik *friend_unsigned_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="c86ad-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="c86ad-116">Program wyprowadza dwa ciągi: **Class1. test** i **'klasa. test**.</span><span class="sxs-lookup"><span data-stu-id="c86ad-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="c86ad-117">Zabezpieczenia platformy .NET</span><span class="sxs-lookup"><span data-stu-id="c86ad-117">.NET security</span></span>

<span data-ttu-id="c86ad-118">Istnieją podobieństwa między atrybutem <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> a klasą <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="c86ad-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="c86ad-119">Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> mogą wymagać uprawnień zabezpieczeń do uruchamiania określonej sekcji kodu, natomiast atrybut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> kontroluje widoczność typów i składowych `internal` lub `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c86ad-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="c86ad-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c86ad-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="c86ad-121">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="c86ad-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="c86ad-122">Zaprzyjaźnione zestawy</span><span class="sxs-lookup"><span data-stu-id="c86ad-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="c86ad-123">Instrukcje: Tworzenie podpisanych zestawów zaprzyjaźnionych</span><span class="sxs-lookup"><span data-stu-id="c86ad-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="c86ad-124">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="c86ad-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c86ad-125">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c86ad-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
