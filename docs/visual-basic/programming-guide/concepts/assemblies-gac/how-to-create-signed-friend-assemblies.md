---
title: 'Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
ms.openlocfilehash: 20d1bb571d9cd354ea3f3dba560743da00c8bf22
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359019"
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a><span data-ttu-id="df099-102">Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df099-102">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="df099-103">W tym przykładzie pokazano, jak przyjaznych zestawów za pomocą zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="df099-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="df099-104">Oba zestawy muszą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="df099-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="df099-105">Mimo że oba zestawy w tym przykładzie użyć tych samych kluczy, można użyć różnych kluczy dla dwóch zestawów.</span><span class="sxs-lookup"><span data-stu-id="df099-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="df099-106">Tworzenie zestawu podpisanego za pomocą i zestaw przyjazny</span><span class="sxs-lookup"><span data-stu-id="df099-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="df099-107">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="df099-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="df099-108">Za pomocą następującej sekwencji poleceń narzędzie silnych nazw do wygenerowania pliku klucza i wyświetlić swój klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="df099-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="df099-109">Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnych nazw)](../../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="df099-109">For more information, see [Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
    1.  <span data-ttu-id="df099-110">Wygeneruj klucz silnej nazwy dla tego przykładu i zapisz go w pliku FriendAssemblies.snk:</span><span class="sxs-lookup"><span data-stu-id="df099-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="df099-111">Wyodrębnij klucz publiczny z FriendAssemblies.snk i umieścić go w FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="df099-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="df099-112">Wyświetl klucz publiczny, przechowywane w pliku FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="df099-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="df099-113">Utwórz plik w języku Visual Basic o nazwie `friend_signed_A` zawierający poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="df099-113">Create a Visual Basic file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="df099-114">Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="df099-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="df099-115">Narzędzie silnych nazw generuje nowy klucz publiczny, za każdym razem, gdy działa.</span><span class="sxs-lookup"><span data-stu-id="df099-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="df099-116">W związku z tym jak pokazano w poniższym przykładzie, za pomocą klucza publicznego, który zostanie wygenerowany, musisz zastąpić klucza publicznego w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="df099-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  <span data-ttu-id="df099-117">Skompiluj i podpisać friend_signed_A przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="df099-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```console  
    Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  <span data-ttu-id="df099-118">Utwórz plik w języku Visual Basic, który nosi nazwę `friend_signed_B` i zawiera następujący kod.</span><span class="sxs-lookup"><span data-stu-id="df099-118">Create a Visual Basic file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="df099-119">Ponieważ friend_signed_A określa friend_signed_B jako zestaw przyjazny, kod w friend_signed_B mogą uzyskiwać dostęp do `Friend` typów i elementów członkowskich z friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="df099-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `Friend` types and members from friend_signed_A.</span></span> <span data-ttu-id="df099-120">Plik zawiera następujący kod.</span><span class="sxs-lookup"><span data-stu-id="df099-120">The file contains the following code.</span></span>  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="df099-121">Skompiluj i podpisać friend_signed_B przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="df099-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```console  
    vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     <span data-ttu-id="df099-122">Nazwa zestawu, który został wygenerowany przez kompilator musi odpowiadać przekazany do nazwy przyjaznego zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="df099-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="df099-123">Należy jawnie określić zestawu przy użyciu `-out` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="df099-123">You can explicitly set the assembly by using the `-out` compiler option.</span></span> <span data-ttu-id="df099-124">Aby uzyskać więcej informacji, zobacz [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="df099-124">For more information, see [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
7.  <span data-ttu-id="df099-125">Uruchom plik friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="df099-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="df099-126">To pole zawiera ciąg "Class1.Test".</span><span class="sxs-lookup"><span data-stu-id="df099-126">The program displays the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="df099-127">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="df099-127">.NET Framework Security</span></span>  
 <span data-ttu-id="df099-128">Istnieją podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="df099-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="df099-129">Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> może wymagać uprawnienia zabezpieczeń do uruchamiania w określonej sekcji kodu, natomiast <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `Friend` typów i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="df099-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df099-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df099-130">See also</span></span>
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="df099-131">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="df099-131">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="df099-132">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="df099-132">Friend Assemblies</span></span>](../../../../standard/assembly/friend-assemblies.md)
- [<span data-ttu-id="df099-133">Instrukcje: Tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df099-133">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="df099-134">-keyfile</span><span class="sxs-lookup"><span data-stu-id="df099-134">-keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)
- <span data-ttu-id="df099-135">[SN.exe (narzędzie silnych nazw)](../../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="df099-135">[Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
- [<span data-ttu-id="df099-136">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="df099-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="df099-137">Pojęcia związane z programowaniem</span><span class="sxs-lookup"><span data-stu-id="df099-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
