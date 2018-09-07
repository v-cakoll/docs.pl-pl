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
ms.openlocfilehash: 361dfd8cc9264f86bfc94a150635d9891274c9ac
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061679"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>Porady: podpisywanie dokumentów XML za pomocą podpisów cyfrowych
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby podpisać dokument XML lub części dokumentu XML przy użyciu podpisu cyfrowego.  Podpisy cyfrowe XML (XMLDSIG) pozwalają zweryfikować, że dane nie została zmodyfikowana po podpisaniu.  Aby uzyskać więcej informacji na temat standardowych XMLDSIG zobacz zalecenia konsorcjum World Wide Web Consortium (W3C) [składni podpisu XML i przetwarzanie](https://www.w3.org/TR/xmldsig-core/).  
  
 Przykład kodu w tej procedurze pokazano, jak cyfrowe podpisywanie całego dokumentu XML i Dołącz podpis do dokumentu w <`Signature`> element.  Przykład tworzy klucz podpisywania RSA, dodaje klucz do bezpiecznego kontenera kluczy, a następnie używa klucza do cyfrowego podpisywania dokumentu XML.  Klucz można pobrać można zweryfikować podpisu cyfrowego XML lub może być używany do podpisywania innego dokumentu XML.  
  
 Aby dowiedzieć się, jak sprawdzić podpis cyfrowy XML, który został utworzony przy użyciu tej procedury, zobacz [jak: Sprawdź podpisów cyfrowych z dokumentów XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).  
  
### <a name="to-digitally-sign-an-xml-document"></a>Aby cyfrowo podpisać dokument XML  
  
1.  Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera kluczy.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  Generowanie asymetrycznego klucza <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Klucz są automatycznie zapisywane w kontenerze kluczy, jeśli przekazujesz <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Ten klucz będzie używany do podpisywania dokumentów XML.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  Utwórz <xref:System.Xml.XmlDocument> obiektu, ładując plik XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  Utwórz nową <xref:System.Security.Cryptography.Xml.SignedXml> i przekazać <xref:System.Xml.XmlDocument> obiektu do niego.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  Dodaj klucz RSA podpisywania, który <xref:System.Security.Cryptography.Xml.SignedXml> obiektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  Utwórz <xref:System.Security.Cryptography.Xml.Reference> obiekt, który opisano, czego się.  Aby zalogować się w całym dokumencie, należy ustawić <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> właściwość `""`.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  Dodaj <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> obiekt <xref:System.Security.Cryptography.Xml.Reference> obiektu.  Przekształcenie umożliwia weryfikatora do reprezentowania danych XML w identyczny sposób, że osoby podpisującej używane.  Dane XML mogą być reprezentowane w różny sposób, aby ten krok jest niezbędny do weryfikacji.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8.  Dodaj <xref:System.Security.Cryptography.Xml.Reference> obiekt <xref:System.Security.Cryptography.Xml.SignedXml> obiektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. Obliczenia podpis, wywołując <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> metody.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. Pobieranie podpis reprezentację XML (<`Signature`> elementu) i zapisz go na nowy <xref:System.Xml.XmlElement> obiektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. Dołącz element do <xref:System.Xml.XmlDocument> obiektu.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. Zapisz dokument.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie założono, że plik o nazwie `test.xml` istnieje w tym samym katalogu co skompilowanego programu.  Następujący kod XML może umieścić w pliku o nazwie `test.xml` i użycie go w tym przykładzie.  
  
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
  
-   Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
-   Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie magazynu lub transfer klucza prywatnego pary kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat klucze szyfrowania symetrycznego i asymetrycznego zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie można osadzić klucza prywatnego bezpośrednio w kodzie źródłowym.  Osadzone klucze można łatwo odczytać z zestawu przy użyciu [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstów, takiego jak Notatnik.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>  
- [Instrukcje: sprawdzanie podpisów cyfrowych w dokumentach XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
