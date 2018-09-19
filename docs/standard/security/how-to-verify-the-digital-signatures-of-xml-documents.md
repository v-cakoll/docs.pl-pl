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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ec813e50bb4dca33c8dda8b41914cfa5d5596c2
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006408"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Porady: sprawdzanie podpisów cyfrowych w dokumentach XML
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeń nazw w celu weryfikacji danych XML podpisany przy użyciu podpisu cyfrowego.  Podpisy cyfrowe XML (XMLDSIG) pozwalają zweryfikować, że dane nie została zmodyfikowana po podpisaniu.  Aby uzyskać więcej informacji na temat standardowych XMLDSIG, zobacz specyfikację World Wide Web Consortium (W3C) na http://www.w3.org/TR/xmldsig-core/.  
  
 Przykład kodu w tej procedurze pokazano, jak sprawdzić podpis cyfrowy XML zawartych w <`Signature`> element.  Przykład pobiera klucz publiczny RSA z kontenera kluczy, a następnie używa klucza można zweryfikować podpisu.  
  
 Aby uzyskać informacje o tym, jak utworzyć podpis cyfrowy, który może zostać zweryfikowany przy użyciu tej metody, zobacz [jak: logowanie dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Aby sprawdzić podpis cyfrowy dokumentu XML  
  
1.  Aby sprawdzić, czy dokument, należy użyć tego samego klucza asymetrycznego, który został użyty do podpisania.  Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera kluczy, który został użyty do podpisania.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  Pobieranie klucza publicznego przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Klucz jest automatycznie ładowany z kontenera kluczy według nazwy podczas przekazywania <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  Utwórz <xref:System.Xml.XmlDocument> obiektu, ładując plik XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera podpisanych dokumentu XML, aby sprawdzić.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  Utwórz nową <xref:System.Security.Cryptography.Xml.SignedXml> i przekazać <xref:System.Xml.XmlDocument> obiektu do niego.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  Znajdź <`signature`> element i Utwórz nowy <xref:System.Xml.XmlNodeList> obiektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  Ładowanie kodu XML pierwszego <`signature`> elementu do <xref:System.Security.Cryptography.Xml.SignedXml> obiektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  Sprawdzić przy użyciu podpisu <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> metody i klucz publiczny RSA.  Ta metoda zwraca wartość logiczną, która wskazuje powodzenie lub niepowodzenie.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie założono, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowanego programu.  `"test.xml"` Plik musi być podpisany za pomocą metod opisanych w [jak: logowanie dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
-   Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie magazynu lub transfer klucza prywatnego pary kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat klucze szyfrowania symetrycznego i asymetrycznego zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie można osadzić klucza prywatnego bezpośrednio w kodzie źródłowym.  Osadzone klucze można łatwo odczytać z zestawu przy użyciu [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstów, takiego jak Notatnik.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>  
- [Instrukcje: podpisywanie dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
