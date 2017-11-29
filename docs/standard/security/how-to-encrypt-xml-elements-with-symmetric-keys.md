---
title: "Porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych"
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
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56bce016d16b9bf12446ba7b31725d49c48988a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych
Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML służy do przechowywania lub transportu poufnych XML, nie martwiąc się o łatwo odczytywane dane.  Ta procedura odszyfrowuje — element XML przy użyciu algorytmu szyfrowania AES (Advanced Standard), nazywany także Rijndael.  
  
 Aby uzyskać informacje o tym, jak można odszyfrować element XML, która została zaszyfrowana przy użyciu tej procedury, zobacz [porady: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 Korzystając z algorytmu symetrycznego, takich jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.  Przykład w tej procedurze przyjęto założenie, że zostaną odszyfrowane przy użyciu tego samego klucza zaszyfrowanego pliku XML i że szyfrowanie i odszyfrowywanie strony wyrażanie zgody na algorytm i klucz do użycia.  W tym przykładzie nie przechowuje ani szyfrowania w zawartości XML zaszyfrowanego klucza AES.  
  
 W tym przykładzie jest przydatne w sytuacjach, w których pojedynczej aplikacji wymaga szyfrowania danych na podstawie klucza sesji, przechowywane w pamięci lub oparte na silną kryptograficznie klucza generowanego na podstawie hasła.  W sytuacjach, w których dwie lub więcej aplikacji musi udostępniać zaszyfrowanych danych XML Rozważ użycie schematu szyfrowania, na podstawie algorytmu asymetrycznego lub certyfikatu X.509.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>Aby zaszyfrować element XML przy użyciu klucza symetrycznego  
  
1.  Generowanie klucza symetrycznego użyciu <xref:System.Security.Cryptography.RijndaelManaged> klasy.  Ten klucz będzie używany do szyfrowania elementu XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2.  Utwórz <xref:System.Xml.XmlDocument> obiektu przez ładowanie pliku XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3.  Znajdź element określony w <xref:System.Xml.XmlDocument> obiekt i utworzyć nową <xref:System.Xml.XmlElement> obiekt reprezentujący element, który chcesz zaszyfrować.  W tym przykładzie `"creditcard"` element jest zaszyfrowany.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4.  Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i jej użyciu można zaszyfrować <xref:System.Xml.XmlElement> przy użyciu klucza symetrycznego.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda zwraca zaszyfrowany element jako tablicę bajtów zaszyfrowanych.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5.  Utworzyć <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu i wypełnić ją identyfikator adresu URL elementu XML szyfrowania.  Ten identyfikator URL umożliwia odszyfrowywania strona wiedzieć, że plik XML zawiera zaszyfrowany element.  Można użyć <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> Aby określić identyfikator adresu URL.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6.  Utwórz <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt, który jest inicjowana na adres URL identyfikator algorytmu kryptograficznego używanego do generowania klucza.  Przekaż <xref:System.Security.Cryptography.Xml.EncryptionMethod> do obiektu <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> właściwości.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7.  Dodaj element zaszyfrowane dane do <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8.  Zastąp element z oryginalnego <xref:System.Xml.XmlDocument> obiekt z <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a>Przykład  
  
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
 Nigdy nie przechowują klucza kryptograficznego w postaci zwykłego tekstu lub przenieść klucz między komputerami w postaci zwykłego tekstu.  W zamian użyj bezpiecznego kontenera klucza do przechowywania kluczy kryptograficznych.  
  
 Gdy wszystko będzie gotowe za pomocą klucza kryptograficznego, wyczyść go z pamięci przez ustawienie każdego bajtu na wartość zero lub wywoływania <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy kryptografii zarządzanych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography.Xml>  
 [Porady: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
