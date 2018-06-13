---
title: 'Porady: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da4f65d1510f22e05cef4295a342163bba2d1958
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583383"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Porady: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych
Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML służy do przechowywania lub transportu poufnych XML, nie martwiąc się o łatwo odczytywane dane.  W tym przykładzie kodu odszyfrowuje — element XML przy użyciu algorytmu szyfrowania AES (Advanced Standard), nazywany także Rijndael.  
  
 Aby uzyskać informacje o szyfrowaniu elementu XML za pomocą tej procedury, zobacz [porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 Korzystając z algorytmu symetrycznego, takich jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.  Przykład w tej procedurze założono, że zaszyfrowane XML została zaszyfrowana przy użyciu tego samego klucza, a szyfrowanie i odszyfrowywanie strony wyrażanie zgody na algorytm i klucz do użycia.  W tym przykładzie nie przechowuje ani szyfrowania w zawartości XML zaszyfrowanego klucza AES.  
  
 W tym przykładzie jest przydatne w sytuacjach, w których pojedynczej aplikacji wymaga szyfrowania danych na podstawie klucza sesji, przechowywane w pamięci lub oparte na silną kryptograficznie klucza generowanego na podstawie hasła.  W sytuacjach, w których dwie lub więcej aplikacji musi udostępniać zaszyfrowanych danych XML Rozważ użycie schematu szyfrowania, na podstawie algorytmu asymetrycznego lub certyfikatu X.509.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>Aby odszyfrować element XML przy użyciu klucza symetrycznego  
  
1.  Szyfrowanie — element XML przy użyciu klucza wcześniej wygenerowanych przy użyciu metod opisanych w [porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2.  Znajdź <`EncryptedData`> elementu (określoną przez XML Encryption standard) w <xref:System.Xml.XmlDocument> obiekt zawierający zaszyfrowanego pliku XML i utworzyć nową <xref:System.Xml.XmlElement> obiektu do reprezentowania tego elementu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  Utwórz <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu przez załadowanie nieprzetworzone dane XML z utworzonej wcześniej <xref:System.Xml.XmlElement> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  Utwórz nową <xref:System.Security.Cryptography.Xml.EncryptedXml> obiektu i użyć go do odszyfrowywania danych XML przy użyciu tego samego klucza, który był używany do szyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  Zastąp element zaszyfrowane za pomocą elementu nowo odszyfrowane w postaci zwykłego tekstu w dokumencie XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.  
  
-   Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie przechowują klucza kryptograficznego w postaci zwykłego tekstu lub przenieść klucz między komputerami w postaci zwykłego tekstu.  
  
 Gdy wszystko będzie gotowe za pomocą klucza szyfrowania symetrycznego, wyczyść go z pamięci przez ustawienie każdego bajtu na wartość zero lub wywoływania <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy kryptografii zarządzanych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography.Xml>  
 [Instrukcje: szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
