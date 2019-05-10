---
title: 'Instrukcje: Odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c1891bf91095a5c09257b795c66e96dbc2bf69d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64653885"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Instrukcje: Odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw do szyfrowania i odszyfrowywania elementu w dokumencie XML.  Szyfrowanie XML to standardowy sposób wymiany ani nie przechowują zaszyfrowane dane XML, nie martwiąc się o łatwo odczytywanych danych.  Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz zalecenia konsorcjum World Wide Web Consortium (W3C) [składni podpisu XML i przetwarzanie](https://www.w3.org/TR/xmldsig-core/).  
  
 Przykład w tej procedurze odszyfrowuje element XML, która została zaszyfrowana przy użyciu metod opisanych w [jak: Szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Znajdzie <`EncryptedData`> element, odszyfrowuje elementu i następnie zamienia element w oryginalnym elemencie XML zwykłego tekstu.  
  
 W tym przykładzie odszyfrowuje elementu XML za pomocą dwóch kluczy.  Pobiera wcześniej wygenerowany klucz prywatny RSA z kontenera kluczy, a następnie używa klucza RSA do odszyfrowania klucza sesji przechowywany w <`EncryptedKey`> elementu <`EncryptedData`> element.  Przykład następnie używa klucza sesji, aby odszyfrować XML element.  
  
 W tym przykładzie jest odpowiednie w sytuacji, gdy wiele aplikacji jest współużytkowany zaszyfrowanych danych lub gdy aplikacja musi zapisać zaszyfrowane dane między godzinami, które działa.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Aby odszyfrować XML element przy użyciu klucza asymetrycznego  
  
1. Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera kluczy.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Pobrać wcześniej wygenerowany klucz asymetryczny z kontenera przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu.  Klucz jest automatycznie pobierany z kontenera kluczy, jeśli przekazujesz <xref:System.Security.Cryptography.CspParameters> obiekt <xref:System.Security.Cryptography.RSACryptoServiceProvider> konstruktora.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Utwórz nową <xref:System.Security.Cryptography.Xml.EncryptedXml> obiektu do odszyfrowania dokumentu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. Dodaj mapowanie klucz/nazwę do skojarzenia klucza RSA z elementem w dokumencie, który powinien być odszyfrowane.  Należy użyć takiej samej nazwie klucz który jest używany podczas szyfrowania dokumentu.  Należy pamiętać, że ta nazwa jest oddzielona od Nazwa służąca do identyfikacji klucza w kontenerze kluczy określonym w kroku 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. Wywołaj <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metodę, aby odszyfrować <`EncryptedData`> element.  Ta metoda używa klucza RSA do odszyfrowania klucza sesji i automatycznie używa klucza sesji, aby odszyfrować XML element.  Automatycznie zastępuje <`EncryptedData`> element z oryginalnej postaci zwykłego tekstu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. Zapisz dokument XML.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie założono, że plik o nazwie `test.xml` istnieje w tym samym katalogu co skompilowanego programu.  Przyjęto również założenie, że `test.xml` zawiera element XML, która została zaszyfrowana przy użyciu metod opisanych w [jak: Szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
- Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie przechowują symetrycznego klucza kryptograficznego w postaci zwykłego tekstu lub przenieść klucz symetryczny między maszynami w postaci zwykłego tekstu.  Ponadto nigdy nie magazynu lub transfer klucza prywatnego pary kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat klucze szyfrowania symetrycznego i asymetrycznego zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie można osadzić klucza bezpośrednio w kodzie źródłowym.  Osadzone klucze można łatwo odczytać z zestawu przy użyciu [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstów, takiego jak Notatnik.  
  
 Po zakończeniu za pomocą klucza kryptograficznego, wyczyść to pole wyboru z pamięci, ustawiając poszczególne bajty do zera lub przez wywołanie <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy zarządzanej kryptografii.  Klucze kryptograficzne czasami można odczytać pamięci przez debuger lub odczytu z dysku twardego, jeśli lokalizacja pamięci jest stronicowanej na dysku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: Szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
