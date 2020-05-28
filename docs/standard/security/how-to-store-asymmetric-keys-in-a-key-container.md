---
title: 'Instrukcje: przechowywanie kluczy asymetrycznych w kontenerze kluczy'
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
ms.openlocfilehash: 36bae05fbfb35dc112e0c543c9a1a975a8fa8db5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143624"
---
# <a name="store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="74a32-102">Przechowywanie kluczy asymetrycznych w kontenerze kluczy</span><span class="sxs-lookup"><span data-stu-id="74a32-102">Store asymmetric keys in a key container</span></span>

<span data-ttu-id="74a32-103">Asymetryczne klucze prywatne nigdy nie powinny być przechowywane Verbatim ani w postaci zwykłego tekstu na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="74a32-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="74a32-104">Jeśli musisz zapisać klucz prywatny, Użyj kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="74a32-104">If you need to store a private key, use a key container.</span></span> <span data-ttu-id="74a32-105">Aby uzyskać więcej informacji na temat kontenerów kluczy, zobacz temat [Omówienie kontenerów kluczy RSA na poziomie komputera i użytkownika](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="74a32-105">For more information on key containers, see [Understanding machine-level and user-level RSA key containers](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="74a32-106">Tworzenie klucza asymetrycznego i zapisywanie go w kontenerze kluczy</span><span class="sxs-lookup"><span data-stu-id="74a32-106">Create an asymmetric key and save it in a key container</span></span>

1. <span data-ttu-id="74a32-107">Utwórz nowe wystąpienie <xref:System.Security.Cryptography.CspParameters> klasy i przekaż nazwę, która ma być wywoływana przez kontener kluczy do <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pola.</span><span class="sxs-lookup"><span data-stu-id="74a32-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="74a32-108">Utwórz nowe wystąpienie klasy, która dziedziczy z <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy (zwykle <xref:System.Security.Cryptography.RSACryptoServiceProvider> lub <xref:System.Security.Cryptography.DSACryptoServiceProvider> ) i przekaż wcześniej utworzony `CspParameters` obiekt do jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="74a32-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually <xref:System.Security.Cryptography.RSACryptoServiceProvider> or <xref:System.Security.Cryptography.DSACryptoServiceProvider>) and pass the previously created `CspParameters` object to its constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="74a32-109">Tworzenie i pobieranie klucza asymetrycznego jest jedną operacją.</span><span class="sxs-lookup"><span data-stu-id="74a32-109">The creation and retrieval of an asymmetric key is one operation.</span></span> <span data-ttu-id="74a32-110">Jeśli klucz nie znajduje się już w kontenerze, jest tworzony przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="74a32-110">If a key is not already in the container, it's created before being returned.</span></span>
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a><span data-ttu-id="74a32-111">Usuń klucz z kontenera kluczy</span><span class="sxs-lookup"><span data-stu-id="74a32-111">Delete the key from the key container</span></span>

1. <span data-ttu-id="74a32-112">Utwórz nowe wystąpienie `CspParameters` klasy i przekaż nazwę, która ma być wywoływana przez kontener kluczy do <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pola.</span><span class="sxs-lookup"><span data-stu-id="74a32-112">Create a new instance of a `CspParameters` class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="74a32-113">Utwórz nowe wystąpienie klasy, która dziedziczy z <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy (zwykle `RSACryptoServiceProvider` lub `DSACryptoServiceProvider` ) i przekaż wcześniej utworzony `CspParameters` obiekt do jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="74a32-113">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually `RSACryptoServiceProvider` or `DSACryptoServiceProvider`) and pass the previously created `CspParameters` object to its constructor.</span></span>

1. <span data-ttu-id="74a32-114">Ustaw <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> lub <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> Właściwość klasy, która pochodzi od `AsymmetricAlgorithm` do `false` ( `False` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="74a32-114">Set the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> or the <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> property of the class that derives from `AsymmetricAlgorithm` to `false` (`False` in Visual Basic).</span></span>

1. <span data-ttu-id="74a32-115">Wywoływanie `Clear` metody klasy, która dziedziczy z `AsymmetricAlgorithm` .</span><span class="sxs-lookup"><span data-stu-id="74a32-115">Call the `Clear` method of the class that derives from `AsymmetricAlgorithm`.</span></span> <span data-ttu-id="74a32-116">Ta metoda zwalnia wszystkie zasoby klasy i czyści kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="74a32-116">This method releases all resources of the class and clears the key container.</span></span>

## <a name="example"></a><span data-ttu-id="74a32-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="74a32-117">Example</span></span>

<span data-ttu-id="74a32-118">Poniższy przykład ilustruje sposób tworzenia klucza asymetrycznego, zapisywania go w kontenerze kluczy, pobierania klucza w późniejszym czasie i usuwania klucza z kontenera.</span><span class="sxs-lookup"><span data-stu-id="74a32-118">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>

<span data-ttu-id="74a32-119">Zwróć uwagę, że kod w `GenKey_SaveInContainer` metodzie i `GetKeyFromContainer` metodzie jest podobny.</span><span class="sxs-lookup"><span data-stu-id="74a32-119">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span> <span data-ttu-id="74a32-120">Jeśli określisz nazwę kontenera kluczy dla <xref:System.Security.Cryptography.CspParameters> obiektu i przekażesz go do <xref:System.Security.Cryptography.AsymmetricAlgorithm> obiektu z <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> właściwością lub <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> właściwością ustawioną na `true` , zachowanie jest następujące:</span><span class="sxs-lookup"><span data-stu-id="74a32-120">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to `true`, the behavior is as follows:</span></span>

- <span data-ttu-id="74a32-121">Jeśli kontener kluczy o podanej nazwie nie istnieje, zostanie utworzony jeden i klucz zostanie utrwalony.</span><span class="sxs-lookup"><span data-stu-id="74a32-121">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>
- <span data-ttu-id="74a32-122">Jeśli istnieje kontener kluczy o podanej nazwie, klucz w kontenerze zostanie automatycznie załadowany do bieżącego <xref:System.Security.Cryptography.AsymmetricAlgorithm> obiektu.</span><span class="sxs-lookup"><span data-stu-id="74a32-122">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>

<span data-ttu-id="74a32-123">W związku z tym kod w `GenKey_SaveInContainer` metodzie utrzymuje klucz, ponieważ jest uruchamiany jako pierwszy, podczas gdy kod w `GetKeyFromContainer` metodzie ładuje klucz, ponieważ jest uruchamiany drugi.</span><span class="sxs-lookup"><span data-stu-id="74a32-123">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it's run second.</span></span>

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

<span data-ttu-id="74a32-124">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="74a32-124">The output is as follows:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="74a32-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74a32-125">See also</span></span>

- [<span data-ttu-id="74a32-126">Generowanie kluczy szyfrowania i odszyfrowywania</span><span class="sxs-lookup"><span data-stu-id="74a32-126">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="74a32-127">Szyfrowanie danych</span><span class="sxs-lookup"><span data-stu-id="74a32-127">Encrypting data</span></span>](encrypting-data.md)
- [<span data-ttu-id="74a32-128">Odszyfrowywanie danych</span><span class="sxs-lookup"><span data-stu-id="74a32-128">Decrypting data</span></span>](decrypting-data.md)
- [<span data-ttu-id="74a32-129">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="74a32-129">Cryptographic services</span></span>](cryptographic-services.md)
