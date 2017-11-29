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
ms.openlocfilehash: 93cd88d0321133a8340864645954b450a8e530ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>Porady: tworzenie obiektów GenericPrincipal i GenericIdentity
Można użyć <xref:System.Security.Principal.GenericIdentity> klasy w połączeniu z <xref:System.Security.Principal.GenericPrincipal> klasę, aby utworzyć schemat autoryzacji, czy istnieje niezależnie od domeny systemu Windows.  
  
### <a name="to-create-a-genericprincipal-object"></a>Do tworzenia obiektu GenericPrincipal  
  
1.  Utwórz nowe wystąpienie klasy tożsamości i zainicjować go o nazwie ma być przechowywane. Poniższy kod tworzy nową **genericidentity —** obiektu i inicjuje go o nazwie `MyUser`.  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  Utwórz nowe wystąpienie klasy **GenericPrincipal** klasy i zainicjować go z utworzonej wcześniej **genericidentity —** obiekt i Tablica ciągów, które reprezentują role, które mają skojarzone z tego podmiotu zabezpieczeń. Poniższy przykład kodu Określa tablicę ciągów reprezentujących rolą administratora oraz roli użytkownika. **GenericPrincipal** następnie jest inicjowany z poprzedniej **genericidentity —** i tablicy ciągów.  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  Użyć poniższego kodu do dołączenia do podmiotu zabezpieczeń do bieżącego wątku. Jest to przydatne w sytuacjach, w których podmiot zabezpieczeń musi zostać zweryfikowany kilka razy, musi zostać zweryfikowany przez inny kod w aplikacji lub musi zostać zweryfikowany przez <xref:System.Security.Permissions.PrincipalPermission> obiektu. Może nadal wykonywać walidacji opartej na rolach na obiekt główny bez dołączeniu go do wątku. Aby uzyskać więcej informacji, zobacz [zastępowanie obiektu głównego](../../../docs/standard/security/replacing-a-principal-object.md).  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób tworzenia wystąpienia **GenericPrincipal** i **genericidentity —**. Ten kod wyświetla wartości z tych obiektów do konsoli.  
  
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
  
 Po wykonaniu aplikacja wyświetla dane wyjściowe podobne do następującego.  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Principal.GenericIdentity>  
 <xref:System.Security.Principal.GenericPrincipal>  
 <xref:System.Security.Permissions.PrincipalPermission>  
 [Zastępowanie obiektu głównego](../../../docs/standard/security/replacing-a-principal-object.md)  
 [Główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)
