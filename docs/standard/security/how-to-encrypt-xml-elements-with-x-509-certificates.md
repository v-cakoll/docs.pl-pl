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
ms.openlocfilehash: 674a4c917df20f58a509e92465e756c4615118ca
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45969918"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="7d1fc-102">Porady: szyfrowanie elementów XML za pomocą certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="7d1fc-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="7d1fc-103">Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="7d1fc-104">Szyfrowanie XML to standardowy sposób wymiany ani nie przechowują zaszyfrowane dane XML, nie martwiąc się o łatwo odczytywanych danych.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="7d1fc-105">Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz specyfikację World Wide Web Consortium (W3C) dla szyfrowanie XML znajdujący się w http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="7d1fc-106">Szyfrowanie XML umożliwia zastąpienie dowolnego elementu XML lub dokumentów za pomocą <`EncryptedData`> element, który zawiera zaszyfrowane dane XML.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="7d1fc-107"><`EncryptedData`> Element może zawierać elementy podrzędne, które zawierają informacje o kluczach i procesem stosowanym podczas szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="7d1fc-108">Szyfrowanie XML umożliwia dokumentu zawiera wiele elementów zaszyfrowanych i umożliwia elementu do zaszyfrowania wiele razy.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="7d1fc-109">Przykład kodu w tej procedurze przedstawiono sposób tworzenia <`EncryptedData`> element wraz z kilku elementów podrzędnych, w które można użyć później, podczas odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="7d1fc-110">W tym przykładzie szyfruje elementu XML za pomocą dwóch kluczy.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="7d1fc-111">Generuje testu X.509 certyfikatu za pomocą [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) i zapisuje certyfikat do magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) and saves the certificate to a certificate store.</span></span>  <span data-ttu-id="7d1fc-112">Przykład następnie programowo pobiera certyfikat i używa go do zaszyfrowania — element XML przy użyciu <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span>  <span data-ttu-id="7d1fc-113">Wewnętrznie <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metoda tworzy klucz oddzielną sesję i używa go do zaszyfrowania dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="7d1fc-114">Ta metoda szyfruje klucz sesji i zapisuje go wraz z zaszyfrowanego pliku XML, w ramach nowego <`EncryptedData`> element.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="7d1fc-115">Aby odszyfrować XML element, wystarczy wywołać <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody, która automatycznie pobiera certyfikat X.509 z magazynu i wykonuje niezbędne odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="7d1fc-116">Aby uzyskać więcej informacji na temat odszyfrować element XML, która została zaszyfrowana przy użyciu tej procedury, zobacz [porady: odszyfrowywanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7d1fc-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="7d1fc-117">W tym przykładzie jest odpowiednie w sytuacji, gdy wiele aplikacji muszą udostępniać dane zaszyfrowane lub której aplikacja musi zapisać zaszyfrowane dane między godzinami, które działa.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="7d1fc-118">Aby zaszyfrować element XML z certyfikatem X.509</span><span class="sxs-lookup"><span data-stu-id="7d1fc-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="7d1fc-119">Użyj [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) do generowania certyfikatu X.509 testu i umieść go w magazynie użytkownika lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-119">Use the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) to generate a test X.509 certificate and place it in the local user store.</span></span>  <span data-ttu-id="7d1fc-120">Należy wygenerować klucz wymiany, i należy klucz możliwy do eksportu.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="7d1fc-121">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="7d1fc-121">Run the following command:</span></span>  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  <span data-ttu-id="7d1fc-122">Utwórz <xref:System.Security.Cryptography.X509Certificates.X509Store> obiektu i zainicjuj ją, aby otworzyć magazynie bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  <span data-ttu-id="7d1fc-123">Otwórz Sklep w trybie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  <span data-ttu-id="7d1fc-124">Inicjowanie <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> wszystkie certyfikaty w magazynie.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  <span data-ttu-id="7d1fc-125">Wyliczanie przy użyciu certyfikatów w magazynie i znaleźć certyfikatu z odpowiednią nazwę.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="7d1fc-126">W tym przykładzie nosi nazwę certyfikatu `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  <span data-ttu-id="7d1fc-127">Po znajduje się certyfikat, należy zamknąć magazynu.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  <span data-ttu-id="7d1fc-128">Utwórz <xref:System.Xml.XmlDocument> obiektu, ładując plik XML z dysku.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="7d1fc-129"><xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  <span data-ttu-id="7d1fc-130">Znajdź element określony w <xref:System.Xml.XmlDocument> obiektu i Utwórz nowy <xref:System.Xml.XmlElement> obiekt reprezentujący element, który chcesz zaszyfrować.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="7d1fc-131">W tym przykładzie `"creditcard"` elementu są szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="7d1fc-132">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i jej użyciu można zaszyfrować określony element przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="7d1fc-133"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda zwraca element zaszyfrowany jako <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="7d1fc-134">Zastąp element z oryginalnym <xref:System.Xml.XmlDocument> obiekt z <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="7d1fc-135">Zapisz <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="7d1fc-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d1fc-136">Example</span></span>  
 <span data-ttu-id="7d1fc-137">W tym przykładzie założono, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowanego programu.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="7d1fc-138">Przyjęto również założenie, że `"test.xml"` zawiera `"creditcard"` elementu.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="7d1fc-139">Następujący kod XML może umieścić w pliku o nazwie `test.xml` i użycie go w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d1fc-140">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7d1fc-140">Compiling the Code</span></span>  
  
-   <span data-ttu-id="7d1fc-141">Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="7d1fc-142">Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7d1fc-143">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7d1fc-143">.NET Framework Security</span></span>  
 <span data-ttu-id="7d1fc-144">Certyfikat X.509 używany w tym przykładzie jest tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="7d1fc-145">Aplikacje, należy użyć certyfikatu X.509, który jest generowany przez zaufany urząd certyfikacji lub użycia certyfikatu wygenerowanego przez program Microsoft Windows Certificate Server.</span><span class="sxs-lookup"><span data-stu-id="7d1fc-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1fc-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d1fc-146">See also</span></span>

- <xref:System.Security.Cryptography.Xml>  
- [<span data-ttu-id="7d1fc-147">Instrukcje: odszyfrowywanie elementów XML za pomocą certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="7d1fc-147">How to: Decrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
