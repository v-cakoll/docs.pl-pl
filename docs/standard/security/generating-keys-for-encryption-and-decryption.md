---
title: Generowanie kluczy szyfrowania i odszyfrowywania
description: Informacje na temat tworzenia kluczy symetrycznych i asymetrycznych na potrzeby szyfrowania i odszyfrowywania w programie .NET oraz zarządzania nimi.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: f8c3633d18e200037235502487d0d91d42083241
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661812"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="26123-103">Generowanie kluczy szyfrowania i odszyfrowywania</span><span class="sxs-lookup"><span data-stu-id="26123-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="26123-104">Tworzenie kluczy i zarządzanie nimi jest ważną częścią procesu kryptograficznego.</span><span class="sxs-lookup"><span data-stu-id="26123-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="26123-105">Algorytmy symetryczne wymagają utworzenia klucza i wektora inicjalizacji (IV).</span><span class="sxs-lookup"><span data-stu-id="26123-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="26123-106">Klucz musi być poufny dla każdego, kto nie powinien odszyfrować danych.</span><span class="sxs-lookup"><span data-stu-id="26123-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="26123-107">IV nie musi być tajny, ale powinien zostać zmieniony dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="26123-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="26123-108">Algorytmy asymetryczne wymagają utworzenia klucza publicznego i klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="26123-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="26123-109">Klucz publiczny może być publiczny dla każdej osoby, natomiast klucz prywatny musi być znany tylko przez osobę, która będzie odszyfrować dane zaszyfrowane za pomocą klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="26123-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="26123-110">W tej sekcji opisano, jak generować klucze dla algorytmów symetrycznych i asymetrycznych oraz zarządzać nimi.</span><span class="sxs-lookup"><span data-stu-id="26123-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="26123-111">Klucze symetryczne</span><span class="sxs-lookup"><span data-stu-id="26123-111">Symmetric Keys</span></span>  
 <span data-ttu-id="26123-112">Klasy szyfrowania symetrycznego dostarczane przez .NET Framework wymagają klucza i nowego wektora inicjalizacji (IV) do szyfrowania i odszyfrowywania danych.</span><span class="sxs-lookup"><span data-stu-id="26123-112">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="26123-113">Za każdym razem, gdy tworzysz nowe wystąpienie jednej z zarządzanych symetrycznych klas kryptograficznych przy użyciu konstruktora bez parametrów, nowy klucz i IV są tworzone automatycznie.</span><span class="sxs-lookup"><span data-stu-id="26123-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="26123-114">Każda osoba, która zezwoli na odszyfrowanie danych, musi mieć ten sam klucz i IV i korzystać z tego samego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="26123-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="26123-115">Ogólnie rzecz biorąc, należy utworzyć nowy klucz i IV dla każdej sesji, a klucz i IV nie powinny być przechowywane do użytku w późniejszej sesji.</span><span class="sxs-lookup"><span data-stu-id="26123-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="26123-116">Aby przekazać klucz symetryczny i IV do strony zdalnej, zazwyczaj należy zaszyfrować klucz symetryczny przy użyciu szyfrowania asymetrycznego.</span><span class="sxs-lookup"><span data-stu-id="26123-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="26123-117">Wysyłanie klucza w niezabezpieczonej sieci bez szyfrowania jest niebezpieczne, ponieważ każdy z nich przechwytuje klucz i IV może odszyfrować dane.</span><span class="sxs-lookup"><span data-stu-id="26123-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="26123-118">Aby uzyskać więcej informacji na temat wymiany danych przy użyciu szyfrowania, zobacz [Tworzenie schematu kryptograficznego](creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="26123-118">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="26123-119">Poniższy przykład pokazuje, jak utworzyć nowe wystąpienie <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> klasy implementującej algorytm TripleDES.</span><span class="sxs-lookup"><span data-stu-id="26123-119">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="26123-120">Gdy poprzedni kod jest wykonywany, nowy klucz i IV są generowane i umieszczane odpowiednio w właściwościach **Key** i **IV** .</span><span class="sxs-lookup"><span data-stu-id="26123-120">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="26123-121">Czasami może być konieczne wygenerowanie wielu kluczy.</span><span class="sxs-lookup"><span data-stu-id="26123-121">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="26123-122">W takiej sytuacji można utworzyć nowe wystąpienie klasy implementującej algorytm symetryczny, a następnie utworzyć nowy klucz i IV, wywołując metody **do generowania kluczy** i **GenerateIV** .</span><span class="sxs-lookup"><span data-stu-id="26123-122">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="26123-123">Poniższy przykład kodu ilustruje sposób tworzenia nowych kluczy i użycie japońskich ideograficznych po wykonaniu nowego wystąpienia symetrycznej klasy kryptograficznej.</span><span class="sxs-lookup"><span data-stu-id="26123-123">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 <span data-ttu-id="26123-124">Gdy poprzedni kod jest wykonywany, klucz i IV są generowane, gdy tworzone jest nowe wystąpienie **TripleDESCryptoServiceProvider** .</span><span class="sxs-lookup"><span data-stu-id="26123-124">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="26123-125">Po wywołaniu metod **do generowania kluczy** i **GenerateIV** są tworzone inne klucze i IV.</span><span class="sxs-lookup"><span data-stu-id="26123-125">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="26123-126">Klucze asymetryczne</span><span class="sxs-lookup"><span data-stu-id="26123-126">Asymmetric Keys</span></span>  
 <span data-ttu-id="26123-127">.NET Framework zawiera <xref:System.Security.Cryptography.RSACryptoServiceProvider> <xref:System.Security.Cryptography.DSACryptoServiceProvider> klasy i dla szyfrowania asymetrycznego.</span><span class="sxs-lookup"><span data-stu-id="26123-127">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="26123-128">Te klasy tworzą parę kluczy publiczny/prywatny, gdy do utworzenia nowego wystąpienia jest używany Konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="26123-128">These classes create a public/private key pair when you use the parameterless constructor to create a new instance.</span></span> <span data-ttu-id="26123-129">Klucze asymetryczne mogą być przechowywane do użytku w wielu sesjach lub generowane tylko dla jednej sesji.</span><span class="sxs-lookup"><span data-stu-id="26123-129">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="26123-130">Chociaż klucz publiczny można ogólnie udostępnić, klucz prywatny powinien być ściśle chroniony.</span><span class="sxs-lookup"><span data-stu-id="26123-130">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="26123-131">Para kluczy publiczny/prywatny jest generowana za każdym razem, gdy tworzone jest nowe wystąpienie klasy algorytmu asymetrycznego.</span><span class="sxs-lookup"><span data-stu-id="26123-131">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="26123-132">Po utworzeniu nowego wystąpienia klasy informacje o kluczach można wyodrębnić przy użyciu jednej z dwóch metod:</span><span class="sxs-lookup"><span data-stu-id="26123-132">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
