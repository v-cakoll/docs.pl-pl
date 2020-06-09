---
title: 'Porady: podpisywanie dokumentów XML za pomocą podpisów cyfrowych'
description: Dowiedz się, jak podpisywać dokumenty XML za pomocą podpisów cyfrowych. Użyj klas w przestrzeni nazw System. Security. Cryptography. XML w programie .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: 97bd23182ed54b899b76dbf43e179fe0c94b011d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598570"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="2420a-104">Porady: podpisywanie dokumentów XML za pomocą podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="2420a-104">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="2420a-105">Możesz użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby podpisać dokument XML lub część dokumentu XML z podpisem cyfrowym.</span><span class="sxs-lookup"><span data-stu-id="2420a-105">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="2420a-106">Podpisy cyfrowe XML (XMLDSIG) pozwalają sprawdzić, czy dane nie zostały zmienione po podpisaniu.</span><span class="sxs-lookup"><span data-stu-id="2420a-106">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="2420a-107">Aby uzyskać więcej informacji na temat standardu XMLDSIG, zobacz [składnia i przetwarzanie w formacie XML](https://www.w3.org/TR/xmldsig-core/)zalecenia dotyczące organizacja World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="2420a-107">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="2420a-108">Przykład kodu w tej procedurze pokazuje, jak cyfrowo podpisać cały dokument XML i dołączyć podpis do dokumentu w <`Signature`> elementu.</span><span class="sxs-lookup"><span data-stu-id="2420a-108">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="2420a-109">Przykład tworzy klucz podpisywania RSA, dodaje klucz do kontenera klucza zabezpieczeń, a następnie używa klucza do cyfrowego podpisywania dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2420a-109">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="2420a-110">Następnie można pobrać klucz w celu zweryfikowania podpisu cyfrowego XML lub można go użyć do podpisania innego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2420a-110">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="2420a-111">Aby uzyskać informacje na temat weryfikowania podpisu cyfrowego XML, który został utworzony przy użyciu tej procedury, zobacz [How to: Verify Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="2420a-111">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="2420a-112">Aby podpisać cyfrowo dokument XML</span><span class="sxs-lookup"><span data-stu-id="2420a-112">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="2420a-113">Utwórz <xref:System.Security.Cryptography.CspParameters> obiekt i określ nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="2420a-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="2420a-114">Generuj klucz asymetryczny przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.</span><span class="sxs-lookup"><span data-stu-id="2420a-114">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="2420a-115">Klucz jest automatycznie zapisywany do kontenera kluczy podczas przekazywania <xref:System.Security.Cryptography.CspParameters> obiektu do konstruktora <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.</span><span class="sxs-lookup"><span data-stu-id="2420a-115">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="2420a-116">Ten klucz będzie używany do podpisywania dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2420a-116">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="2420a-117">Utwórz <xref:System.Xml.XmlDocument> obiekt przez załadowanie pliku XML z dysku.</span><span class="sxs-lookup"><span data-stu-id="2420a-117">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="2420a-118"><xref:System.Xml.XmlDocument>Obiekt zawiera element XML do zaszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="2420a-118">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="2420a-119">Utwórz nowy <xref:System.Security.Cryptography.Xml.SignedXml> obiekt i przekaż <xref:System.Xml.XmlDocument> do niego obiekt.</span><span class="sxs-lookup"><span data-stu-id="2420a-119">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="2420a-120">Dodaj podpis klucza RSA do <xref:System.Security.Cryptography.Xml.SignedXml> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2420a-120">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="2420a-121">Utwórz obiekt opisujący <xref:System.Security.Cryptography.Xml.Reference> elementy do podpisania.</span><span class="sxs-lookup"><span data-stu-id="2420a-121">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="2420a-122">Aby podpisać cały dokument, należy ustawić <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> Właściwość na `""` .</span><span class="sxs-lookup"><span data-stu-id="2420a-122">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="2420a-123">Dodaj <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> obiekt do <xref:System.Security.Cryptography.Xml.Reference> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2420a-123">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="2420a-124">Przekształcenie umożliwia weryfikatorowi reprezentowania danych XML w taki sam sposób, w jaki użyto osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="2420a-124">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="2420a-125">Dane XML mogą być reprezentowane na różne sposoby, więc ten krok jest niezbędny do weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="2420a-125">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="2420a-126">Dodaj <xref:System.Security.Cryptography.Xml.Reference> obiekt do <xref:System.Security.Cryptography.Xml.SignedXml> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2420a-126">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="2420a-127">Oblicz podpis, wywołując <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="2420a-127">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="2420a-128">Pobierz reprezentację XML sygnatury (<`Signature` elementu>) i Zapisz ją w nowym <xref:System.Xml.XmlElement> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="2420a-128">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="2420a-129">Dołącz element do <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2420a-129">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="2420a-130">Zapisz dokument.</span><span class="sxs-lookup"><span data-stu-id="2420a-130">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="2420a-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="2420a-131">Example</span></span>  
 <span data-ttu-id="2420a-132">W tym przykładzie przyjęto założenie, że plik o nazwie `test.xml` istnieje w tym samym katalogu co skompilowany program.</span><span class="sxs-lookup"><span data-stu-id="2420a-132">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="2420a-133">Można umieścić następujący kod XML w pliku o nazwie `test.xml` i użyć go w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2420a-133">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2420a-134">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2420a-134">Compiling the Code</span></span>  
  
- <span data-ttu-id="2420a-135">Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="2420a-135">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="2420a-136">Uwzględnij następujące przestrzenie nazw: <xref:System.Xml> , <xref:System.Security.Cryptography> , i <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="2420a-136">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2420a-137">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2420a-137">.NET Framework Security</span></span>  
 <span data-ttu-id="2420a-138">Nigdy nie przechowuj ani nie przesyłaj klucza prywatnego pary kluczy asymetrycznych w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="2420a-138">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="2420a-139">Aby uzyskać więcej informacji na temat symetrycznych i asymetrycznych kluczy kryptograficznych, zobacz [generowanie kluczy do szyfrowania i odszyfrowywania](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="2420a-139">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="2420a-140">Nie osadzaj klucza prywatnego bezpośrednio w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="2420a-140">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="2420a-141">Klucze osadzone można łatwo odczytywać z zestawu przy użyciu [Ildasm. exe (Il dezasembler)](../../framework/tools/ildasm-exe-il-disassembler.md) lub otwierając zestaw w edytorze tekstu, takim jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="2420a-141">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2420a-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2420a-142">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="2420a-143">Instrukcje: sprawdzanie podpisów cyfrowych w dokumentach XML</span><span class="sxs-lookup"><span data-stu-id="2420a-143">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
