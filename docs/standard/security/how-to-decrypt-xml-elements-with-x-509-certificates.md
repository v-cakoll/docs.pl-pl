---
title: 'Porady: odszyfrowywanie elementów XML za pomocą certyfikatów X.509'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
ms.openlocfilehash: 46fbefbf7a427ec0d60a34ecc2166f8499d08575
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708891"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="4f344-102">Porady: odszyfrowywanie elementów XML za pomocą certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="4f344-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="4f344-103">Można użyć klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml> do szyfrowania i odszyfrowywania elementu w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="4f344-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="4f344-104">Szyfrowanie XML jest standardowym sposobem wymiany i przechowywania zaszyfrowanych danych XML bez obaw o dane, które są łatwo odczytywane.</span><span class="sxs-lookup"><span data-stu-id="4f344-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="4f344-105">Aby uzyskać więcej informacji na temat standardu szyfrowania XML, zobacz Specyfikacja organizacja World Wide Web Consortium (W3C) dla szyfrowania XML znajdującego się w <https://www.w3.org/TR/xmldsig-core/>.</span><span class="sxs-lookup"><span data-stu-id="4f344-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="4f344-106">Ten przykład odszyfrowuje element XML, który został zaszyfrowany przy użyciu metod opisanych w: [jak szyfrować elementy XML za pomocą certyfikatów X. 509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4f344-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="4f344-107">Znajduje <`EncryptedData`> elementu, odszyfrowuje element, a następnie zamienia element na oryginalny element XML w formacie zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="4f344-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="4f344-108">Przykład kodu w tej procedurze odszyfrowuje element XML przy użyciu certyfikatu X. 509 z lokalnego magazynu certyfikatów bieżącego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4f344-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="4f344-109">W przykładzie zastosowano metodę <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>, aby automatycznie pobrać certyfikat X. 509 i odszyfrować klucz sesji przechowywany w elemencie <`EncryptedKey`> elementu <`EncryptedData`>.</span><span class="sxs-lookup"><span data-stu-id="4f344-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="4f344-110">Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> następnie automatycznie używa klucza sesji do odszyfrowania elementu XML.</span><span class="sxs-lookup"><span data-stu-id="4f344-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="4f344-111">Ten przykład jest odpowiedni dla sytuacji, w których wiele aplikacji musi udostępniać zaszyfrowane dane lub w przypadku, gdy aplikacja wymaga zapisywania zaszyfrowanych danych między uruchomionymi danymi.</span><span class="sxs-lookup"><span data-stu-id="4f344-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="4f344-112">Aby odszyfrować element XML z certyfikatem X.509</span><span class="sxs-lookup"><span data-stu-id="4f344-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="4f344-113">Utwórz obiekt <xref:System.Xml.XmlDocument>, ładując plik XML z dysku.</span><span class="sxs-lookup"><span data-stu-id="4f344-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="4f344-114">Obiekt <xref:System.Xml.XmlDocument> zawiera element XML do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="4f344-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <span data-ttu-id="4f344-115">Utwórz nowy obiekt <xref:System.Security.Cryptography.Xml.EncryptedXml>, przekazując obiekt <xref:System.Xml.XmlDocument> do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="4f344-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. <span data-ttu-id="4f344-116">Odszyfruj dokument XML przy użyciu metody <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f344-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. <span data-ttu-id="4f344-117">Zapisz <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4f344-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="4f344-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f344-118">Example</span></span>  
 <span data-ttu-id="4f344-119">W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowany program.</span><span class="sxs-lookup"><span data-stu-id="4f344-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="4f344-120">Zakłada również, że `"test.xml"` zawiera `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="4f344-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="4f344-121">Można umieścić następujący kod XML w pliku o nazwie `test.xml` i użyć go w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4f344-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f344-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4f344-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="4f344-123">Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="4f344-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="4f344-124">Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="4f344-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4f344-125">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4f344-125">.NET Framework Security</span></span>  
 <span data-ttu-id="4f344-126">Certyfikat X. 509 użyty w tym przykładzie służy tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="4f344-126">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="4f344-127">Aplikacje powinny używać certyfikatu X. 509 wygenerowanego przez zaufany urząd certyfikacji lub użyć certyfikatu wygenerowanego przez serwer certyfikatów systemu Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="4f344-127">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f344-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f344-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="4f344-129">Instrukcje: szyfrowanie elementów XML za pomocą certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="4f344-129">How to: Encrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
