---
title: 'Porady: tworzenie oznaczonych przyjaznych zestawów (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 34243a65f57f41c358439baac82a1ce169233259
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="2bcc5-102">Porady: tworzenie oznaczonych przyjaznych zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcc5-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="2bcc5-103">Ten przykład przedstawia sposób użycia przyjaznych zestawów z zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="2bcc5-104">Oba zestawy muszą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="2bcc5-105">Mimo że oba zestawy w tym przykładzie używają tych samych kluczy, można użyć różnych kluczy dla dwóch zestawów.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="2bcc5-106">Aby utworzyć podpisanych zestawów i przyjaznego zestawu</span><span class="sxs-lookup"><span data-stu-id="2bcc5-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="2bcc5-107">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="2bcc5-108">Aby wygenerować plik klucza i wyświetlić jego klucz publiczny, użyj następującej procedury poleceń za pomocą narzędzia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="2bcc5-109">Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnej nazwy)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="2bcc5-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="2bcc5-110">Generowanie klucza silnej nazwy, w tym przykładzie i zapisze go w pliku FriendAssemblies.snk:</span><span class="sxs-lookup"><span data-stu-id="2bcc5-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="2bcc5-111">Wyodrębniania klucza publicznego z FriendAssemblies.snk i poddane FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="2bcc5-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="2bcc5-112">Klucz publiczny, przechowywane w pliku FriendAssemblies.publickey do wyświetlenia:</span><span class="sxs-lookup"><span data-stu-id="2bcc5-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="2bcc5-113">Utwórz plik C# o nazwie `friend_signed_A` zawierający następujący kod.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="2bcc5-114">W kodzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="2bcc5-115">Przez narzędzie Strong Name generuje nowy klucz publiczny w każdym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="2bcc5-116">W związku z tym musisz zastąpić klucz publiczny w poniższym kodzie klucza publicznego, który zostanie wygenerowany, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="2bcc5-117">Skompiluj i podpisz friend_signed_A za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  <span data-ttu-id="2bcc5-118">Tworzenie pliku C# o nazwie `friend_signed_B` i zawiera następujący kod.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="2bcc5-119">Ponieważ friend_signed_A określa friend_signed_B jako przyjaznego zestawu, może uzyskać dostęp przez kod friend_signed_B `internal` typów i członków z friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="2bcc5-120">Plik zawiera następujący kod.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-120">The file contains the following code.</span></span>  
  
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
  
6.  <span data-ttu-id="2bcc5-121">Skompiluj i podpisz friend_signed_B za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="2bcc5-122">Nazwa zestawu generowane przez kompilator musi odpowiadać przekazany do nazwy przyjaznego zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="2bcc5-123">Należy jawnie określić nazwę zestawu wyjściowego (.exe lub .dll) przy użyciu `/out` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="2bcc5-124">Aby uzyskać więcej informacji, zobacz [/out (opcje kompilatora C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2bcc5-124">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7.  <span data-ttu-id="2bcc5-125">Uruchom plik friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="2bcc5-126">Program drukuje ciąg "Class1.Test".</span><span class="sxs-lookup"><span data-stu-id="2bcc5-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2bcc5-127">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2bcc5-127">.NET Framework Security</span></span>  
 <span data-ttu-id="2bcc5-128">Brak podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="2bcc5-129">Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> można zażądać uprawnienia zabezpieczeń do uruchomienia określonej części kodu, podczas gdy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `internal` typy i składniki.</span><span class="sxs-lookup"><span data-stu-id="2bcc5-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bcc5-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bcc5-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="2bcc5-131">Zestawy i Globalna pamięć podręczna zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcc5-131">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="2bcc5-132">Przyjazne zestawy (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcc5-132">Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="2bcc5-133">Porady: tworzenie nieoznaczonych przyjaznych zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="2bcc5-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="2bcc5-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="2bcc5-134">/keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="2bcc5-135">Sn.exe (narzędzie silnych nazw)</span><span class="sxs-lookup"><span data-stu-id="2bcc5-135">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="2bcc5-136">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="2bcc5-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="2bcc5-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2bcc5-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
