---
title: szyfrowanie i odszyfrowywanie danych
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 36e405c7362993471d3e6da8e319bccb854e1026
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343586"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="5e32c-102">Wskazówki: szyfrowanie i odszyfrowywanie ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e32c-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="5e32c-103">W tym instruktażu pokazano, jak za pomocą klasy <xref:System.Security.Cryptography.DESCryptoServiceProvider> szyfrować i odszyfrowywać ciągi przy użyciu wersji dostawcy usług kryptograficznych (CSP) algorytmu Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>).</span><span class="sxs-lookup"><span data-stu-id="5e32c-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="5e32c-104">Pierwszym krokiem jest utworzenie prostej klasy otoki, która hermetyzuje algorytm 3DES i przechowuje zaszyfrowane dane jako ciąg zakodowany Base-64.</span><span class="sxs-lookup"><span data-stu-id="5e32c-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="5e32c-105">Następnie ten otoka służy do bezpiecznego przechowywania prywatnych danych użytkownika w publicznie dostępnym pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="5e32c-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="5e32c-106">Za pomocą szyfrowania można chronić klucze tajne użytkowników (na przykład hasła) i wprowadzać poświadczenia jako nieczytelne dla nieautoryzowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5e32c-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="5e32c-107">Pozwala to chronić tożsamość autoryzowanego użytkownika przed kradzieżą, która chroni zasoby użytkownika i nie umożliwia wyparcia.</span><span class="sxs-lookup"><span data-stu-id="5e32c-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="5e32c-108">Szyfrowanie umożliwia również ochronę danych użytkownika przed dostępem nieautoryzowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5e32c-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="5e32c-109">Aby uzyskać więcej informacji, zobacz [usługi kryptograficzne](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="5e32c-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5e32c-110">Rijndael (teraz określane jako Advanced Encryption Standard [AES]) i algorytmy Triple Data Encryption Standard (3DES) zapewniają lepsze zabezpieczenia niż algorytm DES, ponieważ znacznie intensywnie korzystają z nich.</span><span class="sxs-lookup"><span data-stu-id="5e32c-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="5e32c-111">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="5e32c-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="5e32c-112">Aby utworzyć otokę szyfrowania</span><span class="sxs-lookup"><span data-stu-id="5e32c-112">To create the encryption wrapper</span></span>  
  
1. <span data-ttu-id="5e32c-113">Utwórz klasę `Simple3Des`, aby hermetyzować metody szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="5e32c-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. <span data-ttu-id="5e32c-114">Dodaj Import przestrzeni nazw kryptografii do początku pliku, który zawiera klasę `Simple3Des`.</span><span class="sxs-lookup"><span data-stu-id="5e32c-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. <span data-ttu-id="5e32c-115">W klasie `Simple3Des` Dodaj pole private, aby zachować dostawcę usług kryptograficznych 3DES.</span><span class="sxs-lookup"><span data-stu-id="5e32c-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. <span data-ttu-id="5e32c-116">Dodaj prywatną metodę, która tworzy tablicę bajtową o określonej długości ze skrótu określonego klucza.</span><span class="sxs-lookup"><span data-stu-id="5e32c-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. <span data-ttu-id="5e32c-117">Dodaj Konstruktor, aby zainicjować dostawcę usług kryptograficznych 3DES.</span><span class="sxs-lookup"><span data-stu-id="5e32c-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="5e32c-118">`key` parametr steruje metodami `EncryptData` i `DecryptData`.</span><span class="sxs-lookup"><span data-stu-id="5e32c-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. <span data-ttu-id="5e32c-119">Dodaj metodę publiczną, która szyfruje ciąg.</span><span class="sxs-lookup"><span data-stu-id="5e32c-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. <span data-ttu-id="5e32c-120">Dodaj metodę publiczną, która odszyfrowuje ciąg.</span><span class="sxs-lookup"><span data-stu-id="5e32c-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     <span data-ttu-id="5e32c-121">Klasy otoki można teraz używać do ochrony zasobów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5e32c-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="5e32c-122">W tym przykładzie jest używany do bezpiecznego przechowywania prywatnych danych użytkownika w publicznie dostępnym pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="5e32c-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="5e32c-123">Aby przetestować otokę szyfrowania</span><span class="sxs-lookup"><span data-stu-id="5e32c-123">To test the encryption wrapper</span></span>  
  
1. <span data-ttu-id="5e32c-124">W oddzielnym klasie Dodaj metodę, która używa metody `EncryptData` otoki, aby zaszyfrować ciąg i zapisać go w folderze Moje dokumenty użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5e32c-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. <span data-ttu-id="5e32c-125">Dodaj metodę, która odczytuje zaszyfrowany ciąg z folderu Moje dokumenty użytkownika i odszyfrowuje ciąg za pomocą metody `DecryptData` otoki.</span><span class="sxs-lookup"><span data-stu-id="5e32c-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. <span data-ttu-id="5e32c-126">Dodaj kod interfejsu użytkownika, aby wywołać metody `TestEncoding` i `TestDecoding`.</span><span class="sxs-lookup"><span data-stu-id="5e32c-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4. <span data-ttu-id="5e32c-127">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="5e32c-127">Run the application.</span></span>  
  
     <span data-ttu-id="5e32c-128">Podczas testowania aplikacji należy zauważyć, że nie odszyfruje danych w przypadku podania nieprawidłowego hasła.</span><span class="sxs-lookup"><span data-stu-id="5e32c-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e32c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e32c-129">See also</span></span>

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="5e32c-130">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="5e32c-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
