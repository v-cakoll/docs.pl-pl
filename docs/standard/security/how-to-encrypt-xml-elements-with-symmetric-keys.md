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
ms.openlocfilehash: f5c221dc05787c6d76d998977069ad327a3dfa83
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881226"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="aa0e3-102">Porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych</span><span class="sxs-lookup"><span data-stu-id="aa0e3-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="aa0e3-103">Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="aa0e3-104">Szyfrowanie XML umożliwia przechowywania lub transportu poufnych kod XML, nie martwiąc się o łatwo odczytywanych danych.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="aa0e3-105">Ta procedura odszyfrowuje — element XML przy użyciu algorytmu Advanced Encryption Standard (AES), nazywany także Rijndael.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-105">This procedure decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="aa0e3-106">Aby uzyskać informacje o tym, jak można odszyfrować element XML, która została zaszyfrowana przy użyciu tej procedury, zobacz [porady: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="aa0e3-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="aa0e3-107">Korzystając z algorytmu symetrycznego, takich jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="aa0e3-108">Przykład w tej procedurze przyjęto założenie, zaszyfrowanego pliku XML zostaną odszyfrowane przy użyciu tego samego klucza, i że szyfrowanie i odszyfrowywanie strony zgody na algorytm i klucz do użycia.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="aa0e3-109">W tym przykładzie nie przechowuje ani szyfrowania klucza AES, w ramach zaszyfrowanego pliku XML.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="aa0e3-110">W tym przykładzie jest odpowiednie w sytuacjach, w których pojedynczej aplikacji wymaga szyfrowania danych na podstawie klucza sesji, przechowywane w pamięci lub na podstawie klucza silną kryptograficznie pochodzące z hasła.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="aa0e3-111">W sytuacjach, w której dwa lub więcej aplikacji muszą udostępniać zaszyfrowane dane XML należy wziąć pod uwagę przy użyciu schematu szyfrowania, na podstawie algorytmu asymetrycznego lub certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="aa0e3-112">Aby zaszyfrować element XML przy użyciu klucza symetrycznego</span><span class="sxs-lookup"><span data-stu-id="aa0e3-112">To encrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="aa0e3-113">Generuj klucz symetryczny za pomocą <xref:System.Security.Cryptography.RijndaelManaged> klasy.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="aa0e3-114">Ten klucz będzie używany do szyfrowania elementu XML.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="aa0e3-115">Utwórz <xref:System.Xml.XmlDocument> obiektu, ładując plik XML z dysku.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="aa0e3-116"><xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="aa0e3-117">Znajdź element określony w <xref:System.Xml.XmlDocument> obiektu i Utwórz nowy <xref:System.Xml.XmlElement> obiekt reprezentujący element, który chcesz zaszyfrować.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="aa0e3-118">W tym przykładzie `"creditcard"` elementu są szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="aa0e3-119">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i jej użyciu można zaszyfrować <xref:System.Xml.XmlElement> przy użyciu klucza symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="aa0e3-120"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda zwraca zaszyfrowany element jako tablicę bajtów zaszyfrowanych.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="aa0e3-121">Konstruowania <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu i wypełnianie jej identyfikator adresu URL elementu szyfrowanie XML.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="aa0e3-122">Ten identyfikator URL umożliwia odszyfrowywanie innych firm, dowiedzieć się, że plik XML zawiera element zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="aa0e3-123">Możesz użyć <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pola, aby określić identyfikator URL.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="aa0e3-124">Utwórz <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt, który jest inicjowany na identyfikator URL algorytm kryptograficzny używany do generowania klucza.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="aa0e3-125">Przekaż <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="aa0e3-126">Dodaj element zaszyfrowane dane <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="aa0e3-127">Zastąp element z oryginalnym <xref:System.Xml.XmlDocument> obiekt z <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="aa0e3-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa0e3-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa0e3-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="aa0e3-129">Compiling the Code</span></span>  
  
-   <span data-ttu-id="aa0e3-130">Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="aa0e3-131">Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="aa0e3-132">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="aa0e3-132">.NET Framework Security</span></span>  
 <span data-ttu-id="aa0e3-133">Nigdy nie przechowują klucza kryptograficznego w postaci zwykłego tekstu lub przenieść klucz między maszynami w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="aa0e3-134">Zamiast tego należy użyć bezpieczny kontener klucza do przechowywania kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="aa0e3-135">Po zakończeniu za pomocą klucza kryptograficznego, wyczyść to pole wyboru z pamięci, ustawiając poszczególne bajty do zera lub przez wywołanie <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy zarządzanej kryptografii.</span><span class="sxs-lookup"><span data-stu-id="aa0e3-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa0e3-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa0e3-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>  
- [<span data-ttu-id="aa0e3-137">Instrukcje: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych</span><span class="sxs-lookup"><span data-stu-id="aa0e3-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
