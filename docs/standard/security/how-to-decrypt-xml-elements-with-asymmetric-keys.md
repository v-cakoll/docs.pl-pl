---
title: 'Porady: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 5ed1e2eb2518366da0a57655d7a8691e23f725d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706139"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Porady: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych
Można użyć klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml> do szyfrowania i odszyfrowywania elementu w dokumencie XML.  Szyfrowanie XML jest standardowym sposobem wymiany i przechowywania zaszyfrowanych danych XML bez obaw o dane, które są łatwo odczytywane.  Aby uzyskać więcej informacji na temat standardu szyfrowania XML, zobacz [składnię i przetwarzanie podpisu XML](https://www.w3.org/TR/xmldsig-core/)zalecenia organizacja World Wide Web Consortium (W3C).  
  
 Przykład w tej procedurze odszyfrowuje element XML, który został zaszyfrowany przy użyciu metod opisanych w artykule [jak: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Znajduje <`EncryptedData`> elementu, odszyfrowuje element, a następnie zamienia element na oryginalny element XML w formacie zwykłego tekstu.  
  
 Ten przykład odszyfrowuje element XML przy użyciu dwóch kluczy.  Pobiera wcześniej wygenerowany klucz prywatny RSA z kontenera kluczy, a następnie używa klucza RSA do odszyfrowania klucza sesji przechowywanego w <`EncryptedKey`> elementu <`EncryptedData`>.  W przykładzie zostanie użyty klucz sesji do odszyfrowania elementu XML.  
  
 Ten przykład jest odpowiedni dla sytuacji, w których wiele aplikacji musi udostępniać zaszyfrowane dane lub w przypadku, gdy aplikacja ma zapisywać zaszyfrowane dane między uruchomionymi danymi.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Aby odszyfrować element XML za pomocą klucza asymetrycznego  
  
1. Utwórz obiekt <xref:System.Security.Cryptography.CspParameters> i określ nazwę kontenera kluczy.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Pobierz wcześniej wygenerowany klucz asymetryczny z kontenera przy użyciu obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Klucz jest automatycznie pobierany z kontenera kluczy podczas przekazywania obiektu <xref:System.Security.Cryptography.CspParameters> do konstruktora <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Utwórz nowy obiekt <xref:System.Security.Cryptography.Xml.EncryptedXml> do odszyfrowania dokumentu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. Dodaj mapowanie klucza/nazwy, aby skojarzyć klucz RSA z elementem w dokumencie, który ma zostać odszyfrowany.  Należy użyć tej samej nazwy klucza, który został użyty podczas szyfrowania dokumentu.  Należy zauważyć, że ta nazwa jest oddzielona od nazwy używanej do identyfikowania klucza w kontenerze kluczy określonym w kroku 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. Wywołaj metodę <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>, aby odszyfrować <`EncryptedData`> elementu.  Ta metoda powoduje odszyfrowanie klucza sesji przy użyciu klucza RSA i automatyczne odszyfrowanie elementu XML przy użyciu klucza sesji.  Automatycznie zastępuje <`EncryptedData`elementu > pierwotnym tekstem.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. Zapisz dokument XML.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `test.xml` istnieje w tym samym katalogu co skompilowany program.  Zakłada również, że `test.xml` zawiera element XML, który został zaszyfrowany przy użyciu technik opisanych w artykule [jak: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
- Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Nigdy nie przechowuj symetrycznego klucza kryptograficznego w postaci zwykłego tekstu lub przesyłaj klucz symetryczny między maszynami w postaci zwykłego tekstu.  Ponadto nigdy nie należy przechowywać ani przenosić klucza prywatnego pary kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat symetrycznych i asymetrycznych kluczy kryptograficznych, zobacz [generowanie kluczy do szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie osadzaj klucza bezpośrednio w kodzie źródłowym.  Klucze osadzone można łatwo odczytywać z zestawu przy użyciu [Ildasm. exe (Il dezasembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub otwierając zestaw w edytorze tekstu, takim jak Notatnik.  
  
 Gdy skończysz korzystać z klucza kryptograficznego, usuń go z pamięci, ustawiając każdy bajt na zero lub wywołując metodę <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> zarządzanej klasy kryptografii.  Klucze kryptograficzne mogą być czasami odczytywane z pamięci przez debuger lub odczytywane z dysku twardego, jeśli lokalizacja pamięci jest stronicowana na dysku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
