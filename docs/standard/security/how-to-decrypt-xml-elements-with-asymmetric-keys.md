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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 329569ea148542ff596057d9eb9efe2e95768341
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589074"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Porady: odszyfrowywanie elementów XML przy użyciu kluczy asymetrycznych
Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw do szyfrowania i odszyfrowywania element w dokumencie XML.  Szyfrowanie XML jest standardowym sposobem exchange lub przechowywania zaszyfrowanych danych XML, nie martwiąc się o łatwo odczytywane dane.  Aby uzyskać więcej informacji na temat standardowych szyfrowanie XML, zobacz zalecenia konsorcjum World Wide Web (W3C) [składnia XML podpisu i przetwarzania](https://www.w3.org/TR/xmldsig-core/).  
  
 Przykład w tej procedurze odszyfrowuje element XML, która została zaszyfrowana przy użyciu metod opisanych w [porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Znajdzie <`EncryptedData`> elementu odszyfrowuje elementu, a następnie zastępuje element oryginalny element XML w postaci zwykłego tekstu.  
  
 W tym przykładzie odszyfrowuje elementu XML za pomocą dwóch kluczy.  Go pobiera wcześniej wygenerowanych prywatnego klucza RSA z kontenera kluczy, a następnie używa kluczy RSA do odszyfrowania klucza sesji w <`EncryptedKey`> elementu <`EncryptedData`> elementu.  W przykładzie użyto następnie klucza sesji do odszyfrowania elementu XML.  
  
 W tym przykładzie jest przydatne w sytuacjach, gdy wiele aplikacji muszą współużytkować zaszyfrowanych danych lub gdy aplikacja ma zapisać zaszyfrowanych danych w okresie, które działa między.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Aby odszyfrować za pomocą klucza asymetrycznego — element XML  
  
1.  Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera kluczy.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Pobrać wcześniej wygenerowanych klucza asymetrycznego z kontenera przy użyciu <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu.  Klucz jest automatycznie pobierany z kontenera kluczy podczas przekazywania <xref:System.Security.Cryptography.CspParameters> do obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> konstruktora.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Utwórz nową <xref:System.Security.Cryptography.Xml.EncryptedXml> obiektu do odszyfrowania dokumentu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  Dodaj mapowanie nazwa/klucza do skojarzenia z elementem w tym dokumencie, który powinien być odszyfrowane kluczy RSA.  Należy użyć tej samej nazwy dla klucza, który został użyty podczas szyfrowania dokumentu.  Należy pamiętać, że ta nazwa jest oddzielony od Nazwa używana do identyfikacji klucza w kontenerze klucza podanego w kroku 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  Wywołanie <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> metody do odszyfrowania <`EncryptedData`> elementu.  Ta metoda używa klucza RSA do odszyfrowania klucza sesji i automatycznie używa klucza sesji do odszyfrowania elementu XML.  Automatycznie zastępuje <`EncryptedData`> elementu z oryginalnego zwykłego tekstu.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  Zapisz dokument XML.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `test.xml` istnieje w tym samym katalogu co program skompilowany.  Założono również, że `test.xml` zawiera element XML, która została zaszyfrowana przy użyciu metod opisanych w [porady: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.  
  
-   Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie przechowują symetrycznego klucza kryptograficznego w postaci zwykłego tekstu lub transfer klucza symetrycznego między komputerami w postaci zwykłego tekstu.  Ponadto nigdy nie magazynu lub przenieść klucz prywatny para kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat symetrycznego i asymetrycznego kluczy kryptograficznych, zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie osadzaj klucza bezpośrednio w kodzie źródłowym.  Osadzony kluczy można łatwo odczytać z zestawu przy użyciu [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstu, takiego jak Notatnik.  
  
 Gdy wszystko będzie gotowe za pomocą klucza kryptograficznego, wyczyść go z pamięci przez ustawienie każdego bajtu na wartość zero lub wywoływania <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy kryptografii zarządzanych.  Klucze kryptograficzne czasami może odczytywać pamięci przez debuger lub odczytu z dysku twardego, jeśli lokalizacji pamięci jest stronicowana na dysk.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography.Xml>  
 [Instrukcje: szyfrowanie elementów XML przy użyciu kluczy asymetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
