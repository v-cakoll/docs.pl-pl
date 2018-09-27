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
ms.openlocfilehash: a5cd157f89797406fbe87c3d70c415d7b192d1a9
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399914"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Porady: przechowywanie kluczy asymetrycznych w kontenerze kluczy
Klucze asymetryczne prywatnej nigdy nie powinny być przechowywane, verbatim lub w postaci zwykłego tekstu, na komputerze lokalnym. Jeśli musisz przechować klucz prywatny, należy użyć kontenera kluczy. Aby uzyskać więcej informacji na temat kontenerów kluczy, zobacz [kontenery kluczy RSA poziomie użytkownika i na poziomie maszyny opis](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Aby utworzyć to klucz asymetryczny i zapisać ją w kontenerze kluczy  
  
1.  Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters> klasy i przekazywać nazwę jednostki, którą chcesz wywołać kontener klucza do <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pola.  
  
2.  Utwórz nowe wystąpienie klasy, która jest pochodną <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy (zazwyczaj **RSACryptoServiceProvider** lub **DSACryptoServiceProvider**) i przekaż utworzony wcześniej  **CspParameters** obiektu dla jego konstruktora.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>Aby usunąć klucz przy użyciu kontenera kluczy  
  
1.  Utwórz nowe wystąpienie klasy **CspParameters** klasy i przekazywać nazwę jednostki, którą chcesz wywołać kontener klucza do **CspParameters.KeyContainerName** pola.  
  
2.  Utwórz nowe wystąpienie klasy, która jest pochodną **AsymmetricAlgorithm** klasy (zazwyczaj **RSACryptoServiceProvider** lub **DSACryptoServiceProvider**) i przekaż utworzone wcześniej **CspParameters** obiektu dla jego konstruktora.  
  
3.  Ustaw **PersistKeyInCSP** właściwość klasy, która pochodzi od klasy **AsymmetricAlgorithm** do **false** (**False** w języku Visual Basic).  
  
4.  Wywołaj **wyczyść** metody klasy, która pochodzi od klasy **AsymmetricAlgorithm**. Ta metoda zwalnia wszystkie zasoby klasy i czyści kontenera kluczy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć klucza asymetrycznego, zapisz go w kontenerze kluczy, pobieranie klucza w późniejszym czasie i Usuń klucz z kontenera.  
  
 Należy zauważyć, że kod w `GenKey_SaveInContainer` metody i `GetKeyFromContainer` metoda jest podobna.  Po określeniu nazwę kontenera kluczy <xref:System.Security.Cryptography.CspParameters> obiektu i przekazać ją do <xref:System.Security.Cryptography.AsymmetricAlgorithm> obiekt z <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> właściwości lub <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> ustawioną na wartość true, zostaną wykonane następujące zadania.  Jeśli kontener kluczy o podanej nazwie nie istnieje, następnie jest tworzona i klucz jest trwały.  Jeśli kontener kluczy o podanej nazwie istnieje, a następnie klawisz w kontenerze jest automatycznie ładowany do bieżącej <xref:System.Security.Cryptography.AsymmetricAlgorithm> obiektu.  W związku z tym, kod w `GenKey_SaveInContainer` metoda będzie się powtarzać klucza, ponieważ jest uruchamiany podczas kod najpierw `GetKeyFromContainer` metoda ładuje klucza, ponieważ jest uruchamiany w drugiej.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
- [Szyfrowanie danych](../../../docs/standard/security/encrypting-data.md)  
- [Odszyfrowywanie danych](../../../docs/standard/security/decrypting-data.md)  
- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
