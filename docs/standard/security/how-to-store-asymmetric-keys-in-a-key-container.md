---
title: 'Porady: przechowywanie kluczy asymetrycznych w kontenerze kluczy'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3db4afb00367f719391193ebce4053cc5da16164
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588859"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Porady: przechowywanie kluczy asymetrycznych w kontenerze kluczy
Prywatne klucze asymetryczne nigdy nie powinny być przechowywane, dosłownego wyrażenia lub w postaci zwykłego tekstu na komputerze lokalnym. Jeśli musisz przechować klucz prywatny, należy użyć kontenera kluczy. Aby uzyskać więcej informacji na kontenerów kluczy, zobacz [kontenery kluczy RSA na poziomie użytkownika i na poziomie maszyny opis](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Aby utworzyć klucz asymetryczny i zapisać ją w kontenerze kluczy  
  
1.  Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters> klasy i podaj nazwę, która ma zostać wywołana klucz kontenera, aby <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pola.  
  
2.  Utwórz nowe wystąpienie klasy, która jest pochodną <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy (zazwyczaj **RSACryptoServiceProvider** lub **DSACryptoServiceProvider**), a następnie przekaż utworzonej wcześniej  **CspParameters** obiektu dla jego konstruktora.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>Aby usunąć klucz z kontenera kluczy  
  
1.  Utwórz nowe wystąpienie klasy **CspParameters** klasy i podaj nazwę, która ma zostać wywołana klucz kontenera, aby **CspParameters.KeyContainerName** pola.  
  
2.  Utwórz nowe wystąpienie klasy, która jest pochodną **AsymmetricAlgorithm** klasy (zazwyczaj **RSACryptoServiceProvider** lub **DSACryptoServiceProvider**) i przekaż wcześniej utworzony **CspParameters** obiektu dla jego konstruktora.  
  
3.  Ustaw **PersistKeyInCSP** właściwości klasy, która jest pochodną **AsymmetricAlgorithm** do **false** (**False** w języku Visual Basic).  
  
4.  Wywołanie **wyczyść** metody klasy, która jest pochodną **AsymmetricAlgorithm**. Ta metoda zwalnia wszystkie zasoby klasy i usuwa kontener kluczy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak utworzyć klucza asymetrycznego, zapisz go w kontenerze kluczy pobrać klucza w późniejszym czasie i usunąć klucz z kontenera.  
  
 Zwróć uwagę, że kod w `GenKey_SaveInContainer` — metoda i `GetKeyFromContainer` metoda jest podobna.  Po określeniu nazwę kontenera kluczy <xref:System.Security.Cryptography.CspParameters> obiektu i przekaż go do <xref:System.Security.Cryptography.AsymmetricAlgorithm> obiekt z <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> właściwości lub <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> właściwość jest ustawiona na wartość true, występuje poniższy.  Jeśli kontener kluczy o podanej nazwie nie istnieje, jest ono tworzone i klucz jest trwały.  Kontener kluczy o podanej nazwie istnieje, a następnie klawisz w kontenerze automatycznie jest ładowany do bieżącego <xref:System.Security.Cryptography.AsymmetricAlgorithm> obiektu.  W związku z tym kod w `GenKey_SaveInContainer` metoda będzie się powtarzał klucza, ponieważ jest uruchamiany pierwszy podczas kod w `GetKeyFromContainer` metody ładuje klucza, ponieważ jest uruchamiany drugi.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```Output  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [Szyfrowanie danych](../../../docs/standard/security/encrypting-data.md)  
 [Odszyfrowywanie danych](../../../docs/standard/security/decrypting-data.md)  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
