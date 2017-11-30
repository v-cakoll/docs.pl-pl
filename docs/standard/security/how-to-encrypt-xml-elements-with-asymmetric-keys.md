---
title: "Porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd8b63ab02527f66d30251f21a63e19ce4da50ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych
Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML jest standardowym sposobem exchange lub przechowywania zaszyfrowanych danych XML, nie martwiąc się o łatwo odczytywane dane.  Aby uzyskać więcej informacji o szyfrowaniu XML standardowego Zobacz się, że w sieci World Wide Web konsorcjum W3C specyfikacji szyfrowanie XML znajduje się w http://www.w3.org/TR/xmldsig-core/.  
  
 Szyfrowanie XML służy do zastępowania żadnych — element XML lub dokument z <`EncryptedData`> element, który zawiera zaszyfrowane dane XML.  <`EncryptedData`> Element może również zawierać elementy podrzędne, które zawierają informacji o kluczach i procesy użyty podczas szyfrowania.  Szyfrowanie XML umożliwia dokumentu zawiera wiele elementów zaszyfrowane i pozwala element zaszyfrowanie wiele razy.  Przykład kodu w tej procedurze przedstawiono sposób tworzenia <`EncryptedData`> element wraz z kilku elementów sub, w których można później podczas odszyfrowywania.  
  
 W tym przykładzie szyfruje elementu XML za pomocą dwóch kluczy.  Generuje pary kluczy publiczny/prywatny RSA, a zapisuje pary kluczy do bezpiecznego kontenera kluczy.  Przykład tworzy następnie klucz sesji oddzielne przy użyciu algorytmu szyfrowania AES (Advanced Standard), nazywany również algorytmu Rijndael.  Przykład używa klucza sesji AES do zaszyfrowania dokumentu XML, a następnie używa klucza publicznego RSA do szyfrowania klucza sesji AES.  Na koniec przykładzie zapisuje zaszyfrowanego klucza sesji AES i szyfrowania danych XML do dokumentu XML w ramach nowej <`EncryptedData`> elementu.  
  
 Aby odszyfrować elementu XML, pobrać przy użyciu kontenera kluczy RSA klucza prywatnego, go użyć do odszyfrowania klucza sesji i następnie użyć klucza sesji do odszyfrowania dokumentu.  Aby uzyskać więcej informacji na temat odszyfrowywania element XML, która została zaszyfrowana przy użyciu tej procedury, zobacz [porady: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 W tym przykładzie jest przydatne w sytuacjach, gdy wiele aplikacji potrzeba udostępnienia zaszyfrowanych danych lub gdy aplikacja musi zapisać zaszyfrowanych danych w okresie, które działa między.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Do szyfrowania z klucza asymetrycznego — element XML  
  
1.  Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera kluczy.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Generowanie klucza symetrycznego użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Klucz jest automatycznie zapisywane do kontenera kluczy podczas przekazywania <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Ten klucz będzie używany do szyfrowania klucza sesji AES i może zostać później pobrana do odszyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Utwórz <xref:System.Xml.XmlDocument> obiektu przez ładowanie pliku XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  Znajdź element określony w <xref:System.Xml.XmlDocument> obiekt i utworzyć nową <xref:System.Xml.XmlElement> obiekt reprezentujący element, który chcesz zaszyfrować. W tym przykładzie `"creditcard"` element jest zaszyfrowany.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  Tworzenie klucza nowej sesji przy użyciu <xref:System.Security.Cryptography.RijndaelManaged> klasy.  Ten klucz będą szyfrowania elementu XML i szyfrowane sam i umieszczone w dokumencie XML.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i jej użyciu można zaszyfrować określony element przy użyciu klucza sesji.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda zwraca zaszyfrowany element jako tablicę bajtów zaszyfrowanych.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  Utworzyć <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu i wypełnić ją identyfikator URL zaszyfrowany element XML.  Ten identyfikator URL umożliwia odszyfrowywania strona wiedzieć, że plik XML zawiera zaszyfrowany element.  Można użyć <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> Aby określić identyfikator adresu URL.  Element XML w postaci zwykłego tekstu zostaną zastąpione <`EncryptedData`> hermetyzowany to element <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  Utwórz <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt, który jest inicjowana na adres URL identyfikator algorytmu kryptograficznego używanego do generowania klucza sesji.  Przekaż <xref:System.Security.Cryptography.Xml.EncryptionMethod> do obiektu <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> właściwości.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Utwórz <xref:System.Security.Cryptography.Xml.EncryptedKey> będzie zawierał klucza szyfrowanej sesji.  Szyfrowanie klucza sesji, należy dodać go do <xref:System.Security.Cryptography.Xml.EncryptedKey> obiekt, a następnie wprowadź nazwę klucza sesji i adres URL identyfikatora klucza.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Utwórz nową <xref:System.Security.Cryptography.Xml.DataReference> obiekt, który mapuje zaszyfrowane dane z kluczem określonej sesji.  Ten opcjonalny krok pozwala łatwo określić, że wielu części dokumentu XML były szyfrowane przez jeden klucz.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Dodaj zaszyfrowany klucz do <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Utwórz nową <xref:System.Security.Cryptography.Xml.KeyInfo> obiektu do określenia nazwy kluczy RSA.  Dodaj go do <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu. Pomaga to strona odszyfrowywania zidentyfikować poprawne klucza asymetrycznego do użycia podczas odszyfrowywania klucza sesji.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Dodaj element zaszyfrowane dane do <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Zastąp element z oryginalnego <xref:System.Xml.XmlDocument> obiekt z <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Zapisz <xref:System.Xml.XmlDocument> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.  
  
-   Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie przechowują symetrycznego klucza kryptograficznego w postaci zwykłego tekstu lub transfer klucza symetrycznego między komputerami w postaci zwykłego tekstu.  Ponadto nigdy nie magazynu lub przenieść klucz prywatny para kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat symetrycznego i asymetrycznego kluczy kryptograficznych, zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie osadzaj klucza bezpośrednio w kodzie źródłowym.  Osadzony kluczy można łatwo odczytać z zestawu za pomocą [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstu, takiego jak Notatnik.  
  
 Gdy wszystko będzie gotowe za pomocą klucza kryptograficznego, wyczyść go z pamięci przez ustawienie każdego bajtu na wartość zero lub wywoływania <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy kryptografii zarządzanych.  Klucze kryptograficzne czasami może odczytywać pamięci przez debuger lub odczytu z dysku twardego, jeśli lokalizacji pamięci jest stronicowana na dysk.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography.Xml>  
 [Porady: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
