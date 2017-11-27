---
title: "Porady: tworzenie oznaczonych przyjaznych zestawów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f87f816992bdfa9ed347c35ba651c59187551772
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a><span data-ttu-id="064b8-102">Porady: tworzenie oznaczonych przyjaznych zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="064b8-102">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="064b8-103">Ten przykład przedstawia sposób użycia przyjaznych zestawów z zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="064b8-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="064b8-104">Oba zestawy muszą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="064b8-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="064b8-105">Mimo że oba zestawy w tym przykładzie używają tych samych kluczy, można użyć różnych kluczy dla dwóch zestawów.</span><span class="sxs-lookup"><span data-stu-id="064b8-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="064b8-106">Aby utworzyć podpisanych zestawów i przyjaznego zestawu</span><span class="sxs-lookup"><span data-stu-id="064b8-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="064b8-107">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="064b8-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="064b8-108">Aby wygenerować plik klucza i wyświetlić jego klucz publiczny, użyj następującej procedury poleceń za pomocą narzędzia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="064b8-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="064b8-109">Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnej nazwy)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="064b8-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="064b8-110">Generowanie klucza silnej nazwy, w tym przykładzie i zapisze go w pliku FriendAssemblies.snk:</span><span class="sxs-lookup"><span data-stu-id="064b8-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="064b8-111">Wyodrębniania klucza publicznego z FriendAssemblies.snk i poddane FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="064b8-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="064b8-112">Klucz publiczny, przechowywane w pliku FriendAssemblies.publickey do wyświetlenia:</span><span class="sxs-lookup"><span data-stu-id="064b8-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="064b8-113">Utwórz plik języka Visual Basic, o nazwie `friend_signed_A` zawierający następujący kod.</span><span class="sxs-lookup"><span data-stu-id="064b8-113">Create a Visual Basic file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="064b8-114">W kodzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="064b8-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="064b8-115">Przez narzędzie Strong Name generuje nowy klucz publiczny w każdym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="064b8-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="064b8-116">W związku z tym musisz zastąpić klucz publiczny w poniższym kodzie klucza publicznego, który zostanie wygenerowany, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="064b8-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  <span data-ttu-id="064b8-117">Skompiluj i podpisz friend_signed_A za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="064b8-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  <span data-ttu-id="064b8-118">Utwórz plik języka Visual Basic, o nazwie `friend_signed_B` i zawiera następujący kod.</span><span class="sxs-lookup"><span data-stu-id="064b8-118">Create a Visual Basic file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="064b8-119">Ponieważ friend_signed_A określa friend_signed_B jako przyjaznego zestawu, może uzyskać dostęp przez kod friend_signed_B `Friend` typów i członków z friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="064b8-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `Friend` types and members from friend_signed_A.</span></span> <span data-ttu-id="064b8-120">Plik zawiera następujący kod.</span><span class="sxs-lookup"><span data-stu-id="064b8-120">The file contains the following code.</span></span>  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="064b8-121">Skompiluj i podpisz friend_signed_B za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="064b8-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     <span data-ttu-id="064b8-122">Nazwa zestawu generowane przez kompilator musi odpowiadać przekazany do nazwy przyjaznego zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="064b8-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="064b8-123">Należy jawnie określić zestaw przy użyciu `/out` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="064b8-123">You can explicitly set the assembly by using the `/out` compiler option.</span></span> <span data-ttu-id="064b8-124">Aby uzyskać więcej informacji, zobacz [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="064b8-124">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
7.  <span data-ttu-id="064b8-125">Uruchom plik friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="064b8-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="064b8-126">Program drukuje ciąg "Class1.Test".</span><span class="sxs-lookup"><span data-stu-id="064b8-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="064b8-127">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="064b8-127">.NET Framework Security</span></span>  
 <span data-ttu-id="064b8-128">Brak podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="064b8-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="064b8-129">Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> można zażądać uprawnienia zabezpieczeń do uruchomienia określonej części kodu, podczas gdy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `Friend` typy i składniki.</span><span class="sxs-lookup"><span data-stu-id="064b8-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064b8-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="064b8-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="064b8-131">Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="064b8-131">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="064b8-132">Przyjazne zestawy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="064b8-132">Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="064b8-133">Porady: tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="064b8-133">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="064b8-134">/ KeyFile</span><span class="sxs-lookup"><span data-stu-id="064b8-134">/keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="064b8-135">SN.exe (narzędzie silnych nazw)</span><span class="sxs-lookup"><span data-stu-id="064b8-135">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="064b8-136">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="064b8-136">Creating and Using Strong-Named Assemblies</span></span>](https://msdn.microsoft.com/library/xwb8f617)  
 [<span data-ttu-id="064b8-137">Koncepcje programowania</span><span class="sxs-lookup"><span data-stu-id="064b8-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
