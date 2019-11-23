---
title: 'Porady: szyfrowanie elementów XML za pomocą certyfikatów X.509'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], X.509 certificates
- cryptography [.NET Framework], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d569d3c020e7329d987e957f181b34c8cfbf941a
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353863"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="823c6-102">Porady: szyfrowanie elementów XML za pomocą certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="823c6-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="823c6-103">Możesz użyć klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml>, aby zaszyfrować element w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="823c6-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="823c6-104">Szyfrowanie XML jest standardowym sposobem wymiany i przechowywania zaszyfrowanych danych XML bez obaw o dane, które są łatwo odczytywane.</span><span class="sxs-lookup"><span data-stu-id="823c6-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="823c6-105">Aby uzyskać więcej informacji na temat standardu szyfrowania XML, zobacz Specyfikacja organizacja World Wide Web Consortium (W3C) dla szyfrowania XML znajdującego się w <https://www.w3.org/TR/xmldsig-core/>.</span><span class="sxs-lookup"><span data-stu-id="823c6-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="823c6-106">Możesz użyć szyfrowania XML, aby zamienić dowolny element XML lub dokument z <`EncryptedData`> elementu, który zawiera zaszyfrowane dane XML.</span><span class="sxs-lookup"><span data-stu-id="823c6-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="823c6-107">Element <`EncryptedData`> może zawierać elementy podrzędne, które zawierają informacje o kluczach i procesach używanych podczas szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="823c6-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="823c6-108">Szyfrowanie XML pozwala dokument może zawierać wiele zaszyfrowanych elementów i umożliwia wielokrotne szyfrowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="823c6-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="823c6-109">Przykład kodu w tej procedurze pokazuje, jak utworzyć <`EncryptedData`> elementu wraz z kilkoma innymi elementami podrzędnymi, które można później użyć podczas odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="823c6-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="823c6-110">Ten przykład szyfruje element XML przy użyciu dwóch kluczy.</span><span class="sxs-lookup"><span data-stu-id="823c6-110">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="823c6-111">Generuje certyfikat testu X. 509 za pomocą narzędzia do [tworzenia certyfikatów (Makecert. exe)](/windows/desktop/SecCrypto/makecert) i zapisuje certyfikat w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="823c6-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) and saves the certificate to a certificate store.</span></span> <span data-ttu-id="823c6-112">Przykładowo program programowo pobiera certyfikat i używa go do szyfrowania elementu XML przy użyciu metody <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>.</span><span class="sxs-lookup"><span data-stu-id="823c6-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="823c6-113">Wewnętrznie metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> tworzy oddzielny klucz sesji i używa jej do szyfrowania dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="823c6-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="823c6-114">Ta metoda szyfruje klucz sesji i zapisuje go wraz z zaszyfrowanym kodem XML w ramach nowego <`EncryptedData`> elementu.</span><span class="sxs-lookup"><span data-stu-id="823c6-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="823c6-115">Aby odszyfrować element XML, po prostu wywołaj metodę <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>, która automatycznie pobiera certyfikat X. 509 ze sklepu i wykonuje wymagane odszyfrowywanie.</span><span class="sxs-lookup"><span data-stu-id="823c6-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="823c6-116">Aby uzyskać więcej informacji na temat odszyfrowywania elementu XML, który został zaszyfrowany przy użyciu tej procedury, zobacz [How to: Deszyfruj elementy XML za pomocą certyfikatów X. 509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="823c6-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="823c6-117">Ten przykład jest odpowiedni dla sytuacji, w których wiele aplikacji musi udostępniać zaszyfrowane dane lub w przypadku, gdy aplikacja wymaga zapisywania zaszyfrowanych danych między uruchomionymi danymi.</span><span class="sxs-lookup"><span data-stu-id="823c6-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="823c6-118">Aby zaszyfrować element XML z certyfikatem X.509</span><span class="sxs-lookup"><span data-stu-id="823c6-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="823c6-119">Użyj [Narzędzia do tworzenia certyfikatów (Makecert. exe)](/windows/desktop/SecCrypto/makecert) w celu wygenerowania testowego certyfikatu X. 509 i umieszczenie go w lokalnym magazynie użytkowników.</span><span class="sxs-lookup"><span data-stu-id="823c6-119">Use the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="823c6-120">Musisz wygenerować klucz wymiany i należy dokonać eksportu klucza.</span><span class="sxs-lookup"><span data-stu-id="823c6-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="823c6-121">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="823c6-121">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="823c6-122">Utwórz obiekt <xref:System.Security.Cryptography.X509Certificates.X509Store> i zainicjuj go, aby otworzyć bieżący magazyn użytkowników.</span><span class="sxs-lookup"><span data-stu-id="823c6-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="823c6-123">Otwórz sklep w trybie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="823c6-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="823c6-124">Zainicjuj <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> ze wszystkimi certyfikatami w sklepie.</span><span class="sxs-lookup"><span data-stu-id="823c6-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="823c6-125">Wylicz certyfikaty w magazynie i Znajdź certyfikat z odpowiednią nazwą.</span><span class="sxs-lookup"><span data-stu-id="823c6-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="823c6-126">W tym przykładzie certyfikat nosi nazwę `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="823c6-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="823c6-127">Zamknij sklep po zlokalizowaniu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="823c6-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="823c6-128">Utwórz obiekt <xref:System.Xml.XmlDocument>, ładując plik XML z dysku.</span><span class="sxs-lookup"><span data-stu-id="823c6-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="823c6-129">Obiekt <xref:System.Xml.XmlDocument> zawiera element XML do zaszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="823c6-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="823c6-130">Znajdź określony element w obiekcie <xref:System.Xml.XmlDocument> i Utwórz nowy obiekt <xref:System.Xml.XmlElement> do reprezentowania elementu, który chcesz zaszyfrować.</span><span class="sxs-lookup"><span data-stu-id="823c6-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="823c6-131">W tym przykładzie element `"creditcard"` jest szyfrowany.</span><span class="sxs-lookup"><span data-stu-id="823c6-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="823c6-132">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> i użyj go do szyfrowania określonego elementu przy użyciu certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="823c6-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="823c6-133">Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> zwraca zaszyfrowany element jako obiekt <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="823c6-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="823c6-134">Zastąp element z oryginalnego obiektu <xref:System.Xml.XmlDocument> elementem <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="823c6-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="823c6-135">Zapisz <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="823c6-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="823c6-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="823c6-136">Example</span></span>  
 <span data-ttu-id="823c6-137">W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowany program.</span><span class="sxs-lookup"><span data-stu-id="823c6-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="823c6-138">Zakłada również, że `"test.xml"` zawiera `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="823c6-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="823c6-139">Można umieścić następujący kod XML w pliku o nazwie `test.xml` i użyć go w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="823c6-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="823c6-140">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="823c6-140">Compiling the Code</span></span>  
  
- <span data-ttu-id="823c6-141">Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="823c6-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="823c6-142">Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="823c6-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="823c6-143">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="823c6-143">.NET Framework Security</span></span>  
 <span data-ttu-id="823c6-144">Certyfikat X. 509 użyty w tym przykładzie służy tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="823c6-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="823c6-145">Aplikacje powinny używać certyfikatu X. 509 wygenerowanego przez zaufany urząd certyfikacji lub użyć certyfikatu wygenerowanego przez serwer certyfikatów systemu Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="823c6-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="823c6-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="823c6-146">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="823c6-147">Instrukcje: odszyfrowywanie elementów XML za pomocą certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="823c6-147">How to: Decrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
