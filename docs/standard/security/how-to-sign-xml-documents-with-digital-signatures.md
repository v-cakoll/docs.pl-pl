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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 829be8663068d4eb492631ccc4194b4e4c3000aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590302"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>Porady: podpisywanie dokumentów XML za pomocą podpisów cyfrowych
Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw do podpisywania dokumentu XML lub części dokumentu XML podpisu cyfrowego.  Podpisy cyfrowe XML (XMLDSIG) pozwalają sprawdzić, czy dane nie została zmodyfikowana po podpisaniu.  Aby uzyskać więcej informacji na temat standardu XMLDSIG, zobacz zalecenia konsorcjum World Wide Web (W3C) [składnia XML podpisu i przetwarzania](https://www.w3.org/TR/xmldsig-core/).  
  
 Przykład kodu w tej procedurze pokazano, jak cyfrowe podpisywanie całego dokumentu XML i dołączyć podpis do dokumentu w <`Signature`> elementu.  Przykład tworzy klucza podpisywania RSA, dodaje klucz do bezpiecznego kontenera klucza, a następnie używa klucza podpisywania dokumentu XML.  Klucz można pobrać można zweryfikować podpisu cyfrowego XML lub może być używany do podpisywania innego dokumentu XML.  
  
 Aby uzyskać informacje dotyczące sposobu weryfikowania podpisu cyfrowego XML, który został utworzony przy użyciu tej procedury, zobacz [porady: Sprawdź podpisów cyfrowych z dokumentów XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).  
  
### <a name="to-digitally-sign-an-xml-document"></a>Do cyfrowego podpisywania dokumentu XML  
  
1.  Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera kluczy.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  Generowanie asymetrycznego klucza <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Klucz jest automatycznie zapisywane do kontenera kluczy podczas przekazywania <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Ten klucz będzie używany do podpisywania dokumentu XML.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  Utwórz <xref:System.Xml.XmlDocument> obiektu przez ładowanie pliku XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  Utwórz nową <xref:System.Security.Cryptography.Xml.SignedXml> obiektu i przekazać <xref:System.Xml.XmlDocument> obiektu do niego.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  Dodaj podpisywania kluczy RSA do <xref:System.Security.Cryptography.Xml.SignedXml> obiektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  Utwórz <xref:System.Security.Cryptography.Xml.Reference> obiekt, który opisano, co do podpisywania.  Aby zalogować się całego dokumentu, ustaw <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> właściwości `""`.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  Dodaj <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> do obiektu <xref:System.Security.Cryptography.Xml.Reference> obiektu.  Przekształcenie umożliwia weryfikatora do reprezentowania danych XML w taki sam sposób, że osoby podpisującej używane.  Dane XML można można przedstawić na różne sposoby, ten krok jest niezbędny do weryfikacji.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8.  Dodaj <xref:System.Security.Cryptography.Xml.Reference> do obiektu <xref:System.Security.Cryptography.Xml.SignedXml> obiektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. Obliczania podpisu przez wywołanie metody <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> metody.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. Pobrać reprezentacji XML podpisu (<`Signature`> elementu) i zapisz go na nowy <xref:System.Xml.XmlElement> obiektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. Element, aby dołączyć <xref:System.Xml.XmlDocument> obiektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. Zapisz dokument.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `test.xml` istnieje w tym samym katalogu co program skompilowany.  Następujący kod XML można umieścić w pliku o nazwie `test.xml` i użyć w tym przykładzie.  
  
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
  
-   Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.  
  
-   Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie magazynu lub przenieść klucz prywatny para kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat symetrycznego i asymetrycznego kluczy kryptograficznych, zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie osadzaj klucza prywatnego bezpośrednio w kodzie źródłowym.  Osadzony kluczy można łatwo odczytać z zestawu za pomocą [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstu, takiego jak Notatnik.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography.Xml>  
 [Instrukcje: sprawdzanie podpisów cyfrowych w dokumentach XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
