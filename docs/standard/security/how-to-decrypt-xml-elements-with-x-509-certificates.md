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
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Porady: odszyfrowywanie elementów XML za pomocą certyfikatów X.509
Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw do szyfrowania i odszyfrowywania element w dokumencie XML.  Szyfrowanie XML jest standardowym sposobem exchange lub przechowywania zaszyfrowanych danych XML, nie martwiąc się o łatwo odczytywane dane.  Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz specyfikację sieci World Wide Web konsorcjum W3C szyfrowanie XML zlokalizowanej w http://www.w3.org/TR/xmldsig-core/.  
  
 W tym przykładzie odszyfrowuje element XML, która została zaszyfrowana przy użyciu metod opisanych w: [porady: szyfrowanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).  Znajdzie <`EncryptedData`> elementu odszyfrowuje elementu, a następnie zastępuje element oryginalny element XML w postaci zwykłego tekstu.  
  
 Przykład kodu w tej procedurze odszyfrowuje elementu XML za pomocą certyfikatu X.509 z lokalnego magazynu certyfikatów bieżącego konta użytkownika.  W przykładzie użyto <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodę, aby automatycznie pobrać certyfikatu X.509 i odszyfrować klucza przechowywanego w sesji <`EncryptedKey`> elementu <`EncryptedData`> elementu.  <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> Metoda następnie automatycznie używa klucza sesji do odszyfrowania elementu XML.  
  
 W tym przykładzie jest przydatne w sytuacjach, gdy wiele aplikacji potrzeba udostępnienia zaszyfrowanych danych lub gdy aplikacja musi zapisać zaszyfrowanych danych w okresie, które działa między.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>Aby odszyfrować element XML z certyfikatem X.509  
  
1.  Utwórz <xref:System.Xml.XmlDocument> obiektu przez ładowanie pliku XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do odszyfrowania.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  Utwórz nową <xref:System.Security.Cryptography.Xml.EncryptedXml> obiektu przez przekazywanie <xref:System.Xml.XmlDocument> obiekt do konstruktora.  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  Odszyfrować za pomocą dokumentu XML <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody.  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  Zapisz <xref:System.Xml.XmlDocument> obiektu.  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co program skompilowany.  Założono również, że `"test.xml"` zawiera `"creditcard"` elementu.  Następujący kod XML można umieścić w pliku o nazwie `test.xml` i użyć w tym przykładzie.  
  
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
  
-   Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.  
  
-   Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Certyfikat X.509 używany w tym przykładzie jest tylko do celów testowych.  Aplikacje należy użyć certyfikatu X.509 generowane przez zaufany urząd certyfikacji lub Użyj certyfikatu wygenerowanego przez serwer Microsoft Windows certyfikatu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography.Xml>  
 [Instrukcje: szyfrowanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
