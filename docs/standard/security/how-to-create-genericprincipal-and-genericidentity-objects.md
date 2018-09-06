---
title: 'Porady: tworzenie obiektów GenericPrincipal i GenericIdentity'
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
ms.openlocfilehash: 79b5e05fe9133eb2282eedefa001e64ece5e0f57
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44035590"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>Porady: tworzenie obiektów GenericPrincipal i GenericIdentity
Możesz użyć <xref:System.Security.Principal.GenericIdentity> klasy w połączeniu z <xref:System.Security.Principal.GenericPrincipal> klasy, aby utworzyć schemat autoryzacji, która istnieje jako niezależne od domeny Windows.  
  
### <a name="to-create-a-genericprincipal-object"></a>Aby utworzyć obiekt obiektów GenericPrincipal  
  
1.  Utwórz nowe wystąpienie klasy tożsamości i Zainicjuj go przy użyciu nazwy, chcesz, aby pomieścić. Poniższy kod tworzy nową **genericidentity —** obiektu i inicjuje ją o nazwie `MyUser`.  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  Utwórz nowe wystąpienie klasy **obiektów GenericPrincipal** klasy i zainicjuj ją przy użyciu utworzonej wcześniej **genericidentity —** obiekt i Tablica ciągów, które reprezentują role, które mają skojarzone z tej jednostki. Poniższy przykład kodu Określa tablicę ciągów, które reprezentują rolę administratora użytkownikowi i rolę użytkownika. **Obiektów GenericPrincipal** następnie jest inicjowany z poprzedniego **genericidentity —** i tablicy ciągów.  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  Użyj poniższego kodu, aby dołączyć podmiot zabezpieczeń do bieżącego wątku. Jest to przydatne w sytuacjach, w których podmiot zabezpieczeń muszą być weryfikowane kilka razy, muszą być weryfikowane przez inny kod uruchomiony w swojej aplikacji lub muszą być weryfikowane przez <xref:System.Security.Permissions.PrincipalPermission> obiektu. Walidacja oparta na rolach można wciąż wykonywać na obiekt podmiotu zabezpieczeń bez dołączania ich do wątku. Aby uzyskać więcej informacji, zobacz [zastępowanie obiektu głównego](../../../docs/standard/security/replacing-a-principal-object.md).  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć wystąpienie **obiektów GenericPrincipal** i **genericidentity —**. Ten kod wyświetla wartości z tych obiektów do konsoli.  
  
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
  
 Po wykonaniu aplikacja wyświetla dane wyjściowe podobne do następujących.  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Principal.GenericIdentity>  
- <xref:System.Security.Principal.GenericPrincipal>  
- <xref:System.Security.Permissions.PrincipalPermission>  
- [Zastępowanie obiektu podmiotu zabezpieczeń](../../../docs/standard/security/replacing-a-principal-object.md)  
- [Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)
