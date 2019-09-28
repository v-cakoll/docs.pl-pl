---
title: 'Instrukcje: Szyfrowanie elementów XML za pomocą certyfikatów X.509'
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
ms.openlocfilehash: d569d3c020e7329d987e957f181b34c8cfbf941a
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353863"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Instrukcje: Szyfrowanie elementów XML za pomocą certyfikatów X.509
Można użyć klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml> do szyfrowania elementu w dokumencie XML.  Szyfrowanie XML jest standardowym sposobem wymiany i przechowywania zaszyfrowanych danych XML bez obaw o dane, które są łatwo odczytywane.  Aby uzyskać więcej informacji na temat standardu szyfrowania XML, zobacz Specyfikacja organizacja World Wide Web Consortium (W3C) dla szyfrowania XML znajdującego się w <https://www.w3.org/TR/xmldsig-core/>.  
  
 Możesz użyć szyfrowania XML, aby zamienić dowolny element XML lub dokument z < `EncryptedData` > elementu, który zawiera zaszyfrowane dane XML. Element < `EncryptedData` > może zawierać elementy podrzędne, które zawierają informacje o kluczach i procesach używanych podczas szyfrowania.  Szyfrowanie XML pozwala dokument może zawierać wiele zaszyfrowanych elementów i umożliwia wielokrotne szyfrowanie elementu.  W przykładzie kodu w tej procedurze pokazano, jak utworzyć element < `EncryptedData` > wraz z kilkoma innymi elementami podrzędnymi, które można później użyć podczas odszyfrowywania.  
  
 Ten przykład szyfruje element XML przy użyciu dwóch kluczy. Generuje certyfikat testu X. 509 za pomocą narzędzia do [tworzenia certyfikatów (Makecert. exe)](/windows/desktop/SecCrypto/makecert) i zapisuje certyfikat w magazynie certyfikatów. Przykładowo program programowo pobiera certyfikat i używa go do szyfrowania elementu XML przy użyciu metody <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>. Wewnętrznie metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> tworzy oddzielny klucz sesji i używa jej do szyfrowania dokumentu XML. Ta metoda szyfruje klucz sesji i zapisuje go wraz z zaszyfrowanym kodem XML w ramach nowego < `EncryptedData` > elementu.  
  
 Aby odszyfrować element XML, po prostu wywołaj metodę <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>, która automatycznie pobiera certyfikat X. 509 ze sklepu i wykonuje wymagane odszyfrowywanie.  Aby uzyskać więcej informacji na temat odszyfrowywania elementu XML, który został zaszyfrowany przy użyciu tej procedury, zobacz [How: Odszyfruj elementy XML za pomocą certyfikatów X. 509 @ no__t-0.  
  
 Ten przykład jest odpowiedni dla sytuacji, w których wiele aplikacji musi udostępniać zaszyfrowane dane lub w przypadku, gdy aplikacja wymaga zapisywania zaszyfrowanych danych między uruchomionymi danymi.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Aby zaszyfrować element XML z certyfikatem X.509  
  
1. Użyj [Narzędzia do tworzenia certyfikatów (Makecert. exe)](/windows/desktop/SecCrypto/makecert) w celu wygenerowania testowego certyfikatu X. 509 i umieszczenie go w lokalnym magazynie użytkowników. Musisz wygenerować klucz wymiany i należy dokonać eksportu klucza. Uruchom następujące polecenie:  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. Utwórz obiekt <xref:System.Security.Cryptography.X509Certificates.X509Store> i zainicjuj go, aby otworzyć bieżący magazyn użytkowników.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. Otwórz sklep w trybie tylko do odczytu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. Zainicjuj <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> ze wszystkimi certyfikatami w sklepie.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. Wylicz certyfikaty w magazynie i Znajdź certyfikat z odpowiednią nazwą.  W tym przykładzie certyfikat nosi nazwę `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. Zamknij sklep po zlokalizowaniu certyfikatu.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. Utwórz obiekt <xref:System.Xml.XmlDocument> przez załadowanie pliku XML z dysku.  Obiekt <xref:System.Xml.XmlDocument> zawiera element XML do zaszyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. Znajdź określony element w obiekcie <xref:System.Xml.XmlDocument> i Utwórz nowy obiekt <xref:System.Xml.XmlElement> do reprezentowania elementu, który chcesz zaszyfrować.  W tym przykładzie element `"creditcard"` jest szyfrowany.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> i użyj go do szyfrowania określonego elementu przy użyciu certyfikatu X. 509.  Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> zwraca zaszyfrowany element jako obiekt <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Zastąp element z oryginalnego obiektu <xref:System.Xml.XmlDocument> elementem <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Zapisz obiekt <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowany program.  Zakłada również, że `"test.xml"` zawiera element `"creditcard"`.  Można umieścić następujący kod XML w pliku o nazwie `test.xml` i użyć go w tym przykładzie.  
  
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
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
- Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography> i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Certyfikat X. 509 użyty w tym przykładzie służy tylko do celów testowych.  Aplikacje powinny używać certyfikatu X. 509 wygenerowanego przez zaufany urząd certyfikacji lub użyć certyfikatu wygenerowanego przez serwer certyfikatów systemu Microsoft Windows.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: Odszyfrowywanie elementów XML za pomocą certyfikatów X. 509 @ no__t-0
