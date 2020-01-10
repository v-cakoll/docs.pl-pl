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
ms.openlocfilehash: fd377cd470d361f5a46c662ab37780713a2d3804
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706126"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Porady: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych
Możesz użyć klas w przestrzeni nazw <xref:System.Security.Cryptography.Xml>, aby zaszyfrować element w dokumencie XML.  Szyfrowanie XML umożliwia przechowywanie i transportowanie poufnego kodu XML bez obaw o dane, które są łatwo odczytywane.  Ten przykład kodu odszyfrowuje element XML przy użyciu algorytmu Advanced Encryption Standard (AES), znanego również jako Rijndael.  
  
 Informacje o sposobie szyfrowania elementu XML przy użyciu tej procedury znajdują się w temacie [How to: szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 W przypadku używania algorytmu symetrycznego, takiego jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.  W przykładzie tej procedury przyjęto założenie, że zaszyfrowany kod XML został zaszyfrowany przy użyciu tego samego klucza, a strony szyfrujące i odszyfrowuje zgadzają się na algorytm i klucz do użycia.  Ten przykład nie przechowuje ani nie szyfruje klucza AES w zaszyfrowanym formacie XML.  
  
 Ten przykład jest odpowiedni dla sytuacji, w których pojedyncza aplikacja musi szyfrować dane na podstawie klucza sesji przechowywanego w pamięci lub na podstawie kryptograficznego klucza silnego pochodzącego z hasła.  W przypadku, gdy co najmniej dwie aplikacje muszą udostępniać zaszyfrowane dane XML, należy rozważyć użycie schematu szyfrowania na podstawie algorytmu asymetrycznego lub certyfikatu X. 509.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>Aby odszyfrować element XML przy użyciu klucza symetrycznego  
  
1. Szyfruj element XML z wcześniej wygenerowanym kluczem przy użyciu technik opisanych w artykule [How to: Szyfruj elementy XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2. Znajdź <`EncryptedData`> element (zdefiniowany przez standard szyfrowania XML) w obiekcie <xref:System.Xml.XmlDocument>, który zawiera zaszyfrowany kod XML i Utwórz nowy obiekt <xref:System.Xml.XmlElement> do reprezentowania tego elementu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. Utwórz obiekt <xref:System.Security.Cryptography.Xml.EncryptedData>, ładując pierwotne dane XML z wcześniej utworzonego obiektu <xref:System.Xml.XmlElement>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. Utwórz nowy obiekt <xref:System.Security.Cryptography.Xml.EncryptedXml> i użyj go do odszyfrowania danych XML przy użyciu tego samego klucza, który był używany do szyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. Zastąp zaszyfrowany element nowo odszyfrowanym tekstem w dokumencie XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll`.  
  
- Uwzględnij następujące przestrzenie nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Nie przechowuj klucza kryptograficznego w postaci zwykłego tekstu lub przesyłaj klucz między maszynami w postaci zwykłego tekstu.  
  
 Po zakończeniu korzystania z symetrycznego klucza kryptograficznego Wyczyść go z pamięci, ustawiając każdy bajt na zero lub wywołując metodę <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> zarządzanej klasy kryptografii.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: szyfrowanie elementów XML przy użyciu kluczy symetrycznych](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
