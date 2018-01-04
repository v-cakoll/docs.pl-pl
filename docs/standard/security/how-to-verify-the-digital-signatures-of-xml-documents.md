---
title: "Porady: sprawdzanie podpisów cyfrowych w dokumentach XML"
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
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c45ffbffd5eae812dbd9703ffde4423c94581234
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Porady: sprawdzanie podpisów cyfrowych w dokumentach XML
Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby sprawdzić, dane XML podpisane za pomocą podpisu cyfrowego.  Podpisy cyfrowe XML (XMLDSIG) pozwalają sprawdzić, czy dane nie została zmodyfikowana po podpisaniu.  Aby uzyskać więcej informacji na temat XMLDSIG standardowe zobacz specyfikację sieci World Wide Web konsorcjum W3C w http://www.w3.org/TR/xmldsig-core/.  
  
 Przykład kodu w tej procedurze pokazano, jak można zweryfikować podpisu cyfrowego XML zawarte w <`Signature`> elementu.  Przykład pobiera klucza publicznego RSA z kontenera kluczy, a następnie używa klucza można zweryfikować podpisu.  
  
 Aby uzyskać informacje o tym, jak utworzyć podpis cyfrowy, który można sprawdzić za pomocą tej metody, zobacz [porady: znak dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Aby sprawdzić podpis cyfrowy dokumentu XML  
  
1.  Aby sprawdzić dokumentu, należy użyć tego samego klucza asymetrycznego, który został użyty do podpisywania.  Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera klucza, który został użyty do podpisywania.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  Pobrać publicznego klucza za pomocą <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  Klucz jest ładowane automatycznie przy użyciu kontenera kluczy według nazwy podczas przekazywania <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  Utwórz <xref:System.Xml.XmlDocument> obiektu przez ładowanie pliku XML z dysku.  <xref:System.Xml.XmlDocument> Obiekt zawiera podpisanego dokumentu XML można zweryfikować.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  Utwórz nową <xref:System.Security.Cryptography.Xml.SignedXml> obiektu i przekazać <xref:System.Xml.XmlDocument> obiektu do niego.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  Znajdź <`signature`> element i utworzyć nową <xref:System.Xml.XmlNodeList> obiektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  Ładowanie pliku XML pierwszego <`signature`> element do <xref:System.Security.Cryptography.Xml.SignedXml> obiektu.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  Sprawdzanie podpisu przy użyciu <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> — metoda i klucza publicznego RSA.  Ta metoda zwraca wartość logiczną, która wskazuje powodzenie lub niepowodzenie.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co program skompilowany.  `"test.xml"` Pliku muszą być podpisane za pomocą metod opisanych w [porady: znak dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.  
  
-   Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nigdy nie magazynu lub przenieść klucz prywatny para kluczy asymetrycznych w postaci zwykłego tekstu.  Aby uzyskać więcej informacji na temat symetrycznego i asymetrycznego kluczy kryptograficznych, zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nigdy nie osadzaj klucza prywatnego bezpośrednio w kodzie źródłowym.  Osadzony kluczy można łatwo odczytać z zestawu za pomocą [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstu, takiego jak Notatnik.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography.Xml>  
 [Instrukcje: podpisywanie dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
