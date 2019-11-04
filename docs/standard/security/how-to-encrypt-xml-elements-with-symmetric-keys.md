---
title: 'Porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b792fd6eea0a33b0143fafa03641a78947d7e127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458073"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="7dfe9-102">Porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych</span><span class="sxs-lookup"><span data-stu-id="7dfe9-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="7dfe9-103">Możesz użyć klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml>, aby zaszyfrować element w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="7dfe9-104">Szyfrowanie XML umożliwia przechowywanie i transportowanie poufnego kodu XML bez obaw o dane, które są łatwo odczytywane.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="7dfe9-105">Ta procedura służy do szyfrowania elementu XML przy użyciu algorytmu Advanced Encryption Standard (AES), znanego również jako Rijndael.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-105">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="7dfe9-106">Informacje o sposobie odszyfrowywania elementu XML, który został zaszyfrowany przy użyciu tej procedury, można znaleźć w temacie [How to: Deszyfruj elementy XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="7dfe9-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="7dfe9-107">W przypadku używania algorytmu symetrycznego, takiego jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="7dfe9-108">W przykładzie tej procedury przyjęto założenie, że zaszyfrowany kod XML zostanie odszyfrowany przy użyciu tego samego klucza, a strony szyfrujące i odszyfrowuje zgadzają się na algorytm i klucz do użycia.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="7dfe9-109">Ten przykład nie przechowuje ani nie szyfruje klucza AES w zaszyfrowanym formacie XML.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="7dfe9-110">Ten przykład jest odpowiedni dla sytuacji, w których pojedyncza aplikacja musi szyfrować dane na podstawie klucza sesji przechowywanego w pamięci lub na podstawie kryptograficznego klucza silnego pochodzącego z hasła.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="7dfe9-111">W przypadku, gdy co najmniej dwie aplikacje muszą udostępniać zaszyfrowane dane XML, należy rozważyć użycie schematu szyfrowania na podstawie algorytmu asymetrycznego lub certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="7dfe9-112">Aby zaszyfrować element XML przy użyciu klucza symetrycznego</span><span class="sxs-lookup"><span data-stu-id="7dfe9-112">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="7dfe9-113">Generuj klucz symetryczny przy użyciu klasy <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="7dfe9-114">Ten klucz będzie używany do szyfrowania elementu XML.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="7dfe9-115">Utwórz obiekt <xref:System.Xml.XmlDocument>, ładując plik XML z dysku.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="7dfe9-116">Obiekt <xref:System.Xml.XmlDocument> zawiera element XML do zaszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="7dfe9-117">Znajdź określony element w obiekcie <xref:System.Xml.XmlDocument> i Utwórz nowy obiekt <xref:System.Xml.XmlElement> do reprezentowania elementu, który chcesz zaszyfrować.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="7dfe9-118">W tym przykładzie element `"creditcard"` jest szyfrowany.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="7dfe9-119">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> i użyj go do zaszyfrowania <xref:System.Xml.XmlElement> przy użyciu klucza symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="7dfe9-120">Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> zwraca zaszyfrowany element jako tablicę szyfrowanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="7dfe9-121">Utwórz obiekt <xref:System.Security.Cryptography.Xml.EncryptedData> i wypełnij go identyfikatorem URL elementu szyfrowania XML.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="7dfe9-122">Ten identyfikator adresu URL umożliwia osobie odszyfrowanej, że kod XML zawiera zaszyfrowany element.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="7dfe9-123">Możesz użyć pola <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>, aby określić identyfikator URL.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="7dfe9-124">Utwórz obiekt <xref:System.Security.Cryptography.Xml.EncryptionMethod>, który jest zainicjowany do identyfikatora URL algorytmu kryptograficznego użytego do wygenerowania klucza.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="7dfe9-125">Przekaż obiekt <xref:System.Security.Cryptography.Xml.EncryptionMethod> do właściwości <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="7dfe9-126">Dodaj dane zaszyfrowanego elementu do obiektu <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="7dfe9-127">Zastąp element z oryginalnego obiektu <xref:System.Xml.XmlDocument> elementem <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="7dfe9-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7dfe9-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="7dfe9-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7dfe9-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="7dfe9-130">Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="7dfe9-131">Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7dfe9-132">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7dfe9-132">.NET Framework Security</span></span>  
 <span data-ttu-id="7dfe9-133">Nie przechowuj klucza kryptograficznego w postaci zwykłego tekstu lub przesyłaj klucz między maszynami w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="7dfe9-134">Zamiast tego należy użyć bezpiecznego kontenera kluczy do przechowywania kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="7dfe9-135">Gdy skończysz korzystać z klucza kryptograficznego, usuń go z pamięci, ustawiając każdy bajt na zero lub wywołując metodę <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> zarządzanej klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="7dfe9-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfe9-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dfe9-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="7dfe9-137">Instrukcje: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych</span><span class="sxs-lookup"><span data-stu-id="7dfe9-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
