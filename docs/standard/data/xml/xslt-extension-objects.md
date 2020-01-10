---
title: Obiekty rozszerzeń XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: 6ad5b5140239ad7dc0ad72e65d10af744dfbd784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709715"
---
# <a name="xslt-extension-objects"></a>Obiekty rozszerzeń XSLT
Obiekty rozszerzeń służą do rozszerzania funkcjonalności arkuszy stylów. Obiekty rozszerzeń są obsługiwane przez klasę <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Poniżej przedstawiono zalety użycia obiektu rozszerzenia zamiast skryptu osadzonego:  
  
- Zapewnia lepszą hermetyzację i ponowne użycie klas.  
  
- Zezwala na mniejsze i łatwiejsze w obsłudze arkusze stylów.  
  
 Obiekty rozszerzeń XSLT są dodawane do obiektu <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem rozszerzenia w tym czasie.  
  
> [!NOTE]
> Aby wywołać metodę <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>, wymagany jest zestaw uprawnień FullTrust. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu](../../../../docs/framework/misc/code-access-security.md) i [nazwane zestawy uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Typy danych zwracane z obiektów rozszerzeń to jeden z czterech podstawowych typów danych XPath `number`, `string`, `Boolean`i `node set`.  
  
 Dowolna metoda, która jest zdefiniowana za pomocą słowa kluczowego `params`, która umożliwia przekazanie nieokreślonej liczby parametrów, nie jest obecnie obsługiwana przez klasę <xref:System.Xml.Xsl.XslCompiledTransform>. Arkusze stylów XSLT używające dowolnej metody zdefiniowanej za pomocą słowa kluczowego `params` nie będą działały prawidłowo. Aby uzyskać szczegółowe informacje, zobacz [params](../../../csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Aby użyć obiektu rozszerzenia XSLT  
  
1. Utwórz obiekt <xref:System.Xml.Xsl.XsltArgumentList> i Dodaj obiekt rozszerzenia przy użyciu metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2. Wywołaj obiekt rozszerzenia z arkusza stylów.  
  
3. Przekaż obiekt <xref:System.Xml.Xsl.XsltArgumentList> do metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Zagadnienia dotyczące bezpieczeństwa danych XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
