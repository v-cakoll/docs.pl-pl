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
ms.openlocfilehash: 32a6d95b96bb20571c14c16cc70b944fa3e4032b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277391"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Porady: odszyfrowywanie elementów XML za pomocą certyfikatów X.509
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw do szyfrowania i odszyfrowywania elementu w dokumencie XML.  Szyfrowanie XML jest standardowym sposobem wymiany i przechowywania zaszyfrowanych danych XML bez obaw o dane, które są łatwo odczytywane.  Aby uzyskać więcej informacji na temat standardu szyfrowania XML, zapoznaj się z artykułem Specyfikacja organizacja World Wide Web Consortium (W3C) dla szyfrowania XML znajdującego się w temacie <https://www.w3.org/TR/xmldsig-core/> .  
  
 Ten przykład odszyfrowuje element XML, który został zaszyfrowany przy użyciu metod opisanych w: [jak szyfrować elementy XML za pomocą certyfikatów X. 509](how-to-encrypt-xml-elements-with-x-509-certificates.md).  Znajduje `EncryptedData` element> <, odszyfrowuje element, a następnie zamienia element na oryginalny element XML w formacie zwykłego tekstu.  
  
 Przykład kodu w tej procedurze odszyfrowuje element XML przy użyciu certyfikatu X. 509 z lokalnego magazynu certyfikatów bieżącego konta użytkownika.  W przykładzie używa <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody do automatycznego pobierania certyfikatu X. 509 i odszyfrowywania klucza sesji przechowywanego w <> elementu `EncryptedKey` <`EncryptedData`>.  <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>Metoda następnie automatycznie używa klucza sesji do odszyfrowania elementu XML.  
  
 Ten przykład jest odpowiedni dla sytuacji, w których wiele aplikacji musi udostępniać zaszyfrowane dane lub w przypadku, gdy aplikacja wymaga zapisywania zaszyfrowanych danych między uruchomionymi danymi.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>Aby odszyfrować element XML z certyfikatem X.509  
  
1. Utwórz <xref:System.Xml.XmlDocument> obiekt przez załadowanie pliku XML z dysku.  <xref:System.Xml.XmlDocument>Obiekt zawiera element XML do odszyfrowania.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. Utwórz nowy <xref:System.Security.Cryptography.Xml.EncryptedXml> obiekt przez przekazanie <xref:System.Xml.XmlDocument> obiektu do konstruktora.  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. Odszyfruj dokument XML przy użyciu <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody.  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. Zapisz <xref:System.Xml.XmlDocument> obiekt.  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowany program.  Zakłada również, że `"test.xml"` zawiera `"creditcard"` element.  Można umieścić następujący kod XML w pliku o nazwie `test.xml` i użyć go w tym przykładzie.  
  
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
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll` .  
  
- Uwzględnij następujące przestrzenie nazw: <xref:System.Xml> , <xref:System.Security.Cryptography> , i <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Certyfikat X. 509 użyty w tym przykładzie służy tylko do celów testowych.  Aplikacje powinny używać certyfikatu X. 509 wygenerowanego przez zaufany urząd certyfikacji lub użyć certyfikatu wygenerowanego przez serwer certyfikatów systemu Microsoft Windows.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: szyfrowanie elementów XML za pomocą certyfikatów X.509](how-to-encrypt-xml-elements-with-x-509-certificates.md)
