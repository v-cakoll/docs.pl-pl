---
title: Obiekty rozszerzeń XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25c9c1c81db0bb6775aa9226318d7ec726a93e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924937"
---
# <a name="xslt-extension-objects"></a>Obiekty rozszerzeń XSLT
Obiekty rozszerzeń służą do rozszerzania funkcjonalności arkuszy stylów. Obiekty rozszerzeń są obsługiwane przez <xref:System.Xml.Xsl.XsltArgumentList> klasę.  
  
 Poniżej przedstawiono zalety użycia obiektu rozszerzenia zamiast skryptu osadzonego:  
  
- Zapewnia lepszą hermetyzację i ponowne użycie klas.  
  
- Zezwala na mniejsze i łatwiejsze w obsłudze arkusze stylów.  
  
 Obiekty rozszerzeń XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> obiektu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> za pomocą metody. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem rozszerzenia w tym czasie.  
  
> [!NOTE]
> Zestaw uprawnień FullTrust jest wymagany do wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu](../../../../docs/framework/misc/code-access-security.md) i [nazwane zestawy uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Typy danych zwracane z obiektów rozszerzeń to jeden z czterech `number`podstawowych typów danych XPath `Boolean`, `string`,, i `node set`.  
  
 Każda metoda, która jest zdefiniowana za `params` pomocą słowa kluczowego, umożliwiająca nieokreśloną liczbę parametrów do przesłania, nie jest obecnie obsługiwana <xref:System.Xml.Xsl.XslCompiledTransform> przez klasę. Arkusze stylów XSLT używające dowolnej metody zdefiniowanej za `params` pomocą słowa kluczowego nie będą działały prawidłowo. Aby uzyskać szczegółowe informacje, zobacz [params](../../../csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Aby użyć obiektu rozszerzenia XSLT  
  
1. Utwórz obiekt i Dodaj obiekt rozszerzenia za pomocą <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. <xref:System.Xml.Xsl.XsltArgumentList>  
  
2. Wywołaj obiekt rozszerzenia z arkusza stylów.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList> Przekaż obiekt<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> do metody.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Zagadnienia dotyczące bezpieczeństwa danych XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
