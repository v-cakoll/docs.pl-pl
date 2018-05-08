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
ms.openlocfilehash: fcb2d344e1baae259cebbf8426bfd10de19bf925
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Porady: szyfrowanie elementów XML za pomocą certyfikatów X.509
Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML jest standardowym sposobem exchange lub przechowywania zaszyfrowanych danych XML, nie martwiąc się o łatwo odczytywane dane.  Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz specyfikację sieci World Wide Web konsorcjum W3C szyfrowanie XML zlokalizowanej w http://www.w3.org/TR/xmldsig-core/.  
  
 Szyfrowanie XML służy do zastępowania żadnych — element XML lub dokument z <`EncryptedData`> element, który zawiera zaszyfrowane dane XML. <`EncryptedData`> Element może zawierać elementy podrzędne, które zawierają informacji o kluczach i procesy użyty podczas szyfrowania.  Szyfrowanie XML umożliwia dokumentu zawiera wiele elementów zaszyfrowane i pozwala element zaszyfrowanie wiele razy.  Przykład kodu w tej procedurze przedstawiono sposób tworzenia <`EncryptedData`> element wraz z kilku elementów sub, w których można później podczas odszyfrowywania.  
  
 W tym przykładzie szyfruje elementu XML za pomocą dwóch kluczy.  Generuje, używając certyfikatu X.509 testu [narzędzie tworzenia certyfikatów (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) i zapisuje certyfikat do magazynu certyfikatów.  W przykładzie następnie programowo pobiera certyfikat i używa go do zaszyfrowania — element XML przy użyciu <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metody.  Wewnętrznie <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> metoda tworzy klucz sesji oddzielne i używa go do zaszyfrowania dokumentu XML. Ta metoda szyfruje klucz sesji i zapisuje go wraz z zaszyfrowanego pliku XML w ramach nowej <`EncryptedData`> elementu.  
  
 Aby odszyfrować elementu XML, po prostu Wywołaj <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodę, która automatycznie pobiera certyfikat X.509 z magazynu i wykonuje niezbędne odszyfrowywania.  Aby uzyskać więcej informacji na temat odszyfrowywania element XML, która została zaszyfrowana przy użyciu tej procedury, zobacz [porady: odszyfrowywanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 W tym przykładzie jest przydatne w sytuacjach, gdy wiele aplikacji potrzeba udostępnienia zaszyfrowanych danych lub gdy aplikacja musi zapisać zaszyfrowanych danych w okresie, które działa między.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Aby zaszyfrować element XML z certyfikatem X.509  
  
1.  Użyj [narzędzie tworzenia certyfikatów (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) do wygenerowania certyfikatu X.509 testu i umieszczanie jej w magazynie użytkownika lokalnego.  Należy wygenerować klucz wymiany oraz musi mieć możliwy do wyeksportowania klucza. Uruchom następujące polecenie:  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  Utwórz <xref:System.Security.Cryptography.X509Certificates.X509Store> i zainicjować go, aby otworzyć Sklep bieżącego użytkownika.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  Otwórz magazyn w trybie tylko do odczytu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  Inicjowanie <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> wszystkie certyfikaty w magazynie.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  Wyliczenia certyfikaty w magazynie i znaleźć certyfikatu z odpowiednią nazwę.  W tym przykładzie certyfikat o nazwie `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  Zamknij Sklep po znajduje się certyfikat.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  Utwórz <xref:System.Xml.XmlDocument> obiektu przez ładowanie pliku XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  Znajdź element określony w <xref:System.Xml.XmlDocument> obiekt i utworzyć nową <xref:System.Xml.XmlElement> obiekt reprezentujący element, który chcesz zaszyfrować.  W tym przykładzie `"creditcard"` element jest zaszyfrowany.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i jej użyciu można zaszyfrować określony element za pomocą certyfikatu X.509.  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> Metoda zwraca zaszyfrowany element jako <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Zastąp element z oryginalnego <xref:System.Xml.XmlDocument> obiekt z <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Zapisz <xref:System.Xml.XmlDocument> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.  
  
-   Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Certyfikat X.509 używany w tym przykładzie jest tylko do celów testowych.  Aplikacje należy użyć certyfikatu X.509 generowane przez zaufany urząd certyfikacji lub Użyj certyfikatu wygenerowanego przez serwer Microsoft Windows certyfikatu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography.Xml>  
 [Instrukcje: odszyfrowywanie elementów XML za pomocą certyfikatów X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
