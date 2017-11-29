---
title: "Porady: tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2b2667c60a07a2897a0934d210901042e2e43c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a><span data-ttu-id="b64c4-102">Porady: tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b64c4-102">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="b64c4-103">Ten przykład przedstawia sposób użycia przyjaznych zestawów z zestawów, które nie mają znaku.</span><span class="sxs-lookup"><span data-stu-id="b64c4-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="b64c4-104">Aby utworzyć zestaw i przyjaznego zestawu</span><span class="sxs-lookup"><span data-stu-id="b64c4-104">To create an assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="b64c4-105">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="b64c4-105">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="b64c4-106">Utwórz plik języka Visual Basic, o nazwie `friend_signed_A.` zawierający następujący kod.</span><span class="sxs-lookup"><span data-stu-id="b64c4-106">Create a Visual Basic file named `friend_signed_A.` that contains the following code.</span></span> <span data-ttu-id="b64c4-107">W kodzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b64c4-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' Vbc /target:library friend_unsigned_A.vb  
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
  
3.  <span data-ttu-id="b64c4-108">Skompiluj i podpisz friend_signed_A za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="b64c4-108">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  <span data-ttu-id="b64c4-109">Utwórz plik języka Visual Basic, o nazwie `friend_unsigned_B` zawierający następujący kod.</span><span class="sxs-lookup"><span data-stu-id="b64c4-109">Create a Visual Basic file named `friend_unsigned_B` that contains the following code.</span></span> <span data-ttu-id="b64c4-110">Ponieważ friend_unsigned_A określa friend_unsigned_B jako przyjaznego zestawu, może uzyskać dostęp przez kod friend_unsigned_B `Friend` typów i członków z friend_unsigned_A.</span><span class="sxs-lookup"><span data-stu-id="b64c4-110">Because friend_unsigned_A specifies friend_unsigned_B as a friend assembly, the code in friend_unsigned_B can access `Friend` types and members from friend_unsigned_A.</span></span>  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
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
  
5.  <span data-ttu-id="b64c4-111">Kompiluj friend_signed_B za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="b64c4-111">Compile friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     <span data-ttu-id="b64c4-112">Nazwa zestawu, który jest generowany przez kompilator musi odpowiadać nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b64c4-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="b64c4-113">Należy jawnie określić zestaw przy użyciu `/out` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b64c4-113">You can explicitly set the assembly by using the `/out` compiler option.</span></span>  
  
6.  <span data-ttu-id="b64c4-114">Uruchom plik friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="b64c4-114">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="b64c4-115">Program drukuje dwóch ciągów: "Class1.Test" i "Class2.Test".</span><span class="sxs-lookup"><span data-stu-id="b64c4-115">The program prints two strings: "Class1.Test" and "Class2.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b64c4-116">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b64c4-116">.NET Framework Security</span></span>  
 <span data-ttu-id="b64c4-117">Brak podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="b64c4-117">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="b64c4-118">Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> można zażądać uprawnienia zabezpieczeń do uruchomienia określonej części kodu, podczas gdy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `Friend` typy i składniki.</span><span class="sxs-lookup"><span data-stu-id="b64c4-118">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64c4-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b64c4-119">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="b64c4-120">Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b64c4-120">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="b64c4-121">Przyjazne zestawy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b64c4-121">Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="b64c4-122">Porady: tworzenie oznaczonych przyjaznych zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b64c4-122">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="b64c4-123">Koncepcje Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="b64c4-123">Programming Guide Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
