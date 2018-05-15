---
title: 'Porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6840a9005aaca4805252298e1ceaf7e51f38971
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="7248f-102">Porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych</span><span class="sxs-lookup"><span data-stu-id="7248f-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="7248f-103">Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="7248f-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="7248f-104">Szyfrowanie XML jest standardowym sposobem exchange lub przechowywania zaszyfrowanych danych XML, nie martwiąc się o łatwo odczytywane dane.</span><span class="sxs-lookup"><span data-stu-id="7248f-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="7248f-105">Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz specyfikację sieci World Wide Web konsorcjum W3C szyfrowanie XML zlokalizowanej w http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="7248f-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="7248f-106">Szyfrowanie XML służy do zastępowania żadnych — element XML lub dokument z <`EncryptedData`> element, który zawiera zaszyfrowane dane XML.</span><span class="sxs-lookup"><span data-stu-id="7248f-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="7248f-107"><`EncryptedData`> Element może również zawierać elementy podrzędne, które zawierają informacji o kluczach i procesy użyty podczas szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7248f-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="7248f-108">Szyfrowanie XML umożliwia dokumentu zawiera wiele elementów zaszyfrowane i pozwala element zaszyfrowanie wiele razy.</span><span class="sxs-lookup"><span data-stu-id="7248f-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="7248f-109">Przykład kodu w tej procedurze przedstawiono sposób tworzenia <`EncryptedData`> element wraz z kilku elementów sub, w których można później podczas odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="7248f-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="7248f-110">W tym przykładzie szyfruje elementu XML za pomocą dwóch kluczy.</span><span class="sxs-lookup"><span data-stu-id="7248f-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="7248f-111">Generuje pary kluczy publiczny/prywatny RSA, a zapisuje pary kluczy do bezpiecznego kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="7248f-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="7248f-112">Przykład tworzy następnie klucz sesji oddzielne przy użyciu algorytmu szyfrowania AES (Advanced Standard), nazywany również algorytmu Rijndael.</span><span class="sxs-lookup"><span data-stu-id="7248f-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm, also called the Rijndael algorithm.</span></span>  <span data-ttu-id="7248f-113">Przykład używa klucza sesji AES do zaszyfrowania dokumentu XML, a następnie używa klucza publicznego RSA do szyfrowania klucza sesji AES.</span><span class="sxs-lookup"><span data-stu-id="7248f-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="7248f-114">Na koniec przykładzie zapisuje zaszyfrowanego klucza sesji AES i szyfrowania danych XML do dokumentu XML w ramach nowej <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="7248f-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="7248f-115">Aby odszyfrować elementu XML, pobrać przy użyciu kontenera kluczy RSA klucza prywatnego, go użyć do odszyfrowania klucza sesji i następnie użyć klucza sesji do odszyfrowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7248f-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="7248f-116">Aby uzyskać więcej informacji na temat odszyfrowywania element XML, która została zaszyfrowana przy użyciu tej procedury, zobacz [porady: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="7248f-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="7248f-117">W tym przykładzie jest przydatne w sytuacjach, gdy wiele aplikacji potrzeba udostępnienia zaszyfrowanych danych lub gdy aplikacja musi zapisać zaszyfrowanych danych w okresie, które działa między.</span><span class="sxs-lookup"><span data-stu-id="7248f-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="7248f-118">Do szyfrowania z klucza asymetrycznego — element XML</span><span class="sxs-lookup"><span data-stu-id="7248f-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1.  <span data-ttu-id="7248f-119">Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="7248f-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="7248f-120">Generowanie klucza symetrycznego użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.</span><span class="sxs-lookup"><span data-stu-id="7248f-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="7248f-121">Klucz jest automatycznie zapisywane do kontenera kluczy podczas przekazywania <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.</span><span class="sxs-lookup"><span data-stu-id="7248f-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="7248f-122">Ten klucz będzie używany do szyfrowania klucza sesji AES i może zostać później pobrana do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7248f-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="7248f-123">Utwórz <xref:System.Xml.XmlDocument> obiektu przez ładowanie pliku XML z dysku.</span><span class="sxs-lookup"><span data-stu-id="7248f-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="7248f-124"><xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7248f-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="7248f-125">Znajdź element określony w <xref:System.Xml.XmlDocument> obiekt i utworzyć nową <xref:System.Xml.XmlElement> obiekt reprezentujący element, który chcesz zaszyfrować.</span><span class="sxs-lookup"><span data-stu-id="7248f-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="7248f-126">W tym przykładzie `"creditcard"` element jest zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="7248f-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="7248f-127">Tworzenie klucza nowej sesji przy użyciu <xref:System.Security.Cryptography.RijndaelManaged> klasy.</span><span class="sxs-lookup"><span data-stu-id="7248f-127">Create a new session key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="7248f-128">Ten klucz będą szyfrowania elementu XML i szyfrowane sam i umieszczone w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="7248f-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="7248f-129">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i jej użyciu można zaszyfrować określony element przy użyciu klucza sesji.</span><span class="sxs-lookup"><span data-stu-id="7248f-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="7248f-130"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda zwraca zaszyfrowany element jako tablicę bajtów zaszyfrowanych.</span><span class="sxs-lookup"><span data-stu-id="7248f-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="7248f-131">Utworzyć <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu i wypełnić ją identyfikator URL zaszyfrowany element XML.</span><span class="sxs-lookup"><span data-stu-id="7248f-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="7248f-132">Ten identyfikator URL umożliwia odszyfrowywania strona wiedzieć, że plik XML zawiera zaszyfrowany element.</span><span class="sxs-lookup"><span data-stu-id="7248f-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="7248f-133">Można użyć <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> Aby określić identyfikator adresu URL.</span><span class="sxs-lookup"><span data-stu-id="7248f-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="7248f-134">Element XML w postaci zwykłego tekstu zostaną zastąpione <`EncryptedData`> hermetyzowany to element <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7248f-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="7248f-135">Utwórz <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt, który jest inicjowana na adres URL identyfikator algorytmu kryptograficznego używanego do generowania klucza sesji.</span><span class="sxs-lookup"><span data-stu-id="7248f-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="7248f-136">Przekaż <xref:System.Security.Cryptography.Xml.EncryptionMethod> do obiektu <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7248f-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="7248f-137">Utwórz <xref:System.Security.Cryptography.Xml.EncryptedKey> będzie zawierał klucza szyfrowanej sesji.</span><span class="sxs-lookup"><span data-stu-id="7248f-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="7248f-138">Szyfrowanie klucza sesji, należy dodać go do <xref:System.Security.Cryptography.Xml.EncryptedKey> obiekt, a następnie wprowadź nazwę klucza sesji i adres URL identyfikatora klucza.</span><span class="sxs-lookup"><span data-stu-id="7248f-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="7248f-139">Utwórz nową <xref:System.Security.Cryptography.Xml.DataReference> obiekt, który mapuje zaszyfrowane dane z kluczem określonej sesji.</span><span class="sxs-lookup"><span data-stu-id="7248f-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="7248f-140">Ten opcjonalny krok pozwala łatwo określić, że wielu części dokumentu XML były szyfrowane przez jeden klucz.</span><span class="sxs-lookup"><span data-stu-id="7248f-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="7248f-141">Dodaj zaszyfrowany klucz do <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7248f-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="7248f-142">Utwórz nową <xref:System.Security.Cryptography.Xml.KeyInfo> obiektu do określenia nazwy kluczy RSA.</span><span class="sxs-lookup"><span data-stu-id="7248f-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="7248f-143">Dodaj go do <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7248f-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="7248f-144">Pomaga to strona odszyfrowywania zidentyfikować poprawne klucza asymetrycznego do użycia podczas odszyfrowywania klucza sesji.</span><span class="sxs-lookup"><span data-stu-id="7248f-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="7248f-145">Dodaj element zaszyfrowane dane do <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7248f-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="7248f-146">Zastąp element z oryginalnego <xref:System.Xml.XmlDocument> obiekt z <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.</span><span class="sxs-lookup"><span data-stu-id="7248f-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="7248f-147">Zapisz <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7248f-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="7248f-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="7248f-148">Example</span></span>  
 <span data-ttu-id="7248f-149">W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co program skompilowany.</span><span class="sxs-lookup"><span data-stu-id="7248f-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="7248f-150">Założono również, że `"test.xml"` zawiera `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="7248f-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="7248f-151">Następujący kod XML można umieścić w pliku o nazwie `test.xml` i użyć w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7248f-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7248f-152">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7248f-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="7248f-153">Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="7248f-153">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="7248f-154">Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="7248f-154">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7248f-155">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7248f-155">.NET Framework Security</span></span>  
 <span data-ttu-id="7248f-156">Nigdy nie przechowują symetrycznego klucza kryptograficznego w postaci zwykłego tekstu lub transfer klucza symetrycznego między komputerami w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="7248f-156">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="7248f-157">Ponadto nigdy nie magazynu lub przenieść klucz prywatny para kluczy asymetrycznych w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="7248f-157">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="7248f-158">Aby uzyskać więcej informacji na temat symetrycznego i asymetrycznego kluczy kryptograficznych, zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="7248f-158">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="7248f-159">Nigdy nie osadzaj klucza bezpośrednio w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="7248f-159">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="7248f-160">Osadzony kluczy można łatwo odczytać z zestawu za pomocą [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstu, takiego jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="7248f-160">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="7248f-161">Gdy wszystko będzie gotowe za pomocą klucza kryptograficznego, wyczyść go z pamięci przez ustawienie każdego bajtu na wartość zero lub wywoływania <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy kryptografii zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="7248f-161">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="7248f-162">Klucze kryptograficzne czasami może odczytywać pamięci przez debuger lub odczytu z dysku twardego, jeśli lokalizacji pamięci jest stronicowana na dysk.</span><span class="sxs-lookup"><span data-stu-id="7248f-162">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7248f-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7248f-163">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="7248f-164">Instrukcje: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych</span><span class="sxs-lookup"><span data-stu-id="7248f-164">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
