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
ms.openlocfilehash: fd377cd470d361f5a46c662ab37780713a2d3804
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706126"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="0dd3b-102">Porady: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych</span><span class="sxs-lookup"><span data-stu-id="0dd3b-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="0dd3b-103">Możesz użyć klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml>, aby zaszyfrować element w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="0dd3b-104">Szyfrowanie XML umożliwia przechowywanie i transportowanie poufnego kodu XML bez obaw o dane, które są łatwo odczytywane.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="0dd3b-105">Ten przykład kodu odszyfrowuje element XML przy użyciu algorytmu Advanced Encryption Standard (AES), znanego również jako Rijndael.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="0dd3b-106">Informacje o sposobie szyfrowania elementu XML przy użyciu tej procedury znajdują się w temacie [How to: szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="0dd3b-107">W przypadku używania algorytmu symetrycznego, takiego jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="0dd3b-108">W przykładzie tej procedury przyjęto założenie, że zaszyfrowany kod XML został zaszyfrowany przy użyciu tego samego klucza, a strony szyfrujące i odszyfrowuje zgadzają się na algorytm i klucz do użycia.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="0dd3b-109">Ten przykład nie przechowuje ani nie szyfruje klucza AES w zaszyfrowanym formacie XML.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="0dd3b-110">Ten przykład jest odpowiedni dla sytuacji, w których pojedyncza aplikacja musi szyfrować dane na podstawie klucza sesji przechowywanego w pamięci lub na podstawie kryptograficznego klucza silnego pochodzącego z hasła.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="0dd3b-111">W przypadku, gdy co najmniej dwie aplikacje muszą udostępniać zaszyfrowane dane XML, należy rozważyć użycie schematu szyfrowania na podstawie algorytmu asymetrycznego lub certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="0dd3b-112">Aby odszyfrować element XML przy użyciu klucza symetrycznego</span><span class="sxs-lookup"><span data-stu-id="0dd3b-112">To decrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="0dd3b-113">Szyfruj element XML z wcześniej wygenerowanym kluczem przy użyciu technik opisanych w artykule [How to: Szyfruj elementy XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2. <span data-ttu-id="0dd3b-114">Znajdź <`EncryptedData`> element (zdefiniowany przez standard szyfrowania XML) w obiekcie <xref:System.Xml.XmlDocument>, który zawiera zaszyfrowany kod XML i Utwórz nowy obiekt <xref:System.Xml.XmlElement> do reprezentowania tego elementu.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. <span data-ttu-id="0dd3b-115">Utwórz obiekt <xref:System.Security.Cryptography.Xml.EncryptedData>, ładując pierwotne dane XML z wcześniej utworzonego obiektu <xref:System.Xml.XmlElement>.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. <span data-ttu-id="0dd3b-116">Utwórz nowy obiekt <xref:System.Security.Cryptography.Xml.EncryptedXml> i użyj go do odszyfrowania danych XML przy użyciu tego samego klucza, który był używany do szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. <span data-ttu-id="0dd3b-117">Zastąp zaszyfrowany element nowo odszyfrowanym tekstem w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="0dd3b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="0dd3b-118">Example</span></span>  
 <span data-ttu-id="0dd3b-119">W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowany program.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="0dd3b-120">Zakłada również, że `"test.xml"` zawiera `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="0dd3b-121">Można umieścić następujący kod XML w pliku o nazwie `test.xml` i użyć go w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="0dd3b-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0dd3b-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="0dd3b-123">Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="0dd3b-124">Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0dd3b-125">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0dd3b-125">.NET Framework Security</span></span>  
 <span data-ttu-id="0dd3b-126">Nie przechowuj klucza kryptograficznego w postaci zwykłego tekstu lub przesyłaj klucz między maszynami w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-126">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
 <span data-ttu-id="0dd3b-127">Po zakończeniu korzystania z symetrycznego klucza kryptograficznego Wyczyść go z pamięci, ustawiając każdy bajt na zero lub wywołując metodę <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> zarządzanej klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-127">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd3b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0dd3b-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="0dd3b-129">Instrukcje: szyfrowanie elementów XML przy użyciu kluczy symetrycznych</span><span class="sxs-lookup"><span data-stu-id="0dd3b-129">How to: Encrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
