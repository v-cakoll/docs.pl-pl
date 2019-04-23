---
title: Obiekty rozszerzeń XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b10ab992089e2e9280162c4cd2273bc1d9dc35e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320421"
---
# <a name="xslt-extension-objects"></a>Obiekty rozszerzeń XSLT
Obiekty rozszerzeń są używane do rozszerzania funkcji arkuszy stylów. Obiekty rozszerzeń są obsługiwane przez <xref:System.Xml.Xsl.XsltArgumentList> klasy.  
  
 Poniżej przedstawiono zalety korzystania z obiektu rozszerzenia zamiast osadzonych skryptów:  
  
-   Zapewnia lepszą hermetyzacji i ponowne użycie klas.  
  
-   Umożliwia arkusze stylów była mniejsza i będzie łatwiejszy w utrzymaniu.  
  
 Obiekty rozszerzeń XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektu rozszerzenia, w tym czasie.  
  
> [!NOTE]
>  Zestaw uprawnień FullTrust jest wymagane do wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu](../../../../docs/framework/misc/code-access-security.md) i [nazwanych zestawów uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Typy danych zwróciło obiekty rozszerzeń są jedną z czterech podstawowych XPath typy danych `number`, `string`, `Boolean`, i `node set`.  
  
 Wszystkie metody, która jest zdefiniowana za pomocą `params` — słowo kluczowe, które dopuszcza nieokreślonej liczby parametrów do przekazania, nie jest obsługiwana przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Arkuszy stylów XSLT, które wykorzystują wszelkie metody zdefiniowane przy użyciu `params` — słowo kluczowe nie będą działać poprawnie. Aby uzyskać więcej informacji, zobacz [params](~/docs/csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Używanie obiektu rozszerzenia XSLT  
  
1. Tworzenie <xref:System.Xml.Xsl.XsltArgumentList> obiektu i dodać za pomocą obiektu rozszerzenia <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.  
  
2. Wywołanie obiektu rozszerzenia z arkusza stylów.  
  
3. Przekaż <xref:System.Xml.Xsl.XsltArgumentList> obiekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Zagadnienia dotyczące bezpieczeństwa danych XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
