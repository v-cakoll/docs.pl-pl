---
title: 'Porady: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 329569ea148542ff596057d9eb9efe2e95768341
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="efa31-102">Porady: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych</span><span class="sxs-lookup"><span data-stu-id="efa31-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="efa31-103">Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw do szyfrowania i odszyfrowywania element w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="efa31-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="efa31-104">Szyfrowanie XML jest standardowym sposobem exchange lub przechowywania zaszyfrowanych danych XML, nie martwiąc się o łatwo odczytywane dane.</span><span class="sxs-lookup"><span data-stu-id="efa31-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="efa31-105">Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz zalecenia konsorcjum World Wide Web (W3C) [składnia XML podpisu i przetwarzania](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="efa31-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="efa31-106">Przykład w tej procedurze odszyfrowuje element XML, która została zaszyfrowana przy użyciu metod opisanych w [porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="efa31-106">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="efa31-107">Znajdzie <`EncryptedData`> elementu odszyfrowuje elementu, a następnie zastępuje element oryginalny element XML w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="efa31-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="efa31-108">W tym przykładzie odszyfrowuje elementu XML za pomocą dwóch kluczy.</span><span class="sxs-lookup"><span data-stu-id="efa31-108">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="efa31-109">Go pobiera wcześniej wygenerowanych prywatnego klucza RSA z kontenera kluczy, a następnie używa kluczy RSA do odszyfrowania klucza sesji w <`EncryptedKey`> elementu <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="efa31-109">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="efa31-110">W przykładzie użyto następnie klucza sesji do odszyfrowania elementu XML.</span><span class="sxs-lookup"><span data-stu-id="efa31-110">The example then uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="efa31-111">W tym przykładzie jest przydatne w sytuacjach, gdy wiele aplikacji muszą współużytkować zaszyfrowanych danych lub gdy aplikacja ma zapisać zaszyfrowanych danych w okresie, które działa między.</span><span class="sxs-lookup"><span data-stu-id="efa31-111">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="efa31-112">Aby odszyfrować za pomocą klucza asymetrycznego — element XML</span><span class="sxs-lookup"><span data-stu-id="efa31-112">To decrypt an XML element with an asymmetric key</span></span>  
  
1.  <span data-ttu-id="efa31-113">Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="efa31-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="efa31-114">Pobrać wcześniej wygenerowanych klucza asymetrycznego z kontenera przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu.</span><span class="sxs-lookup"><span data-stu-id="efa31-114">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="efa31-115">Klucz jest automatycznie pobierany z kontenera kluczy podczas przekazywania <xref:System.Security.Cryptography.CspParameters> do obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="efa31-115">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="efa31-116">Utwórz nową <xref:System.Security.Cryptography.Xml.EncryptedXml> obiektu do odszyfrowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="efa31-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  <span data-ttu-id="efa31-117">Dodaj mapowanie nazwa/klucza do skojarzenia z elementem w tym dokumencie, który powinien być odszyfrowane kluczy RSA.</span><span class="sxs-lookup"><span data-stu-id="efa31-117">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="efa31-118">Należy użyć tej samej nazwy dla klucza, który został użyty podczas szyfrowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="efa31-118">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="efa31-119">Należy pamiętać, że ta nazwa jest oddzielony od Nazwa używana do identyfikacji klucza w kontenerze klucza podanego w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="efa31-119">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  <span data-ttu-id="efa31-120">Wywołanie <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody do odszyfrowania <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="efa31-120">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="efa31-121">Ta metoda używa klucza RSA do odszyfrowania klucza sesji i automatycznie używa klucza sesji do odszyfrowania elementu XML.</span><span class="sxs-lookup"><span data-stu-id="efa31-121">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="efa31-122">Automatycznie zastępuje <`EncryptedData`> elementu z oryginalnego zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="efa31-122">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  <span data-ttu-id="efa31-123">Zapisz dokument XML.</span><span class="sxs-lookup"><span data-stu-id="efa31-123">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="efa31-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="efa31-124">Example</span></span>  
 <span data-ttu-id="efa31-125">W tym przykładzie przyjęto założenie, że plik o nazwie `test.xml` istnieje w tym samym katalogu co program skompilowany.</span><span class="sxs-lookup"><span data-stu-id="efa31-125">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="efa31-126">Założono również, że `test.xml` zawiera element XML, która została zaszyfrowana przy użyciu metod opisanych w [porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="efa31-126">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="efa31-127">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="efa31-127">Compiling the Code</span></span>  
  
-   <span data-ttu-id="efa31-128">Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="efa31-128">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="efa31-129">Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="efa31-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="efa31-130">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="efa31-130">.NET Framework Security</span></span>  
 <span data-ttu-id="efa31-131">Nigdy nie przechowują symetrycznego klucza kryptograficznego w postaci zwykłego tekstu lub transfer klucza symetrycznego między komputerami w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="efa31-131">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="efa31-132">Ponadto nigdy nie magazynu lub przenieść klucz prywatny para kluczy asymetrycznych w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="efa31-132">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="efa31-133">Aby uzyskać więcej informacji na temat symetrycznego i asymetrycznego kluczy kryptograficznych, zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="efa31-133">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="efa31-134">Nigdy nie osadzaj klucza bezpośrednio w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="efa31-134">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="efa31-135">Osadzony kluczy można łatwo odczytać z zestawu przy użyciu [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstu, takiego jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="efa31-135">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="efa31-136">Gdy wszystko będzie gotowe za pomocą klucza kryptograficznego, wyczyść go z pamięci przez ustawienie każdego bajtu na wartość zero lub wywoływania <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy kryptografii zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="efa31-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="efa31-137">Klucze kryptograficzne czasami może odczytywać pamięci przez debuger lub odczytu z dysku twardego, jeśli lokalizacji pamięci jest stronicowana na dysk.</span><span class="sxs-lookup"><span data-stu-id="efa31-137">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa31-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efa31-138">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="efa31-139">Instrukcje: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych</span><span class="sxs-lookup"><span data-stu-id="efa31-139">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
