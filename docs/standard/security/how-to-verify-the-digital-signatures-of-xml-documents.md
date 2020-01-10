---
title: 'Porady: sprawdzanie podpisów cyfrowych w dokumentach XML'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: 5d562c23d3b0fd7eda5dc273932ada77709641a1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706009"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Porady: sprawdzanie podpisów cyfrowych w dokumentach XML
Możesz użyć klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml>, aby zweryfikować dane XML podpisane przy użyciu podpisu cyfrowego. Podpisy cyfrowe XML (XMLDSIG) pozwalają sprawdzić, czy dane nie zostały zmienione po podpisaniu. Aby uzyskać więcej informacji na temat standardu XMLDSIG, zobacz specyfikację organizacja World Wide Web Consortium (W3C) w <https://www.w3.org/TR/xmldsig-core/>.
  
 W przykładzie kodu w tej procedurze pokazano, jak sprawdzić podpis cyfrowy XML zawarty w <`Signature`> elementu.  Przykład pobiera klucz publiczny RSA z kontenera kluczy, a następnie używa klucza do zweryfikowania podpisu.  
  
 Aby uzyskać informacje na temat tworzenia podpisu cyfrowego, który można zweryfikować przy użyciu tej metody, zobacz [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Aby sprawdzić podpis cyfrowy dokumentu XML  
  
1. Aby sprawdzić dokument, należy użyć tego samego klucza asymetrycznego, który został użyty do podpisywania.  Utwórz obiekt <xref:System.Security.Cryptography.CspParameters> i określ nazwę kontenera kluczy, który został użyty do podpisywania.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Pobierz klucz publiczny za pomocą klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Klucz jest ładowany automatycznie z kontenera kluczy według nazwy podczas przekazywania obiektu <xref:System.Security.Cryptography.CspParameters> do konstruktora klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Utwórz obiekt <xref:System.Xml.XmlDocument>, ładując plik XML z dysku.  Obiekt <xref:System.Xml.XmlDocument> zawiera podpisany dokument XML do zweryfikowania.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Utwórz nowy obiekt <xref:System.Security.Cryptography.Xml.SignedXml> i Przekaż do niego obiekt <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. Znajdź <`signature`> elementu i Utwórz nowy obiekt <xref:System.Xml.XmlNodeList>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Załaduj plik XML pierwszego <`signature`> elementu do obiektu <xref:System.Security.Cryptography.Xml.SignedXml>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Sprawdź podpis przy użyciu metody <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> i klucza publicznego RSA.  Ta metoda zwraca wartość logiczną wskazującą powodzenie lub niepowodzenie.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowany program.  Plik `"test.xml"` musi być podpisany przy użyciu technik opisanych w [instrukcje: podpisywanie dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
- Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Nigdy nie przechowuj ani nie przesyłaj klucza prywatnego pary kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat symetrycznych i asymetrycznych kluczy kryptograficznych, zobacz [generowanie kluczy do szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nie osadzaj klucza prywatnego bezpośrednio w kodzie źródłowym.  Klucze osadzone można łatwo odczytywać z zestawu przy użyciu [Ildasm. exe (Il dezasembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub otwierając zestaw w edytorze tekstu, takim jak Notatnik.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: podpisywanie dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
