---
title: 'Instrukcje: Odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych'
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
ms.openlocfilehash: c569407bac247e60075834e67fde9327ce6bc4a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795138"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Instrukcje: Odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML umożliwia przechowywania lub transportu poufnych kod XML, nie martwiąc się o łatwo odczytywanych danych.  Ten przykład kodu odszyfrowuje — element XML przy użyciu algorytmu Advanced Encryption Standard (AES), nazywany także Rijndael.  
  
 Aby dowiedzieć się, jak zaszyfrować element XML przy użyciu tej procedury, zobacz [jak: Szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 Korzystając z algorytmu symetrycznego, takich jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.  Przykład w tej procedurze założono, że zaszyfrowane XML została zaszyfrowana przy użyciu tego samego klucza, a szyfrowanie i odszyfrowywanie strony wyrażanie zgody na algorytm i klucz do użycia.  W tym przykładzie nie przechowuje ani szyfrowania klucza AES, w ramach zaszyfrowanego pliku XML.  
  
 W tym przykładzie jest odpowiednie w sytuacjach, w których pojedynczej aplikacji wymaga szyfrowania danych na podstawie klucza sesji, przechowywane w pamięci lub na podstawie klucza silną kryptograficznie pochodzące z hasła.  W sytuacjach, w której dwa lub więcej aplikacji muszą udostępniać zaszyfrowane dane XML należy wziąć pod uwagę przy użyciu schematu szyfrowania, na podstawie algorytmu asymetrycznego lub certyfikatu X.509.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>Aby odszyfrować element XML przy użyciu klucza symetrycznego  
  
1. Zaszyfrować XML element przy użyciu wcześniej wygenerowany klucz przy użyciu metod opisanych w [jak: Szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2. Znajdź <`EncryptedData`> elementu (określoną przez standard szyfrowanie XML) w <xref:System.Xml.XmlDocument> obiekt, który zawiera zaszyfrowane XML i Utwórz nowy <xref:System.Xml.XmlElement> obiekt reprezentujący ten element.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. Tworzenie <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu przez załadowanie pierwotne dane XML z utworzonej wcześniej <xref:System.Xml.XmlElement> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. Utwórz nową <xref:System.Security.Cryptography.Xml.EncryptedXml> obiektu i użyć go do odszyfrowywania danych XML przy użyciu tego samego klucza, który został użyty do szyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. Zastąp element zaszyfrowanych za pomocą elementu nowo odszyfrowane w postaci zwykłego tekstu w dokumencie XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
- Uwzględnić następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie przechowują klucza kryptograficznego w postaci zwykłego tekstu lub przenieść klucz między maszynami w postaci zwykłego tekstu.  
  
 Po zakończeniu przy użyciu klucza szyfrowania symetrycznego, wyczyść to pole wyboru z pamięci, ustawiając poszczególne bajty do zera lub przez wywołanie <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody klasy zarządzanej kryptografii.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: Szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
