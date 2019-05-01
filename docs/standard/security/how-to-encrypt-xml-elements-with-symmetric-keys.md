---
title: 'Instrukcje: Szyfrowanie elementów XML przy użyciu kluczy symetrycznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2268dc813d6f12b69bee99dd07f8f4431b12a283
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795086"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Instrukcje: Szyfrowanie elementów XML przy użyciu kluczy symetrycznych
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML umożliwia przechowywania lub transportu poufnych kod XML, nie martwiąc się o łatwo odczytywanych danych.  Ta procedura odszyfrowuje — element XML przy użyciu algorytmu Advanced Encryption Standard (AES), nazywany także Rijndael.  
  
 Aby uzyskać informacje o tym, jak można odszyfrować element XML, która została zaszyfrowana przy użyciu tej procedury, zobacz [jak: Odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 Korzystając z algorytmu symetrycznego, takich jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.  Przykład w tej procedurze przyjęto założenie, zaszyfrowanego pliku XML zostaną odszyfrowane przy użyciu tego samego klucza, i że szyfrowanie i odszyfrowywanie strony zgody na algorytm i klucz do użycia.  W tym przykładzie nie przechowuje ani szyfrowania klucza AES, w ramach zaszyfrowanego pliku XML.  
  
 W tym przykładzie jest odpowiednie w sytuacjach, w których pojedynczej aplikacji wymaga szyfrowania danych na podstawie klucza sesji, przechowywane w pamięci lub na podstawie klucza silną kryptograficznie pochodzące z hasła.  W sytuacjach, w której dwa lub więcej aplikacji muszą udostępniać zaszyfrowane dane XML należy wziąć pod uwagę przy użyciu schematu szyfrowania, na podstawie algorytmu asymetrycznego lub certyfikatu X.509.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>Aby zaszyfrować element XML przy użyciu klucza symetrycznego  
  
1. Generuj klucz symetryczny za pomocą <xref:System.Security.Cryptography.RijndaelManaged> klasy.  Ten klucz będzie używany do szyfrowania elementu XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. Utwórz <xref:System.Xml.XmlDocument> obiektu, ładując plik XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera element XML do szyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. Znajdź element określony w <xref:System.Xml.XmlDocument> obiektu i Utwórz nowy <xref:System.Xml.XmlElement> obiekt reprezentujący element, który chcesz zaszyfrować.  W tym przykładzie `"creditcard"` elementu są szyfrowane.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i jej użyciu można zaszyfrować <xref:System.Xml.XmlElement> przy użyciu klucza symetrycznego.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> Metoda zwraca zaszyfrowany element jako tablicę bajtów zaszyfrowanych.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. Konstruowania <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu i wypełnianie jej identyfikator adresu URL elementu szyfrowanie XML.  Ten identyfikator URL umożliwia odszyfrowywanie innych firm, dowiedzieć się, że plik XML zawiera element zaszyfrowane.  Możesz użyć <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> pola, aby określić identyfikator URL.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. Utwórz <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt, który jest inicjowany na identyfikator URL algorytm kryptograficzny używany do generowania klucza.  Przekaż <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> właściwości.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. Dodaj element zaszyfrowane dane <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. Zastąp element z oryginalnym <xref:System.Xml.XmlDocument> obiekt z <xref:System.Security.Cryptography.Xml.EncryptedData> elementu.  
  
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
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
- Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie przechowują klucza kryptograficznego w postaci zwykłego tekstu lub przenieść klucz między maszynami w postaci zwykłego tekstu.  Zamiast tego należy użyć bezpieczny kontener klucza do przechowywania kluczy kryptograficznych.  
  
 Po zakończeniu za pomocą klucza kryptograficznego, wyczyść to pole wyboru z pamięci, ustawiając poszczególne bajty do zera lub przez wywołanie <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy zarządzanej kryptografii.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: Odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
