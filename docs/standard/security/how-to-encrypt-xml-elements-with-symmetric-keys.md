---
title: 'Porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych'
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
ms.openlocfilehash: 1ad75b7f36130a9f3acad97f724406650a7fdb68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277326"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Porady: szyfrowanie elementów XML przy użyciu kluczy symetrycznych
Można użyć klas w <xref:System.Security.Cryptography.Xml> przestrzeni nazw do szyfrowania elementu w dokumencie XML.  Szyfrowanie XML umożliwia przechowywanie i transportowanie poufnego kodu XML bez obaw o dane, które są łatwo odczytywane.  Ta procedura służy do szyfrowania elementu XML przy użyciu algorytmu Advanced Encryption Standard (AES), znanego również jako Rijndael.  
  
 Informacje o sposobie odszyfrowywania elementu XML, który został zaszyfrowany przy użyciu tej procedury, można znaleźć w temacie [How to: Deszyfruj elementy XML przy użyciu kluczy symetrycznych](how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 W przypadku używania algorytmu symetrycznego, takiego jak AES do szyfrowania danych XML, należy użyć tego samego klucza do szyfrowania i odszyfrowywania danych XML.  W przykładzie tej procedury przyjęto założenie, że zaszyfrowany kod XML zostanie odszyfrowany przy użyciu tego samego klucza, a strony szyfrujące i odszyfrowuje zgadzają się na algorytm i klucz do użycia.  Ten przykład nie przechowuje ani nie szyfruje klucza AES w zaszyfrowanym formacie XML.  
  
 Ten przykład jest odpowiedni dla sytuacji, w których pojedyncza aplikacja musi szyfrować dane na podstawie klucza sesji przechowywanego w pamięci lub na podstawie kryptograficznego klucza silnego pochodzącego z hasła.  W przypadku, gdy co najmniej dwie aplikacje muszą udostępniać zaszyfrowane dane XML, należy rozważyć użycie schematu szyfrowania na podstawie algorytmu asymetrycznego lub certyfikatu X. 509.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>Aby zaszyfrować element XML przy użyciu klucza symetrycznego  
  
1. Generuj klucz symetryczny przy użyciu <xref:System.Security.Cryptography.RijndaelManaged> klasy.  Ten klucz będzie używany do szyfrowania elementu XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. Utwórz <xref:System.Xml.XmlDocument> obiekt przez załadowanie pliku XML z dysku.  <xref:System.Xml.XmlDocument>Obiekt zawiera element XML do zaszyfrowania.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. Znajdź określony element w <xref:System.Xml.XmlDocument> obiekcie i Utwórz nowy <xref:System.Xml.XmlElement> obiekt do reprezentowania elementu, który chcesz zaszyfrować.  W tym przykładzie `"creditcard"` element jest szyfrowany.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. Utwórz nowe wystąpienie <xref:System.Security.Cryptography.Xml.EncryptedXml> klasy i użyj go do zaszyfrowania <xref:System.Xml.XmlElement> przy użyciu klucza symetrycznego.  <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A>Metoda zwraca zaszyfrowany element jako tablicę szyfrowanych bajtów.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. Utwórz <xref:System.Security.Cryptography.Xml.EncryptedData> obiekt i wypełnij go identyfikatorem URL elementu szyfrowania XML.  Ten identyfikator adresu URL umożliwia osobie odszyfrowanej, że kod XML zawiera zaszyfrowany element.  Możesz użyć pola, <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> Aby określić identyfikator URL.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. Utwórz <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt, który jest zainicjowany do identyfikatora URL algorytmu kryptograficznego użytego do wygenerowania klucza.  Przekaż <xref:System.Security.Cryptography.Xml.EncryptionMethod> obiekt do <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> właściwości.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. Dodaj dane zaszyfrowanego elementu do <xref:System.Security.Cryptography.Xml.EncryptedData> obiektu.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. Zamień element z oryginalnego obiektu na <xref:System.Xml.XmlDocument> <xref:System.Security.Cryptography.Xml.EncryptedData> element.  
  
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
  
- Aby skompilować ten przykład, należy dołączyć odwołanie do `System.Security.dll` .  
  
- Uwzględnij następujące przestrzenie nazw: <xref:System.Xml> , <xref:System.Security.Cryptography> , i <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie przechowuj klucza kryptograficznego w postaci zwykłego tekstu lub przesyłaj klucz między maszynami w postaci zwykłego tekstu.  Zamiast tego należy użyć bezpiecznego kontenera kluczy do przechowywania kluczy kryptograficznych.  
  
 Gdy skończysz korzystać z klucza kryptograficznego, usuń go z pamięci przez ustawienie każdego bajtu na zero lub przez wywołanie <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> metody zarządzanej klasy kryptografii.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography.Xml>
- [Instrukcje: odszyfrowywanie elementów XML przy użyciu kluczy symetrycznych](how-to-decrypt-xml-elements-with-symmetric-keys.md)
