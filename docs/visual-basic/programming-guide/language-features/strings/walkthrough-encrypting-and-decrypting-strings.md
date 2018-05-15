---
title: Szyfrowanie i odszyfrowywanie ciągów w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 96e56ab315a739fef9d5499b076a077f5294f39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="5064f-102">Wskazówki: szyfrowanie i odszyfrowywanie ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5064f-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="5064f-103">Ten przewodnik przedstawia sposób użycia <xref:System.Security.Cryptography.DESCryptoServiceProvider> klasy do szyfrowania i odszyfrowywania ciągów za pomocą wersji dostawcy usług kryptograficznych Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorytmu.</span><span class="sxs-lookup"><span data-stu-id="5064f-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="5064f-104">Pierwszym krokiem jest można utworzyć klasy otoki proste, który hermetyzuje algorytmu 3DES i przechowuje zaszyfrowane dane jako ciąg zakodowany base-64.</span><span class="sxs-lookup"><span data-stu-id="5064f-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="5064f-105">Następnie tej otoki służy bezpiecznie przechowywać prywatnych danych użytkowników w pliku tekstowym publicznie.</span><span class="sxs-lookup"><span data-stu-id="5064f-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="5064f-106">Należy używać szyfrowania, aby chronić hasła użytkownika (na przykład hasła) i wprowadzić poświadczenia niemożliwe do odczytania przez nieautoryzowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5064f-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="5064f-107">To może chronić tożsamość autoryzowanym użytkownikiem z skradzione, która chroni zasoby użytkownika oraz udostępnia wyłączność podpisu.</span><span class="sxs-lookup"><span data-stu-id="5064f-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="5064f-108">Szyfrowanie można również ochronę danych użytkownika z uzyskiwany przez nieautoryzowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5064f-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="5064f-109">Aby uzyskać więcej informacji, zobacz [usługi kryptograficzne](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="5064f-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5064f-110">Algorytmy Triple Data Encryption Standard (3DES) i Rijndael (teraz nazywane Advanced Encryption Standard [AES]) zawiera większe bezpieczeństwo niż metoda DES, ponieważ są one więcej znacznym w praktyce.</span><span class="sxs-lookup"><span data-stu-id="5064f-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="5064f-111">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="5064f-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="5064f-112">Aby utworzyć otoki szyfrowania</span><span class="sxs-lookup"><span data-stu-id="5064f-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="5064f-113">Utwórz `Simple3Des` klasy w celu hermetyzacji metody szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="5064f-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  <span data-ttu-id="5064f-114">Dodaj importu kryptografii przestrzeni nazw na początku pliku, który zawiera `Simple3Des` klasy.</span><span class="sxs-lookup"><span data-stu-id="5064f-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  <span data-ttu-id="5064f-115">W `Simple3Des` klasy, Dodaj pole prywatne do przechowywania 3DES dostawcy usług kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="5064f-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  <span data-ttu-id="5064f-116">Dodaj metody prywatnej, która tworzy tablicę bajtów o określonej długości ze skrótu określonego klucza.</span><span class="sxs-lookup"><span data-stu-id="5064f-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  <span data-ttu-id="5064f-117">Dodaj Konstruktor do zainicjowania dostawcy usług kryptograficznych 3DES.</span><span class="sxs-lookup"><span data-stu-id="5064f-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="5064f-118">`key` Sterowania parametrami `EncryptData` i `DecryptData` metody.</span><span class="sxs-lookup"><span data-stu-id="5064f-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  <span data-ttu-id="5064f-119">Dodaj publiczną metodę, który szyfruje ciąg.</span><span class="sxs-lookup"><span data-stu-id="5064f-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  <span data-ttu-id="5064f-120">Dodaj publiczną metodę odszyfrowujący ciąg.</span><span class="sxs-lookup"><span data-stu-id="5064f-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     <span data-ttu-id="5064f-121">Klasa otoki można teraz używać do ochrony zasobów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5064f-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="5064f-122">W tym przykładzie jest używany bezpiecznie przechowywać prywatnych danych użytkowników w pliku tekstowym publicznie.</span><span class="sxs-lookup"><span data-stu-id="5064f-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="5064f-123">Aby przetestować otoki szyfrowania</span><span class="sxs-lookup"><span data-stu-id="5064f-123">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="5064f-124">W osobnej klasy, Dodaj metody, która używa otoki `EncryptData` metodę szyfrowania ciągu i zapisać go do użytkownika do folderu Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="5064f-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  <span data-ttu-id="5064f-125">Dodaj metodę, która odczytuje zaszyfrowanego ciągu użytkownika do folderu Moje dokumenty i odszyfrowuje ciągu z otoką `DecryptData` metody.</span><span class="sxs-lookup"><span data-stu-id="5064f-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  <span data-ttu-id="5064f-126">Dodaj kod interfejsu użytkownika do wywołania `TestEncoding` i `TestDecoding` metody.</span><span class="sxs-lookup"><span data-stu-id="5064f-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="5064f-127">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="5064f-127">Run the application.</span></span>  
  
     <span data-ttu-id="5064f-128">Podczas testowania aplikacji, zwróć uwagę, że jej nie powoduje odszyfrowania danych Jeśli podasz nieprawidłowe hasło.</span><span class="sxs-lookup"><span data-stu-id="5064f-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5064f-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5064f-129">See Also</span></span>  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [<span data-ttu-id="5064f-130">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="5064f-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
