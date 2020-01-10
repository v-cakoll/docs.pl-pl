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
ms.openlocfilehash: 2ebf3f86ac550c0179b2e26879a7df128fd529e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706100"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych
Możesz użyć klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml>, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML jest standardowym sposobem wymiany i przechowywania zaszyfrowanych danych XML bez obaw o dane, które są łatwo odczytywane.  Aby uzyskać więcej informacji na temat standardu szyfrowania XML, zobacz Specyfikacja organizacja World Wide Web Consortium (W3C) dla szyfrowania XML znajdującego się w <https://www.w3.org/TR/xmldsig-core/>.  
  
 Możesz użyć szyfrowania XML, aby zamienić dowolny element XML lub dokument z <`EncryptedData`> elementu, który zawiera zaszyfrowane dane XML.  Element <`EncryptedData`> może również zawierać elementy podrzędne, które zawierają informacje o kluczach i procesach używanych podczas szyfrowania.  Szyfrowanie XML pozwala dokument może zawierać wiele zaszyfrowanych elementów i umożliwia wielokrotne szyfrowanie elementu.  Przykład kodu w tej procedurze pokazuje, jak utworzyć <`EncryptedData`> elementu wraz z kilkoma innymi elementami podrzędnymi, które można później użyć podczas odszyfrowywania.  
  
 Ten przykład szyfruje element XML przy użyciu dwóch kluczy.  Generuje parę kluczy publiczny/prywatny RSA i zapisuje parę kluczy do kontenera Secure Key.  W przykładzie tworzony jest oddzielny klucz sesji przy użyciu algorytmu Advanced Encryption Standard (AES), nazywany również algorytmem Rijndael.  W przykładzie zastosowano klucz sesji AES do szyfrowania dokumentu XML, a następnie jest on stosowany do szyfrowania klucza sesji AES przy użyciu klucza publicznego RSA.  Na koniec przykład zapisuje zaszyfrowany klucz sesji AES i zaszyfrowane dane XML w dokumencie XML w ramach nowego <`EncryptedData`> elementu.  
  
 Aby odszyfrować element XML, należy pobrać klucz prywatny RSA z kontenera kluczy, użyć go do odszyfrowania klucza sesji, a następnie użyć klucza sesji do odszyfrowania dokumentu.  Aby uzyskać więcej informacji na temat odszyfrowywania elementu XML, który został zaszyfrowany przy użyciu tej procedury, zobacz [How to: Deszyfruj elementy XML za pomocą kluczy asymetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Ten przykład jest odpowiedni dla sytuacji, w których wiele aplikacji musi udostępniać zaszyfrowane dane lub w przypadku, gdy aplikacja wymaga zapisywania zaszyfrowanych danych między uruchomionymi danymi.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Aby zaszyfrować element XML kluczem asymetrycznym  
  
1. Utwórz obiekt <xref:System.Security.Cryptography.CspParameters> i określ nazwę kontenera kluczy.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Generuj klucz symetryczny przy użyciu klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Klucz jest automatycznie zapisywany w kontenerze kluczy podczas przekazywania obiektu <xref:System.Security.Cryptography.CspParameters> do konstruktora klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Ten klucz będzie używany do szyfrowania klucza sesji AES i można go później pobrać w celu odszyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Utwórz obiekt <xref:System.Xml.XmlDocument>, ładując plik XML z dysku.  Obiekt <xref:System.Xml.XmlDocument> zawiera element XML do zaszyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. Znajdź określony element w obiekcie <xref:System.Xml.XmlDocument> i Utwórz nowy obiekt <xref:System.Xml.XmlElement> do reprezentowania elementu, który chcesz zaszyfrować. W tym przykładzie element `"creditcard"` jest szyfrowany.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. Utwórz nowy klucz sesji przy użyciu klasy <xref:System.Security.Cryptography.RijndaelManaged>.  Ten klucz spowoduje zaszyfrowanie elementu XML, a następnie zaszyfrowanie go i umieszczenie w dokumencie XML.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> i użyj go do zaszyfrowania określonego elementu przy użyciu klucza sesji.  Metoda <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> zwraca zaszyfrowany element jako tablicę szyfrowanych bajtów.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. Utwórz obiekt <xref:System.Security.Cryptography.Xml.EncryptedData> i wypełnij go identyfikatorem URL zaszyfrowanego elementu XML.  Ten identyfikator adresu URL umożliwia osobie odszyfrowanej, że kod XML zawiera zaszyfrowany element.  Możesz użyć pola <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl>, aby określić identyfikator URL.  Element XML w postaci zwykłego tekstu zostanie zastąpiony przez <`EncryptedData`> element hermetyzowany przez ten obiekt <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. Utwórz obiekt <xref:System.Security.Cryptography.Xml.EncryptionMethod>, który jest zainicjowany do identyfikatora URL algorytmu kryptograficznego używanego do generowania klucza sesji.  Przekaż obiekt <xref:System.Security.Cryptography.Xml.EncryptionMethod> do właściwości <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Utwórz obiekt <xref:System.Security.Cryptography.Xml.EncryptedKey>, aby zawierał zaszyfrowany klucz sesji.  Zaszyfruj klucz sesji, Dodaj go do obiektu <xref:System.Security.Cryptography.Xml.EncryptedKey>, a następnie wprowadź nazwę klucza sesji i adres URL identyfikatora klucza.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Utwórz nowy obiekt <xref:System.Security.Cryptography.Xml.DataReference>, który mapuje dane zaszyfrowane do określonego klucza sesji.  Ten opcjonalny krok pozwala łatwo określić, że wiele części dokumentu XML było szyfrowanych za pomocą jednego klucza.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Dodaj zaszyfrowany klucz do obiektu <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Utwórz nowy obiekt <xref:System.Security.Cryptography.Xml.KeyInfo>, aby określić nazwę klucza RSA.  Dodaj go do obiektu <xref:System.Security.Cryptography.Xml.EncryptedData>. Dzięki temu odszyfrowanie umożliwia zidentyfikowanie poprawnego klucza asymetrycznego do użycia podczas odszyfrowywania klucza sesji.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Dodaj dane zaszyfrowanego elementu do obiektu <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Zastąp element z oryginalnego obiektu <xref:System.Xml.XmlDocument> elementem <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Zapisz <xref:System.Xml.XmlDocument> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co skompilowany program.  Zakłada również, że `"test.xml"` zawiera `"creditcard"` elementu.  Można umieścić następujący kod XML w pliku o nazwie `test.xml` i użyć go w tym przykładzie.  
  
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
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
- Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Nigdy nie przechowuj symetrycznego klucza kryptograficznego w postaci zwykłego tekstu lub przesyłaj klucz symetryczny między maszynami w postaci zwykłego tekstu.  Ponadto nigdy nie należy przechowywać ani przenosić klucza prywatnego pary kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat symetrycznych i asymetrycznych kluczy kryptograficznych, zobacz [generowanie kluczy do szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie osadzaj klucza bezpośrednio w kodzie źródłowym.  Klucze osadzone można łatwo odczytywać z zestawu przy użyciu [Ildasm. exe (Il dezasembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub otwierając zestaw w edytorze tekstu, takim jak Notatnik.  
  
 Gdy skończysz korzystać z klucza kryptograficznego, usuń go z pamięci, ustawiając każdy bajt na zero lub wywołując metodę <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> zarządzanej klasy kryptografii.  Klucze kryptograficzne mogą być czasami odczytywane z pamięci przez debuger lub odczytywane z dysku twardego, jeśli lokalizacja pamięci jest stronicowana na dysku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
