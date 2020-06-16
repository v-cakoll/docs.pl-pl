---
title: 'Instrukcje: przechowywanie kluczy asymetrycznych w kontenerze kluczy'
description: Dowiedz się, jak przechowywać klucze asymetryczne w kontenerze kluczy w programie .NET. Zobacz jak utworzyć klucz asymetryczny, zapisać go w kontenerze kluczy i pobrać i usunąć klucz.
ms.date: 05/26/2020
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
ms.openlocfilehash: a0fbde37491043cc1aab71e9733087bf410b997d
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769032"
---
# <a name="store-asymmetric-keys-in-a-key-container"></a>Przechowywanie kluczy asymetrycznych w kontenerze kluczy

Asymetryczne klucze prywatne nigdy nie powinny być przechowywane Verbatim ani w postaci zwykłego tekstu na komputerze lokalnym. Jeśli musisz zapisać klucz prywatny, Użyj kontenera kluczy. Aby uzyskać więcej informacji na temat kontenerów kluczy, zobacz temat [Omówienie kontenerów kluczy RSA na poziomie komputera i użytkownika](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Tworzenie klucza asymetrycznego i zapisywanie go w kontenerze kluczy

1. Utwórz nowe wystąpienie <xref:System.Security.Cryptography.CspParameters> klasy i przekaż nazwę, która ma być wywoływana przez kontener kluczy do <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pola.

1. Utwórz nowe wystąpienie klasy, która dziedziczy z <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy (zwykle <xref:System.Security.Cryptography.RSACryptoServiceProvider> lub <xref:System.Security.Cryptography.DSACryptoServiceProvider> ) i przekaż wcześniej utworzony `CspParameters` obiekt do jego konstruktora.

> [!NOTE]
> Tworzenie i pobieranie klucza asymetrycznego jest jedną operacją. Jeśli klucz nie znajduje się już w kontenerze, jest tworzony przed zwróceniem.
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a>Usuń klucz z kontenera kluczy

1. Utwórz nowe wystąpienie `CspParameters` klasy i przekaż nazwę, która ma być wywoływana przez kontener kluczy do <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pola.

1. Utwórz nowe wystąpienie klasy, która dziedziczy z <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy (zwykle `RSACryptoServiceProvider` lub `DSACryptoServiceProvider` ) i przekaż wcześniej utworzony `CspParameters` obiekt do jego konstruktora.

1. Ustaw <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> lub <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> Właściwość klasy, która pochodzi od `AsymmetricAlgorithm` do `false` ( `False` w Visual Basic).

1. Wywoływanie `Clear` metody klasy, która dziedziczy z `AsymmetricAlgorithm` . Ta metoda zwalnia wszystkie zasoby klasy i czyści kontener kluczy.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób tworzenia klucza asymetrycznego, zapisywania go w kontenerze kluczy, pobierania klucza w późniejszym czasie i usuwania klucza z kontenera.

Zwróć uwagę, że kod w `GenKey_SaveInContainer` metodzie i `GetKeyFromContainer` metodzie jest podobny. Jeśli określisz nazwę kontenera kluczy dla <xref:System.Security.Cryptography.CspParameters> obiektu i przekażesz go do <xref:System.Security.Cryptography.AsymmetricAlgorithm> obiektu z <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> właściwością lub <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> właściwością ustawioną na `true` , zachowanie jest następujące:

- Jeśli kontener kluczy o podanej nazwie nie istnieje, zostanie utworzony jeden i klucz zostanie utrwalony.
- Jeśli istnieje kontener kluczy o podanej nazwie, klucz w kontenerze zostanie automatycznie załadowany do bieżącego <xref:System.Security.Cryptography.AsymmetricAlgorithm> obiektu.

W związku z tym kod w `GenKey_SaveInContainer` metodzie utrzymuje klucz, ponieważ jest uruchamiany jako pierwszy, podczas gdy kod w `GetKeyFromContainer` metodzie ładuje klucz, ponieważ jest uruchamiany drugi.

```vb
Imports System
Imports System.Security.Cryptography

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

    Private Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        ' name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key added to container:  {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub GetKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key retrieved from container : {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container.
        ' Delete the key entry in the container.
        Dim rsa As New RSACryptoServiceProvider(parameters) With {
            .PersistKeyInCsp = False
        }

        ' Call Clear to release resources and delete the key from the container.
        rsa.Clear()

        Console.WriteLine("Key deleted.")
    End Sub
End Class
```

```csharp
using System;
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
        catch (CryptographicException e)
        {
            Console.WriteLine(e.Message);
        }
    }

    private static void GenKey_SaveInContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key added to container: \n  {rsa.ToXmlString(true)}");
    }

    private static void GetKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key retrieved from container : \n {rsa.ToXmlString(true)}");
    }

    private static void DeleteKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container.
        using var rsa = new RSACryptoServiceProvider(parameters)
        {
            // Delete the key entry in the container.
            PersistKeyInCsp = false
        };

        // Call Clear to release resources and delete the key from the container.
        rsa.Clear();

        Console.WriteLine("Key deleted.");
    }
}
```

Wynik jest następujący:

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

## <a name="see-also"></a>Zobacz też

- [Generowanie kluczy szyfrowania i odszyfrowywania](generating-keys-for-encryption-and-decryption.md)
- [Szyfrowanie danych](encrypting-data.md)
- [Odszyfrowywanie danych](decrypting-data.md)
- [Usługi kryptograficzne](cryptographic-services.md)
