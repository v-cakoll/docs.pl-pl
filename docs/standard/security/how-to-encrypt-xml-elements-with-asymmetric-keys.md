---
title: 'Porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61984d4778e42abf378a1369a86ba599d78980af
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121327"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML to standardowy sposób wymiany ani nie przechowują zaszyfrowane dane XML, nie martwiąc się o łatwo odczytywanych danych.  Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz specyfikację World Wide Web Consortium (W3C) dla szyfrowanie XML znajdujący się w <https://www.w3.org/TR/xmldsig-core/>.  
  
 Szyfrowanie XML umożliwia zastąpienie dowolnego elementu XML lub dokumentów za pomocą <`EncryptedData`> element, który zawiera zaszyfrowane dane XML.  <`EncryptedData`> Element może również zawierać elementy podrzędne, które zawierają informacje o kluczach i procesem stosowanym podczas szyfrowania.  Szyfrowanie XML umożliwia dokumentu zawiera wiele elementów zaszyfrowanych i umożliwia elementu do zaszyfrowania wiele razy.  Przykład kodu w tej procedurze przedstawiono sposób tworzenia <`EncryptedData`> element wraz z kilku elementów podrzędnych, w które można użyć później, podczas odszyfrowywania.  
  
 W tym przykładzie szyfruje elementu XML za pomocą dwóch kluczy.  On generuje parę kluczy publiczny/prywatny RSA i zapisuje pary kluczy do bezpiecznego kontenera kluczy.  Ten przykład tworzy następnie klucz oddzielną sesję przy użyciu algorytmu Advanced Encryption Standard (AES), nazywany również algorytmu Rijndael.  Przykład używa klucza sesji AES do zaszyfrowania dokumentu XML, a następnie używa klucza publicznego RSA do szyfrowania klucza sesji AES.  Na koniec przykład zapisuje zaszyfrowanego klucza sesji AES i szyfrowania danych XML w dokumencie XML w ramach nowego <`EncryptedData`> element.  
  
 Aby odszyfrować XML element, pobrać prywatnego klucza RSA z kontenera kluczy, użyć go do odszyfrowywania klucza sesji i następnie użyj klucza sesji w celu odszyfrowania dokumentu.  Aby uzyskać więcej informacji na temat odszyfrować element XML, która została zaszyfrowana przy użyciu tej procedury, zobacz [porady: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 W tym przykładzie jest odpowiednie w sytuacji, gdy wiele aplikacji muszą udostępniać dane zaszyfrowane lub której aplikacja musi zapisać zaszyfrowane dane między godzinami, które działa.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Aby zaszyfrować XML element przy użyciu klucza asymetrycznego  
  
1.  Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera kluczy.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Generuj klucz symetryczny za pomocą <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Klucz są automatycznie zapisywane w kontenerze kluczy, jeśli przekazujesz <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Ten klucz będzie używany do szyfrowania klucza sesji AES i może zostać później pobrana do odszyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Utwórz <xref:System.Xml.XmlDocument> obiektu, ładując plik XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  Znajdź element określony w <xref:System.Xml.XmlDocument> obiektu i Utwórz nowy <xref:System.Xml.XmlElement> obiekt reprezentujący element, który chcesz zaszyfrować. W tym przykładzie `"creditcard"` elementu są szyfrowane.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  Utwórz nową sesję klucza przy użyciu <xref:System.Security.Cryptography.RijndaelManaged> klasy.  Ten klucz zostanie zaszyfrować XML element i następnie zaszyfrowana sam i umieszczone w dokumencie XML.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i jej użyciu można zaszyfrować określony element przy użyciu klucza sesji.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda zwraca zaszyfrowany element jako tablicę bajtów zaszyfrowanych.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  Konstruowania <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu i wypełnianie jej identyfikator adresu URL elementu XML zaszyfrowane.  Ten identyfikator URL umożliwia odszyfrowywanie innych firm, dowiedzieć się, że plik XML zawiera element zaszyfrowane.  Możesz użyć <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pola, aby określić identyfikator URL.  Element XML w postaci zwykłego tekstu, zostanie zastąpiona przez <`EncryptedData`> element hermetyzowane to <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  Utwórz <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt, który jest inicjowany na identyfikator URL algorytm kryptograficzny używany do generowania klucza sesji.  Przekaż <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> właściwości.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Utwórz <xref:System.Security.Cryptography.Xml.EncryptedKey> będzie zawierał klucza szyfrowanej sesji.  Szyfrowanie klucza sesji, dodaj ją do <xref:System.Security.Cryptography.Xml.EncryptedKey> obiektu, a następnie wprowadź nazwę klucza sesji i adres URL identyfikatora klucza.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Utwórz nową <xref:System.Security.Cryptography.Xml.DataReference> obiektu, który mapuje zaszyfrowanych danych w kluczu określonej sesji.  Ten opcjonalny krok pozwala łatwo określić, że wiele części dokumentu XML zostały zaszyfrowane przy użyciu jednego klucza.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Dodaj zaszyfrowany klucz, który <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Utwórz nową <xref:System.Security.Cryptography.Xml.KeyInfo> obiektu, aby określić nazwę klucza RSA.  Dodaj go do <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu. Dzięki temu odszyfrowywanie strona identyfikacji poprawny klucz asymetryczny do użycia podczas odszyfrowywania klucza sesji.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Dodaj element zaszyfrowane dane <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Zastąp element z oryginalnym <xref:System.Xml.XmlDocument> obiekt z <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Zapisz <xref:System.Xml.XmlDocument> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
-   Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie przechowują symetrycznego klucza kryptograficznego w postaci zwykłego tekstu lub przenieść klucz symetryczny między maszynami w postaci zwykłego tekstu.  Ponadto nigdy nie magazynu lub transfer klucza prywatnego pary kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat klucze szyfrowania symetrycznego i asymetrycznego zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie można osadzić klucza bezpośrednio w kodzie źródłowym.  Osadzone klucze można łatwo odczytać z zestawu przy użyciu [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstów, takiego jak Notatnik.  
  
 Po zakończeniu za pomocą klucza kryptograficznego, wyczyść to pole wyboru z pamięci, ustawiając poszczególne bajty do zera lub przez wywołanie <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy zarządzanej kryptografii.  Klucze kryptograficzne czasami można odczytać pamięci przez debuger lub odczytu z dysku twardego, jeśli lokalizacja pamięci jest stronicowanej na dysku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>  
- [Instrukcje: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
