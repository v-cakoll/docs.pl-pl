---
title: Generowanie kluczy szyfrowania i odszyfrowywania
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
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 333e99997bad3852ae34753165aa736ef32ac004
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="a6554-102">Generowanie kluczy szyfrowania i odszyfrowywania</span><span class="sxs-lookup"><span data-stu-id="a6554-102">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="a6554-103">Tworzenie i zarządzanie kluczami jest ważnym elementem procesu szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="a6554-103">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="a6554-104">Symetryczne algorytmy wymaga utworzenia klucza i wektor inicjowania (IV).</span><span class="sxs-lookup"><span data-stu-id="a6554-104">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="a6554-105">Klucz musi być trzymane w każdy, kto powinien nie odszyfrowania danych.</span><span class="sxs-lookup"><span data-stu-id="a6554-105">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="a6554-106">IV musi być tajny, ale powinny być zmieniane dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="a6554-106">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="a6554-107">Asymetryczne algorytmy wymaga utworzenia klucz publiczny i klucz prywatny.</span><span class="sxs-lookup"><span data-stu-id="a6554-107">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="a6554-108">Klucz publiczny mogą być ujawniane innym osobom, gdy klucz prywatny musi znane tylko przez strony, która będzie odszyfrować dane zaszyfrowane przy użyciu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="a6554-108">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="a6554-109">W tej sekcji opisano, jak do generowania i zarządzania kluczami zarówno symetrycznego i asymetryczne algorytmy.</span><span class="sxs-lookup"><span data-stu-id="a6554-109">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="a6554-110">Klucze symetryczne</span><span class="sxs-lookup"><span data-stu-id="a6554-110">Symmetric Keys</span></span>  
 <span data-ttu-id="a6554-111">Klasy szyfrowania symetrycznego dostarczonych przez program .NET Framework wymaga klucza i nowy wektor inicjowania (IV) do szyfrowania i odszyfrowywania danych.</span><span class="sxs-lookup"><span data-stu-id="a6554-111">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="a6554-112">Podczas tworzenia nowego wystąpienia jednego z zarządzanych za pomocą konstruktora domyślnego symetrycznego klas kryptograficznych klucza i IV są tworzone automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a6554-112">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the default constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="a6554-113">Każda osoba, która pozwala na odszyfrowywanie danych musi posiadać ten sam klucz i IV i korzystać z tego samego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="a6554-113">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="a6554-114">Ogólnie rzecz biorąc dla każdej sesji powinien zostać utworzony nowy klucz i IV, a klucz ani IV powinny być przechowywane do wykorzystania w późniejszym sesji.</span><span class="sxs-lookup"><span data-stu-id="a6554-114">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="a6554-115">Do komunikacji klucza symetrycznego i IV strona zdalna, czy zwykle szyfrowania symetrycznego klucza przy użyciu szyfrowanie asymetryczne.</span><span class="sxs-lookup"><span data-stu-id="a6554-115">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="a6554-116">Przesyłania tego klucza przez niezabezpieczonej sieci bez szyfrowania jest niebezpieczne, ponieważ każdy użytkownik, który przechwytuje klucza i IV odszyfrować danych.</span><span class="sxs-lookup"><span data-stu-id="a6554-116">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="a6554-117">Aby uzyskać więcej informacji na temat wymiany danych przy użyciu szyfrowania, zobacz [tworzenie schematu kryptograficznego](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="a6554-117">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="a6554-118">W poniższym przykładzie pokazano tworzenie nowego wystąpienia <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> klasa implementująca algorytmu TripleDES.</span><span class="sxs-lookup"><span data-stu-id="a6554-118">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="a6554-119">Po wykonaniu poprzednich kodu nowy klucz i IV były generowane i umieszczane w **klucza** i **IV** właściwości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="a6554-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="a6554-120">Czasami może być konieczne do wygenerowania wielu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a6554-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="a6554-121">W takiej sytuacji można tworzyć nowe wystąpienie klasy, która implementuje algorytmu symetrycznego i utworzyć nowy klucz i IV przez wywołanie metody **GenerateKey** i **GenerateIV** metody.</span><span class="sxs-lookup"><span data-stu-id="a6554-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="a6554-122">Poniższy przykładowy kod ilustruje sposób tworzenia nowych kluczy i wektory inicjacji po dokonaniu nowe wystąpienie klasy asymetrycznego kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="a6554-122">The following code example illustrates how to create new keys and IVs after a new instance of the asymmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
