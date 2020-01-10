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
ms.openlocfilehash: 8ca4c4c5b1257411ecdf86858040bf428a9e6ce0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706061"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Porady: przechowywanie kluczy asymetrycznych w kontenerze kluczy
Asymetryczne klucze prywatne nigdy nie powinny być przechowywane Verbatim ani w postaci zwykłego tekstu na komputerze lokalnym. Jeśli musisz przechować klucz prywatny, należy użyć kontenera kluczy. Aby uzyskać więcej informacji na temat kontenerów kluczy, zobacz temat [Omówienie kontenerów kluczy RSA na poziomie komputera i użytkownika](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Aby utworzyć klucz asymetryczny i zapisać go w kontenerze kluczy  
  
1. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters> i przekaż nazwę, która ma być wywoływana przez kontener kluczy do pola <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType>.  
  
2. Utwórz nowe wystąpienie klasy, która dziedziczy z klasy <xref:System.Security.Cryptography.AsymmetricAlgorithm> (zazwyczaj **RSACryptoServiceProvider** lub **DSACryptoServiceProvider**) i przekaż poprzednio utworzony obiekt **CspParameters** do jego konstruktora.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>Aby usunąć klucz z kontenera kluczy  
  
1. Utwórz nowe wystąpienie klasy **CspParameters** i przekaż nazwę, która ma być wywoływana z kontenera kluczy do pola **CspParameters. ContainerName** .  
  
2. Utwórz nowe wystąpienie klasy, która dziedziczy z klasy **AsymmetricAlgorithm** (zazwyczaj **RSACryptoServiceProvider** lub **DSACryptoServiceProvider**) i przekaż wcześniej utworzony obiekt **CspParameters** do jego konstruktora.  
  
3. Ustaw właściwość **PersistKeyInCSP** klasy, która dziedziczy z **AsymmetricAlgorithm** na **false** (**false** w Visual Basic).  
  
4. Wywołaj metodę **Clear** klasy, która pochodzi od **AsymmetricAlgorithm**. Ta metoda zwalnia wszystkie zasoby klasy i czyści kontener kluczy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób tworzenia klucza asymetrycznego, zapisywania go w kontenerze kluczy, pobierania klucza w późniejszym czasie i usuwania klucza z kontenera.  
  
 Zwróć uwagę, że kod w metodzie `GenKey_SaveInContainer` i Metoda `GetKeyFromContainer` są podobne.  Jeśli określisz nazwę kontenera kluczy dla obiektu <xref:System.Security.Cryptography.CspParameters> i przekażesz go do obiektu <xref:System.Security.Cryptography.AsymmetricAlgorithm> z właściwością <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> lub właściwością <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> ustawioną na true, wystąpią poniższe.  Jeśli kontener kluczy o podanej nazwie nie istnieje, zostanie utworzony jeden i klucz zostanie utrwalony.  Jeśli istnieje kontener kluczy o podanej nazwie, klucz w kontenerze zostanie automatycznie załadowany do bieżącego obiektu <xref:System.Security.Cryptography.AsymmetricAlgorithm>.  W związku z tym kod w metodzie `GenKey_SaveInContainer` utrzymuje klucz, ponieważ jest uruchamiany jako pierwszy, podczas gdy kod w metodzie `GetKeyFromContainer` ładuje klucz, ponieważ jest uruchamiany drugi.  
  
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
  
```console  
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
