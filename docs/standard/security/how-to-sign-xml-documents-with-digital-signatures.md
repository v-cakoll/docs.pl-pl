---
title: 'Porady: podpisywanie dokumentów XML za pomocą podpisów cyfrowych'
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
ms.openlocfilehash: 0df036b3336527f3cc0e48d9a7ec835ab9f1cf4a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706048"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>Porady: podpisywanie dokumentów XML za pomocą podpisów cyfrowych
Za pomocą klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml> można podpisać dokument XML lub część dokumentu XML przy użyciu podpisu cyfrowego.  Podpisy cyfrowe XML (XMLDSIG) pozwalają sprawdzić, czy dane nie zostały zmienione po podpisaniu.  Aby uzyskać więcej informacji na temat standardu XMLDSIG, zobacz [składnia i przetwarzanie w formacie XML](https://www.w3.org/TR/xmldsig-core/)zalecenia dotyczące organizacja World Wide Web Consortium (W3C).  
  
 W przykładzie kodu w tej procedurze pokazano, jak cyfrowo podpisać cały dokument XML i dołączyć podpis do dokumentu w <`Signature`> elementu.  Przykład tworzy klucz podpisywania RSA, dodaje klucz do kontenera klucza zabezpieczeń, a następnie używa klucza do cyfrowego podpisywania dokumentu XML.  Następnie można pobrać klucz w celu zweryfikowania podpisu cyfrowego XML lub można go użyć do podpisania innego dokumentu XML.  
  
 Aby uzyskać informacje na temat weryfikowania podpisu cyfrowego XML, który został utworzony przy użyciu tej procedury, zobacz [How to: Verify Digital Signatures of XML Documents](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).  
  
### <a name="to-digitally-sign-an-xml-document"></a>Aby podpisać cyfrowo dokument XML  
  
1. Utwórz obiekt <xref:System.Security.Cryptography.CspParameters> i określ nazwę kontenera kluczy.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Generuj klucz asymetryczny przy użyciu klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Klucz jest automatycznie zapisywany w kontenerze kluczy podczas przekazywania obiektu <xref:System.Security.Cryptography.CspParameters> do konstruktora klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Ten klucz będzie używany do podpisywania dokumentu XML.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Utwórz obiekt <xref:System.Xml.XmlDocument>, ładując plik XML z dysku.  Obiekt <xref:System.Xml.XmlDocument> zawiera element XML do zaszyfrowania.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Utwórz nowy obiekt <xref:System.Security.Cryptography.Xml.SignedXml> i Przekaż do niego obiekt <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. Dodaj podpis klucza RSA do obiektu <xref:System.Security.Cryptography.Xml.SignedXml>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Utwórz obiekt <xref:System.Security.Cryptography.Xml.Reference>, który opisuje znaczenie do podpisania.  Aby podpisać cały dokument, ustaw właściwość <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> na `""`.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Dodaj obiekt <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> do obiektu <xref:System.Security.Cryptography.Xml.Reference>.  Przekształcenie umożliwia weryfikatorowi reprezentowania danych XML w taki sam sposób, w jaki użyto osoby podpisującej.  Dane XML mogą być reprezentowane na różne sposoby, więc ten krok jest niezbędny do weryfikacji.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. Dodaj obiekt <xref:System.Security.Cryptography.Xml.Reference> do obiektu <xref:System.Security.Cryptography.Xml.SignedXml>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. Oblicz podpis, wywołując metodę <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. Pobierz reprezentację XML sygnatury (<`Signature`> element) i Zapisz ją w nowym obiekcie <xref:System.Xml.XmlElement>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. Dołącz element do obiektu <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. Zapisz dokument.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `test.xml` istnieje w tym samym katalogu co skompilowany program.  Można umieścić następujący kod XML w pliku o nazwie `test.xml` i użyć go w tym przykładzie.  
  
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
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
- Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Nigdy nie przechowuj ani nie przesyłaj klucza prywatnego pary kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat symetrycznych i asymetrycznych kluczy kryptograficznych, zobacz [generowanie kluczy do szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nie osadzaj klucza prywatnego bezpośrednio w kodzie źródłowym.  Klucze osadzone można łatwo odczytywać z zestawu przy użyciu [Ildasm. exe (Il dezasembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub otwierając zestaw w edytorze tekstu, takim jak Notatnik.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: sprawdzanie podpisów cyfrowych w dokumentach XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
