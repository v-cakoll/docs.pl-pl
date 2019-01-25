---
title: Szyfrowanie i odszyfrowywanie ciągów w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: ee3bcd1358536e6fd9bed5c4fec7845fdf441d86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723488"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="628ed-102">Przewodnik: Szyfrowanie i odszyfrowywanie ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="628ed-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="628ed-103">W tym instruktażu dowiesz się, jak używać <xref:System.Security.Cryptography.DESCryptoServiceProvider> klasy szyfrowanie i odszyfrowywanie ciągów za pomocą wersji dostawcy usług kryptograficznych Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorytmu.</span><span class="sxs-lookup"><span data-stu-id="628ed-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="628ed-104">Pierwszym krokiem jest utworzyć klasę otoki prostą, która hermetyzuje algorytmu 3DES i przechowuje zaszyfrowane dane jako ciąg zakodowany base-64.</span><span class="sxs-lookup"><span data-stu-id="628ed-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="628ed-105">Następnie tej otoki służy do bezpiecznego przechowywania prywatnych danych użytkowników w pliku tekstowym dostępny publicznie.</span><span class="sxs-lookup"><span data-stu-id="628ed-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="628ed-106">Szyfrowanie można użyć do ochrony wpisu tajnego użytkownika (na przykład hasła) i poświadczeń nie można go odczytać przez nieautoryzowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="628ed-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="628ed-107">To jest ochrona tożsamości autoryzowanym użytkownikiem z skradzione, co chroni zasoby użytkownika i zapewnia uznawania.</span><span class="sxs-lookup"><span data-stu-id="628ed-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="628ed-108">Szyfrowanie umożliwia również ochronę danych użytkownika przed dostępem nieautoryzowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="628ed-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="628ed-109">Aby uzyskać więcej informacji, zobacz [usługi kryptograficzne](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="628ed-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="628ed-110">Rijndael (teraz nazywana Advanced Encryption Standard [AES]) i algorytmy Triple Data Encryption Standard (3DES) zapewniają większe bezpieczeństwo niż DES, ponieważ są one więcej wymaga dużej mocy obliczeniowej.</span><span class="sxs-lookup"><span data-stu-id="628ed-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="628ed-111">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="628ed-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="628ed-112">Aby utworzyć otokę szyfrowania</span><span class="sxs-lookup"><span data-stu-id="628ed-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="628ed-113">Utwórz `Simple3Des` klasy do hermetyzacji metod szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="628ed-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  <span data-ttu-id="628ed-114">Dodaj import obszaru nazw kryptografii na początku pliku który zawiera `Simple3Des` klasy.</span><span class="sxs-lookup"><span data-stu-id="628ed-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  <span data-ttu-id="628ed-115">W `Simple3Des` klasy, Dodaj pole prywatne do przechowywania dostawcy usług kryptograficznych 3DES.</span><span class="sxs-lookup"><span data-stu-id="628ed-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  <span data-ttu-id="628ed-116">Dodaj metody prywatnej, która tworzy tablicę bajtów o określonej długości ze skrótu z określonym kluczem.</span><span class="sxs-lookup"><span data-stu-id="628ed-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  <span data-ttu-id="628ed-117">Dodaj Konstruktor do zainicjowania dostawcy usług kryptograficznych 3DES.</span><span class="sxs-lookup"><span data-stu-id="628ed-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="628ed-118">`key` Parametr określa `EncryptData` i `DecryptData` metody.</span><span class="sxs-lookup"><span data-stu-id="628ed-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  <span data-ttu-id="628ed-119">Dodaj metodę publiczną, która szyfruje ciągu.</span><span class="sxs-lookup"><span data-stu-id="628ed-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  <span data-ttu-id="628ed-120">Dodaj metodę publiczną, która odszyfrowuje ciągu.</span><span class="sxs-lookup"><span data-stu-id="628ed-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     <span data-ttu-id="628ed-121">Klasa otoki może teraz służyć do ochrony zasobów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="628ed-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="628ed-122">W tym przykładzie jest używany do bezpiecznego przechowywania prywatnych danych użytkowników w pliku tekstowym dostępny publicznie.</span><span class="sxs-lookup"><span data-stu-id="628ed-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="628ed-123">Aby przetestować otoki szyfrowania</span><span class="sxs-lookup"><span data-stu-id="628ed-123">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="628ed-124">W osobnej klasy, Dodaj metodę, która używa otoki `EncryptData` metodę, aby zaszyfrować ciągu i zapisz go do użytkownika w folderze Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="628ed-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  <span data-ttu-id="628ed-125">Dodaj metodę, która odczytuje zaszyfrowany ciąg od użytkownika w folderze Moje dokumenty i odszyfrowuje ciągu z otoką `DecryptData` metody.</span><span class="sxs-lookup"><span data-stu-id="628ed-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  <span data-ttu-id="628ed-126">Dodaj kod interfejsu użytkownika, aby wywołać `TestEncoding` i `TestDecoding` metody.</span><span class="sxs-lookup"><span data-stu-id="628ed-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="628ed-127">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="628ed-127">Run the application.</span></span>  
  
     <span data-ttu-id="628ed-128">Podczas testowania aplikacji, zwróć uwagę, że jej nie powoduje odszyfrowania danych jeśli podano nieprawidłowe hasło.</span><span class="sxs-lookup"><span data-stu-id="628ed-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="628ed-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="628ed-129">See also</span></span>
- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="628ed-130">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="628ed-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
