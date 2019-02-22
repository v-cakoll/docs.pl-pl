---
title: 'Instrukcje: Tworzenie obiektów GenericPrincipal i genericidentity — obiekty'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8dd255aafe16cf0cb893ff4157b3590b3fc8d03
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583683"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="a685b-102">Instrukcje: Tworzenie obiektów GenericPrincipal i genericidentity — obiekty</span><span class="sxs-lookup"><span data-stu-id="a685b-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>
<span data-ttu-id="a685b-103">Możesz użyć <xref:System.Security.Principal.GenericIdentity> klasy w połączeniu z <xref:System.Security.Principal.GenericPrincipal> klasy, aby utworzyć schemat autoryzacji, która istnieje jako niezależne od domeny Windows.</span><span class="sxs-lookup"><span data-stu-id="a685b-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>  
  
### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="a685b-104">Aby utworzyć obiekt obiektów GenericPrincipal</span><span class="sxs-lookup"><span data-stu-id="a685b-104">To create a GenericPrincipal object</span></span>  
  
1.  <span data-ttu-id="a685b-105">Utwórz nowe wystąpienie klasy tożsamości i Zainicjuj go przy użyciu nazwy, chcesz, aby pomieścić.</span><span class="sxs-lookup"><span data-stu-id="a685b-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="a685b-106">Poniższy kod tworzy nową **genericidentity —** obiektu i inicjuje ją o nazwie `MyUser`.</span><span class="sxs-lookup"><span data-stu-id="a685b-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>  
  
    ```vb  
    Dim myIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity myIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  <span data-ttu-id="a685b-107">Utwórz nowe wystąpienie klasy **obiektów GenericPrincipal** klasy i zainicjuj ją przy użyciu utworzonej wcześniej **genericidentity —** obiekt i Tablica ciągów, które reprezentują role, które mają skojarzone z tej jednostki.</span><span class="sxs-lookup"><span data-stu-id="a685b-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="a685b-108">Poniższy przykład kodu Określa tablicę ciągów, które reprezentują rolę administratora użytkownikowi i rolę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a685b-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="a685b-109">**Obiektów GenericPrincipal** następnie jest inicjowany z poprzedniego **genericidentity —** i tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="a685b-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>  
  
    ```vb  
    Dim myStringArray As String() = {"Manager", "Teller"}  
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)  
    ```  
  
    ```csharp  
    String[] myStringArray = {"Manager", "Teller"};  
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);  
    ```  
  
3.  <span data-ttu-id="a685b-110">Użyj poniższego kodu, aby dołączyć podmiot zabezpieczeń do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="a685b-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="a685b-111">Jest to przydatne w sytuacjach, w których podmiot zabezpieczeń muszą być weryfikowane kilka razy, muszą być weryfikowane przez inny kod uruchomiony w swojej aplikacji lub muszą być weryfikowane przez <xref:System.Security.Permissions.PrincipalPermission> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a685b-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="a685b-112">Walidacja oparta na rolach można wciąż wykonywać na obiekt podmiotu zabezpieczeń bez dołączania ich do wątku.</span><span class="sxs-lookup"><span data-stu-id="a685b-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="a685b-113">Aby uzyskać więcej informacji, zobacz [zastępowanie obiektu głównego](../../../docs/standard/security/replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="a685b-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>  
  
    ```vb  
    Thread.CurrentPrincipal = myPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = myPrincipal;  
    ```  
  
## <a name="example"></a><span data-ttu-id="a685b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="a685b-114">Example</span></span>  
 <span data-ttu-id="a685b-115">Poniższy przykład kodu pokazuje, jak utworzyć wystąpienie **obiektów GenericPrincipal** i **genericidentity —**.</span><span class="sxs-lookup"><span data-stu-id="a685b-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="a685b-116">Ten kod wyświetla wartości z tych obiektów do konsoli.</span><span class="sxs-lookup"><span data-stu-id="a685b-116">This code displays the values of these objects to the console.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Principal  
Imports System.Threading  
  
Public Class Class1  
  
    Public Shared Sub Main()  
        ' Create generic identity.  
        Dim myIdentity As New GenericIdentity("MyIdentity")  
  
        ' Create generic principal.  
        Dim myStringArray As String() =  {"Manager", "Teller"}  
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)  
  
        ' Attach the principal to the current thread.  
        ' This is not required unless repeated validation must occur,  
        ' other code in your application must validate, or the   
        ' PrincipalPermisson object is used.   
        Thread.CurrentPrincipal = myPrincipal  
  
        ' Print values to the console.  
        Dim name As String = myPrincipal.Identity.Name  
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated  
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")  
  
        Console.WriteLine("The name is: {0}", name)  
        Console.WriteLine("The isAuthenticated is: {0}", auth)  
        Console.WriteLine("Is this a Manager? {0}", isInRole)  
  
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
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");  
  
    // Create generic principal.  
    String[] myStringArray = {"Manager", "Teller"};  
    GenericPrincipal myPrincipal =   
        new GenericPrincipal(myIdentity, myStringArray);  
  
    // Attach the principal to the current thread.  
    // This is not required unless repeated validation must occur,  
    // other code in your application must validate, or the   
    // PrincipalPermisson object is used.   
    Thread.CurrentPrincipal = myPrincipal;  
  
    // Print values to the console.  
    String name =  myPrincipal.Identity.Name;  
    bool auth =  myPrincipal.Identity.IsAuthenticated;   
    bool isInRole =  myPrincipal.IsInRole("Manager");  
  
    Console.WriteLine("The name is: {0}", name);  
    Console.WriteLine("The isAuthenticated is: {0}", auth);  
    Console.WriteLine("Is this a Manager? {0}", isInRole);  
  
    return 0;  
    }  
}  
```  
  
 <span data-ttu-id="a685b-117">Po wykonaniu aplikacja wyświetla dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="a685b-117">When executed, the application displays output similar to the following.</span></span>  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a><span data-ttu-id="a685b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a685b-118">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="a685b-119">Zastępowanie obiektu podmiotu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a685b-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)
- [<span data-ttu-id="a685b-120">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="a685b-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