TDES.GenerateIV()  
TDES.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
TDES.GenerateIV();  
TDES.GenerateKey();  
```  
  
 <span data-ttu-id="a6554-123">Po wykonaniu poprzedni kod klucza i IV są generowane podczas nowe wystąpienie klasy **TripleDESCryptoServiceProvider** staje się.</span><span class="sxs-lookup"><span data-stu-id="a6554-123">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="a6554-124">Inny klucz i IV są tworzone, gdy **GenerateKey** i **GenerateIV** metody są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="a6554-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="a6554-125">Klucze asymetryczne</span><span class="sxs-lookup"><span data-stu-id="a6554-125">Asymmetric Keys</span></span>  
 <span data-ttu-id="a6554-126">Platforma .NET Framework zapewnia <xref:System.Security.Cryptography.RSACryptoServiceProvider> i <xref:System.Security.Cryptography.DSACryptoServiceProvider> klasy dla szyfrowanie asymetryczne.</span><span class="sxs-lookup"><span data-stu-id="a6554-126">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="a6554-127">Te klasy utworzyć pary kluczy publiczny/prywatny, używając domyślnego konstruktora do utworzenia nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a6554-127">These classes create a public/private key pair when you use the default constructor to create a new instance.</span></span> <span data-ttu-id="a6554-128">Klucze asymetryczne można przechowywane do wykorzystania w wiele sesji lub wygenerowany dla tylko jednej sesji.</span><span class="sxs-lookup"><span data-stu-id="a6554-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="a6554-129">Gdy klucz publiczny mogą być udostępniane ogólnie rzecz biorąc, klucz prywatny powinien ściśle chroniony.</span><span class="sxs-lookup"><span data-stu-id="a6554-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="a6554-130">Pary kluczy publiczny/prywatny jest generowany, gdy tworzone jest nowe wystąpienie klasy algorytmu asymetrycznego.</span><span class="sxs-lookup"><span data-stu-id="a6554-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="a6554-131">Po utworzeniu nowego wystąpienia klasy, informacje o kluczu można wyodrębnić przy użyciu jednej z dwóch metod:</span><span class="sxs-lookup"><span data-stu-id="a6554-131">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
-   <span data-ttu-id="a6554-132"><xref:System.Security.Cryptography.RSA.ToXmlString%2A> Metody, która zwraca informacje o kluczu reprezentację XML.</span><span class="sxs-lookup"><span data-stu-id="a6554-132">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
-   <span data-ttu-id="a6554-133"><xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> Metody, która zwraca <xref:System.Security.Cryptography.RSAParameters> struktury, która przechowuje informacje o kluczu.</span><span class="sxs-lookup"><span data-stu-id="a6554-133">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="a6554-134">Obie metody zaakceptuj wartość logiczną wskazującą, czy zwracać tylko informacje o kluczu publicznym, czy zwracać zarówno klucz publiczny i informacje klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="a6554-134">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="a6554-135">**RSACryptoServiceProvider** klasy mogą być inicjowane w wartości **RSAParameters** struktury przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a6554-135">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="a6554-136">Prywatne klucze asymetryczne nigdy nie powinny być przechowywane, dosłownego wyrażenia lub w postaci zwykłego tekstu na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a6554-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="a6554-137">Jeśli musisz przechować klucz prywatny, należy użyć kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="a6554-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="a6554-138">Aby uzyskać więcej informacji na temat sposobu przechowywania klucza prywatnego w kontenerze kluczy, zobacz [porady: przechowywanie kluczy asymetrycznych w kontenerze klucza](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="a6554-138">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="a6554-139">Poniższy przykład kodu tworzy nowe wystąpienie klasy **RSACryptoServiceProvider** klasy, tworzenie pary kluczy publiczny/prywatny i zapisuje informacje o kluczu publicznym do **RSAParameters** struktury.</span><span class="sxs-lookup"><span data-stu-id="a6554-139">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim RSA as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim RSAKeyInfo As RSAParameters = RSA.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters RSAKeyInfo = RSA.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6554-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6554-140">See Also</span></span>  
 [<span data-ttu-id="a6554-141">Szyfrowanie danych</span><span class="sxs-lookup"><span data-stu-id="a6554-141">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
 [<span data-ttu-id="a6554-142">Odszyfrowywanie danych</span><span class="sxs-lookup"><span data-stu-id="a6554-142">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)  
 [<span data-ttu-id="a6554-143">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="a6554-143">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="a6554-144">Instrukcje: przechowywanie kluczy asymetrycznych w kontenerze kluczy</span><span class="sxs-lookup"><span data-stu-id="a6554-144">How to: Store Asymmetric Keys in a Key Container</span></span>](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