- <span data-ttu-id="26123-133"><xref:System.Security.Cryptography.RSA.ToXmlString%2A>Metoda, która zwraca reprezentację XML informacji o kluczu.</span><span class="sxs-lookup"><span data-stu-id="26123-133">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
- <span data-ttu-id="26123-134"><xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A>Metoda, która zwraca <xref:System.Security.Cryptography.RSAParameters> strukturę, która zawiera informacje o kluczu.</span><span class="sxs-lookup"><span data-stu-id="26123-134">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="26123-135">Obie metody akceptują wartość logiczną, która wskazuje, czy zwrócić tylko informacje o kluczu publicznym, czy zwrócić zarówno klucz publiczny, jak i informacje o kluczu prywatnym.</span><span class="sxs-lookup"><span data-stu-id="26123-135">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="26123-136">Klasa **RSACryptoServiceProvider** może zostać zainicjowana do wartości struktury **RSAParameters** przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="26123-136">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="26123-137">Asymetryczne klucze prywatne nigdy nie powinny być przechowywane Verbatim ani w postaci zwykłego tekstu na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="26123-137">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="26123-138">Jeśli musisz przechować klucz prywatny, należy użyć kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="26123-138">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="26123-139">Aby uzyskać więcej informacji o tym, jak przechowywać klucz prywatny w kontenerze kluczy, zobacz [jak: przechowywanie kluczy asymetrycznych w kontenerze kluczy](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="26123-139">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="26123-140">Poniższy przykład kodu tworzy nowe wystąpienie klasy **RSACryptoServiceProvider** , tworząc parę kluczy publiczny/prywatny i zapisuje informacje o kluczu publicznym do struktury **RSAParameters** .</span><span class="sxs-lookup"><span data-stu-id="26123-140">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="26123-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26123-141">See also</span></span>

- [<span data-ttu-id="26123-142">Szyfrowanie danych</span><span class="sxs-lookup"><span data-stu-id="26123-142">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="26123-143">Odszyfrowywanie danych</span><span class="sxs-lookup"><span data-stu-id="26123-143">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="26123-144">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="26123-144">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="26123-145">Instrukcje: przechowywanie kluczy asymetrycznych w kontenerze kluczy</span><span class="sxs-lookup"><span data-stu-id="26123-145">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
