---
title: "Porady: tworzenie obiektów GenericPrincipal i GenericIdentity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b10029c8b290ffaaa4a858fe3e5a6315031f1bab
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="bb8aa-102">Porady: tworzenie obiektów GenericPrincipal i GenericIdentity</span><span class="sxs-lookup"><span data-stu-id="bb8aa-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>
<span data-ttu-id="bb8aa-103">Można użyć <xref:System.Security.Principal.GenericIdentity> klasy w połączeniu z <xref:System.Security.Principal.GenericPrincipal> klasę, aby utworzyć schemat autoryzacji, czy istnieje niezależnie od domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>  
  
### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="bb8aa-104">Do tworzenia obiektu GenericPrincipal</span><span class="sxs-lookup"><span data-stu-id="bb8aa-104">To create a GenericPrincipal object</span></span>  
  
1.  <span data-ttu-id="bb8aa-105">Utwórz nowe wystąpienie klasy tożsamości i zainicjować go o nazwie ma być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="bb8aa-106">Poniższy kod tworzy nową **genericidentity —** obiektu i inicjuje go o nazwie `MyUser`.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  <span data-ttu-id="bb8aa-107">Utwórz nowe wystąpienie klasy **GenericPrincipal** klasy i zainicjować go z utworzonej wcześniej **genericidentity —** obiekt i Tablica ciągów, które reprezentują role, które mają skojarzone z tego podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="bb8aa-108">Poniższy przykład kodu Określa tablicę ciągów reprezentujących rolą administratora oraz roli użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="bb8aa-109">**GenericPrincipal** następnie jest inicjowany z poprzedniej **genericidentity —** i tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  <span data-ttu-id="bb8aa-110">Użyć poniższego kodu do dołączenia do podmiotu zabezpieczeń do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="bb8aa-111">Jest to przydatne w sytuacjach, w których podmiot zabezpieczeń musi zostać zweryfikowany kilka razy, musi zostać zweryfikowany przez inny kod w aplikacji lub musi zostać zweryfikowany przez <xref:System.Security.Permissions.PrincipalPermission> obiektu.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="bb8aa-112">Może nadal wykonywać walidacji opartej na rolach na obiekt główny bez dołączeniu go do wątku.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="bb8aa-113">Aby uzyskać więcej informacji, zobacz [zastępowanie obiektu głównego](../../../docs/standard/security/replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="bb8aa-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## <a name="example"></a><span data-ttu-id="bb8aa-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb8aa-114">Example</span></span>  
 <span data-ttu-id="bb8aa-115">Poniższy przykładowy kod przedstawia sposób tworzenia wystąpienia **GenericPrincipal** i **genericidentity —**.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="bb8aa-116">Ten kod wyświetla wartości z tych obiektów do konsoli.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-116">This code displays the values of these objects to the console.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Principal  
Imports System.Threading  
  
Public Class Class1  
  
    Public Shared Sub Main()  
        ' Create generic identity.  
        Dim MyIdentity As New GenericIdentity("MyIdentity")  
  
        ' Create generic principal.  
        Dim MyStringArray As String() =  {"Manager", "Teller"}  
        Dim MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
  
        ' Attach the principal to the current thread.  
        ' This is not required unless repeated validation must occur,  
        ' other code in your application must validate, or the   
        ' PrincipalPermisson object is used.   
        Thread.CurrentPrincipal = MyPrincipal  
  
        ' Print values to the console.  
        Dim Name As String = MyPrincipal.Identity.Name  
        Dim Auth As Boolean = MyPrincipal.Identity.IsAuthenticated  
        Dim IsInRole As Boolean = MyPrincipal.IsInRole("Manager")  
  
        Console.WriteLine("The Name is: {0}", Name)  
        Console.WriteLine("The IsAuthenticated is: {0}", Auth)  
        Console.WriteLine("Is this a Manager? {0}", IsInRole)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Security.Principal;  
using System.Threading;  
  
public class Class1  
{  
    public static int Main(string[] args)  
    {  
    // Create generic identity.  
    GenericIdentity MyIdentity = new GenericIdentity("MyIdentity");  
  
    // Create generic principal.  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal =   
        new GenericPrincipal(MyIdentity, MyStringArray);  
  
    // Attach the principal to the current thread.  
    // This is not required unless repeated validation must occur,  
    // other code in your application must validate, or the   
    // PrincipalPermisson object is used.   
    Thread.CurrentPrincipal = MyPrincipal;  
  
    // Print values to the console.  
    String Name =  MyPrincipal.Identity.Name;  
    bool Auth =  MyPrincipal.Identity.IsAuthenticated;   
    bool IsInRole =  MyPrincipal.IsInRole("Manager");  
  
    Console.WriteLine("The Name is: {0}", Name);  
    Console.WriteLine("The IsAuthenticated is: {0}", Auth);  
    Console.WriteLine("Is this a Manager? {0}", IsInRole);  
  
    return 0;  
    }  
}  
```  
  
 <span data-ttu-id="bb8aa-117">Po wykonaniu aplikacja wyświetla dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-117">When executed, the application displays output similar to the following.</span></span>  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb8aa-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb8aa-118">See Also</span></span>  
 <xref:System.Security.Principal.GenericIdentity>  
 <xref:System.Security.Principal.GenericPrincipal>  
 <xref:System.Security.Permissions.PrincipalPermission>  
 [<span data-ttu-id="bb8aa-119">Zastępowanie obiektu podmiotu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="bb8aa-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)  
 [<span data-ttu-id="bb8aa-120">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="bb8aa-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
