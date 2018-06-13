---
title: 'Porady: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da4f65d1510f22e05cef4295a342163bba2d1958
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583383"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="f3c14-102">Porady: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych</span><span class="sxs-lookup"><span data-stu-id="f3c14-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="f3c14-103">Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="f3c14-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="f3c14-104">Szyfrowanie XML służy do przechowywania lub transportu poufnych XML, nie martwiąc się o łatwo odczytywane dane.</span><span class="sxs-lookup"><span data-stu-id="f3c14-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="f3c14-105">W tym przykładzie kodu odszyfrowuje — element XML przy użyciu algorytmu szyfrowania AES (Advanced Standard), nazywany także Rijndael.</span><span class="sxs-lookup"><span data-stu-id="f3c14-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="f3c14-106">Aby uzyskać informacje o szyfrowaniu elementu XML za pomocą tej procedury, zobacz [porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="f3c14-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="f3c14-107">Korzystając z algorytmu symetrycznego, takich jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.</span><span class="sxs-lookup"><span data-stu-id="f3c14-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="f3c14-108">Przykład w tej procedurze założono, że zaszyfrowane XML została zaszyfrowana przy użyciu tego samego klucza, a szyfrowanie i odszyfrowywanie strony wyrażanie zgody na algorytm i klucz do użycia.</span><span class="sxs-lookup"><span data-stu-id="f3c14-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="f3c14-109">W tym przykładzie nie przechowuje ani szyfrowania w zawartości XML zaszyfrowanego klucza AES.</span><span class="sxs-lookup"><span data-stu-id="f3c14-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="f3c14-110">W tym przykładzie jest przydatne w sytuacjach, w których pojedynczej aplikacji wymaga szyfrowania danych na podstawie klucza sesji, przechowywane w pamięci lub oparte na silną kryptograficznie klucza generowanego na podstawie hasła.</span><span class="sxs-lookup"><span data-stu-id="f3c14-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="f3c14-111">W sytuacjach, w których dwie lub więcej aplikacji musi udostępniać zaszyfrowanych danych XML Rozważ użycie schematu szyfrowania, na podstawie algorytmu asymetrycznego lub certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="f3c14-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="f3c14-112">Aby odszyfrować element XML przy użyciu klucza symetrycznego</span><span class="sxs-lookup"><span data-stu-id="f3c14-112">To decrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="f3c14-113">Szyfrowanie — element XML przy użyciu klucza wcześniej wygenerowanych przy użyciu metod opisanych w [porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="f3c14-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="f3c14-114">Znajdź <`EncryptedData`> elementu (określoną przez XML Encryption standard) w <xref:System.Xml.XmlDocument> obiekt zawierający zaszyfrowanego pliku XML i utworzyć nową <xref:System.Xml.XmlElement> obiektu do reprezentowania tego elementu.</span><span class="sxs-lookup"><span data-stu-id="f3c14-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  <span data-ttu-id="f3c14-115">Utwórz <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu przez załadowanie nieprzetworzone dane XML z utworzonej wcześniej <xref:System.Xml.XmlElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f3c14-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  <span data-ttu-id="f3c14-116">Utwórz nową <xref:System.Security.Cryptography.Xml.EncryptedXml> obiektu i użyć go do odszyfrowywania danych XML przy użyciu tego samego klucza, który był używany do szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="f3c14-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  <span data-ttu-id="f3c14-117">Zastąp element zaszyfrowane za pomocą elementu nowo odszyfrowane w postaci zwykłego tekstu w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="f3c14-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="f3c14-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3c14-118">Example</span></span>  
 <span data-ttu-id="f3c14-119">W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co program skompilowany.</span><span class="sxs-lookup"><span data-stu-id="f3c14-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="f3c14-120">Założono również, że `"test.xml"` zawiera `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="f3c14-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="f3c14-121">Następujący kod XML można umieścić w pliku o nazwie `test.xml` i użyć w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f3c14-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3c14-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f3c14-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f3c14-123">Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="f3c14-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="f3c14-124">Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="f3c14-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f3c14-125">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f3c14-125">.NET Framework Security</span></span>  
 <span data-ttu-id="f3c14-126">Nigdy nie przechowują klucza kryptograficznego w postaci zwykłego tekstu lub przenieść klucz między komputerami w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="f3c14-126">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
 <span data-ttu-id="f3c14-127">Gdy wszystko będzie gotowe za pomocą klucza szyfrowania symetrycznego, wyczyść go z pamięci przez ustawienie każdego bajtu na wartość zero lub wywoływania <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy kryptografii zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="f3c14-127">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c14-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3c14-128">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="f3c14-129">Instrukcje: szyfrowanie elementów XML przy użyciu kluczy symetrycznych</span><span class="sxs-lookup"><span data-stu-id="f3c14-129">How to: Encrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
