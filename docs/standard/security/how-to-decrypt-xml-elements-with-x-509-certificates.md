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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0064aaf2e67eb3fb40e4c58995ce8678321d21aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583334"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="ac87b-102">Porady: odszyfrowywanie elementów XML za pomocą certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="ac87b-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="ac87b-103">Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw do szyfrowania i odszyfrowywania element w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="ac87b-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="ac87b-104">Szyfrowanie XML jest standardowym sposobem exchange lub przechowywania zaszyfrowanych danych XML, nie martwiąc się o łatwo odczytywane dane.</span><span class="sxs-lookup"><span data-stu-id="ac87b-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="ac87b-105">Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz specyfikację sieci World Wide Web konsorcjum W3C szyfrowanie XML zlokalizowanej w http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="ac87b-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="ac87b-106">W tym przykładzie odszyfrowuje element XML, która została zaszyfrowana przy użyciu metod opisanych w: [porady: szyfrowanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ac87b-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="ac87b-107">Znajdzie <`EncryptedData`> elementu odszyfrowuje elementu, a następnie zastępuje element oryginalny element XML w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="ac87b-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="ac87b-108">Przykład kodu w tej procedurze odszyfrowuje elementu XML za pomocą certyfikatu X.509 z lokalnego magazynu certyfikatów bieżącego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ac87b-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="ac87b-109">W przykładzie użyto <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodę, aby automatycznie pobrać certyfikatu X.509 i odszyfrować klucza przechowywanego w sesji <`EncryptedKey`> elementu <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="ac87b-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="ac87b-110"><xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> Metoda następnie automatycznie używa klucza sesji do odszyfrowania elementu XML.</span><span class="sxs-lookup"><span data-stu-id="ac87b-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="ac87b-111">W tym przykładzie jest przydatne w sytuacjach, gdy wiele aplikacji potrzeba udostępnienia zaszyfrowanych danych lub gdy aplikacja musi zapisać zaszyfrowanych danych w okresie, które działa między.</span><span class="sxs-lookup"><span data-stu-id="ac87b-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="ac87b-112">Aby odszyfrować element XML z certyfikatem X.509</span><span class="sxs-lookup"><span data-stu-id="ac87b-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="ac87b-113">Utwórz <xref:System.Xml.XmlDocument> obiektu przez ładowanie pliku XML z dysku.</span><span class="sxs-lookup"><span data-stu-id="ac87b-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="ac87b-114"><xref:System.Xml.XmlDocument> Obiekt zawiera element XML do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="ac87b-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="ac87b-115">Utwórz nową <xref:System.Security.Cryptography.Xml.EncryptedXml> obiektu przez przekazywanie <xref:System.Xml.XmlDocument> obiekt do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ac87b-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="ac87b-116">Odszyfrować za pomocą dokumentu XML <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ac87b-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="ac87b-117">Zapisz <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ac87b-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ac87b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac87b-118">Example</span></span>  
 <span data-ttu-id="ac87b-119">W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co program skompilowany.</span><span class="sxs-lookup"><span data-stu-id="ac87b-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="ac87b-120">Założono również, że `"test.xml"` zawiera `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="ac87b-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="ac87b-121">Następujący kod XML można umieścić w pliku o nazwie `test.xml` i użyć w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ac87b-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac87b-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ac87b-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ac87b-123">Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="ac87b-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="ac87b-124">Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="ac87b-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ac87b-125">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ac87b-125">.NET Framework Security</span></span>  
 <span data-ttu-id="ac87b-126">Certyfikat X.509 używany w tym przykładzie jest tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="ac87b-126">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="ac87b-127">Aplikacje należy użyć certyfikatu X.509 generowane przez zaufany urząd certyfikacji lub Użyj certyfikatu wygenerowanego przez serwer Microsoft Windows certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ac87b-127">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac87b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac87b-128">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="ac87b-129">Instrukcje: szyfrowanie elementów XML za pomocą certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="ac87b-129">How to: Encrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
