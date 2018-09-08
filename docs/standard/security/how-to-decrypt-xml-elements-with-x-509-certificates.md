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
ms.openlocfilehash: 25a2fb441269508402263e103a6c6e1be2635406
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140739"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Porady: odszyfrowywanie elementów XML za pomocą certyfikatów X.509
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw do szyfrowania i odszyfrowywania elementu w dokumencie XML.  Szyfrowanie XML to standardowy sposób wymiany ani nie przechowują zaszyfrowane dane XML, nie martwiąc się o łatwo odczytywanych danych.  Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz specyfikację World Wide Web Consortium (W3C) dla szyfrowanie XML znajdujący się w http://www.w3.org/TR/xmldsig-core/.  
  
 W tym przykładzie odszyfrowuje element XML, która została zaszyfrowana przy użyciu metod opisanych w: [porady: szyfrowanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).  Znajdzie <`EncryptedData`> element, odszyfrowuje elementu i następnie zamienia element w oryginalnym elemencie XML zwykłego tekstu.  
  
 Przykład kodu w tej procedurze odszyfrowuje — element XML przy użyciu certyfikatu X.509 z lokalnego magazynu certyfikatów bieżącego konta użytkownika.  W przykładzie użyto <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodę, aby automatycznie pobrać certyfikat X.509 i odszyfrować klucz przechowywany w sesji <`EncryptedKey`> elementu <`EncryptedData`> element.  <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> Metoda następnie automatycznie używa klucza sesji można odszyfrować XML element.  
  
 W tym przykładzie jest odpowiednie w sytuacji, gdy wiele aplikacji muszą udostępniać dane zaszyfrowane lub której aplikacja musi zapisać zaszyfrowane dane między godzinami, które działa.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>Aby odszyfrować element XML z certyfikatem X.509  
  
1.  Utwórz <xref:System.Xml.XmlDocument> obiektu, ładując plik XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do odszyfrowania.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  Utwórz nową <xref:System.Security.Cryptography.Xml.EncryptedXml> obiektu przez przekazanie <xref:System.Xml.XmlDocument> obiekt do konstruktora.  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  Odszyfrować za pomocą dokumentu XML <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody.  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  Zapisz <xref:System.Xml.XmlDocument> obiektu.  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie założono, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowanego programu.  Przyjęto również założenie, że `"test.xml"` zawiera `"creditcard"` elementu.  Następujący kod XML może umieścić w pliku o nazwie `test.xml` i użycie go w tym przykładzie.  
  
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
  
-   Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
-   Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Certyfikat X.509 używany w tym przykładzie jest tylko do celów testowych.  Aplikacje, należy użyć certyfikatu X.509, który jest generowany przez zaufany urząd certyfikacji lub użycia certyfikatu wygenerowanego przez program Microsoft Windows Certificate Server.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>  
- [Instrukcje: szyfrowanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
