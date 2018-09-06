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
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878944"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Porady: szyfrowanie elementów XML za pomocą certyfikatów X.509
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML to standardowy sposób wymiany ani nie przechowują zaszyfrowane dane XML, nie martwiąc się o łatwo odczytywanych danych.  Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz specyfikację World Wide Web Consortium (W3C) dla szyfrowanie XML znajdujący się w http://www.w3.org/TR/xmldsig-core/.  
  
 Szyfrowanie XML umożliwia zastąpienie dowolnego elementu XML lub dokumentów za pomocą <`EncryptedData`> element, który zawiera zaszyfrowane dane XML. <`EncryptedData`> Element może zawierać elementy podrzędne, które zawierają informacje o kluczach i procesem stosowanym podczas szyfrowania.  Szyfrowanie XML umożliwia dokumentu zawiera wiele elementów zaszyfrowanych i umożliwia elementu do zaszyfrowania wiele razy.  Przykład kodu w tej procedurze przedstawiono sposób tworzenia <`EncryptedData`> element wraz z kilku elementów podrzędnych, w które można użyć później, podczas odszyfrowywania.  
  
 W tym przykładzie szyfruje elementu XML za pomocą dwóch kluczy.  Generuje testu X.509 certyfikatu za pomocą [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) i zapisuje certyfikat do magazynu certyfikatów.  Przykład następnie programowo pobiera certyfikat i używa go do zaszyfrowania — element XML przy użyciu <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metody.  Wewnętrznie <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metoda tworzy klucz oddzielną sesję i używa go do zaszyfrowania dokumentu XML. Ta metoda szyfruje klucz sesji i zapisuje go wraz z zaszyfrowanego pliku XML, w ramach nowego <`EncryptedData`> element.  
  
 Aby odszyfrować XML element, wystarczy wywołać <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody, która automatycznie pobiera certyfikat X.509 z magazynu i wykonuje niezbędne odszyfrowywania.  Aby uzyskać więcej informacji na temat odszyfrować element XML, która została zaszyfrowana przy użyciu tej procedury, zobacz [porady: odszyfrowywanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 W tym przykładzie jest odpowiednie w sytuacji, gdy wiele aplikacji muszą udostępniać dane zaszyfrowane lub której aplikacja musi zapisać zaszyfrowane dane między godzinami, które działa.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Aby zaszyfrować element XML z certyfikatem X.509  
  
1.  Użyj [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) do generowania certyfikatu X.509 testu i umieść go w magazynie użytkownika lokalnego.  Należy wygenerować klucz wymiany, i należy klucz możliwy do eksportu. Uruchom następujące polecenie:  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  Utwórz <xref:System.Security.Cryptography.X509Certificates.X509Store> obiektu i zainicjuj ją, aby otworzyć magazynie bieżącego użytkownika.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  Otwórz Sklep w trybie tylko do odczytu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  Inicjowanie <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> wszystkie certyfikaty w magazynie.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  Wyliczanie przy użyciu certyfikatów w magazynie i znaleźć certyfikatu z odpowiednią nazwę.  W tym przykładzie nosi nazwę certyfikatu `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  Po znajduje się certyfikat, należy zamknąć magazynu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  Utwórz <xref:System.Xml.XmlDocument> obiektu, ładując plik XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  Znajdź element określony w <xref:System.Xml.XmlDocument> obiektu i Utwórz nowy <xref:System.Xml.XmlElement> obiekt reprezentujący element, który chcesz zaszyfrować.  W tym przykładzie `"creditcard"` elementu są szyfrowane.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i jej użyciu można zaszyfrować określony element przy użyciu certyfikatu X.509.  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda zwraca element zaszyfrowany jako <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Zastąp element z oryginalnym <xref:System.Xml.XmlDocument> obiekt z <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Zapisz <xref:System.Xml.XmlDocument> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
-   Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Certyfikat X.509 używany w tym przykładzie jest tylko do celów testowych.  Aplikacje, należy użyć certyfikatu X.509, który jest generowany przez zaufany urząd certyfikacji lub użycia certyfikatu wygenerowanego przez program Microsoft Windows Certificate Server.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>  
- [Instrukcje: odszyfrowywanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
