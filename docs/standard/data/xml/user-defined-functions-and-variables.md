---
title: Funkcje i zmienne zdefiniowane przez użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
ms.openlocfilehash: 7040c2ccf6e3bfc6efcbec3505c633c6c3c6508f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710066"
---
# <a name="user-defined-functions-and-variables"></a>Funkcje i zmienne zdefiniowane przez użytkownika
<xref:System.Xml.XPath.XPathNavigator> Klasa zawiera zestaw metod, które są używane do współpracy z <xref:System.Xml.XPath.XPathDocument> danymi. Można uzupełnić standardowe funkcje XPath przez implementację funkcji i zmiennych rozszerzeń do użycia przez wyrażenia zapytań XPath. <xref:System.Xml.XPath.XPathExpression.SetContext%2A> Metoda może akceptować kontekst zdefiniowany przez użytkownika, który <xref:System.Xml.Xsl.XsltContext>pochodzi od. Funkcje zdefiniowane przez użytkownika są rozwiązywane przez kontekst niestandardowy.  
  
 Funkcje i zmienne rozszerzeń mogą być przydatne w zapobieganiu atakom przy iniekcji kodu XML. W tych scenariuszach dane wejściowe użytkownika są przypisywane do zmiennych niestandardowych i przetwarzane przez funkcje rozszerzenia, nie jako pierwotne dane wejściowe połączone z instrukcjami przetwarzania. Funkcje rozszerzenia i zmienne zawierają dane wejściowe użytkownika, dzięki czemu działają tylko na danych XML, które są przewidziane przez projektanta.  
  
 Aby użyć rozszerzeń implementujących klasę niestandardową <xref:System.Xml.Xsl.XsltContext> wraz z interfejsami <xref:System.Xml.Xsl.IXsltContextVariable> <xref:System.Xml.Xsl.IXsltContextFunction> i obsługującymi funkcje rozszerzeń i zmienne. <xref:System.Xml.XPath.XPathExpression> Dodaje <xref:System.Xml.Xsl.XsltArgumentList> do niestandardowego <xref:System.Xml.Xsl.XsltContext>dane wejściowe użytkownika.  
  
 <xref:System.Xml.XPath.XPathExpression> Reprezentuje skompilowane zapytanie, które <xref:System.Xml.XPath.XPathNavigator> używa do znajdowania i przetwarzania węzłów identyfikowanych przez wyrażenie.  
  
 W poniższym przykładzie przedstawiono implementację niestandardowej klasy kontekstu pochodzącej od <xref:System.Xml.Xsl.XsltContext>. Komentarze w kodzie opisują elementy członkowskie klasy i ich użycia w funkcjach niestandardowych. Implementacje funkcji i zmiennych oraz Przykładowa aplikacja, która używa tych implementacji, jest zgodna z tym segmentem kodu.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Poniższy kod implementuje <xref:System.Xml.Xsl.IXsltContextFunction>. Klasa, która implementuje <xref:System.Xml.Xsl.IXsltContextFunction> rozpoznaje i wykonuje funkcje zdefiniowane przez użytkownika. Ten przykład używa funkcji identyfikowanej przez deklarację: `private int CountChar(string title, char charTocount)`.  
  
 Komentarze do kodu opisują elementy członkowskie klasy.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Poniższy kod implementuje <xref:System.Xml.Xsl.IXsltContextVariable>. Ta klasa rozpoznaje odwołania do zmiennych zdefiniowanych przez użytkownika w wyrażeniach zapytań XPath w czasie wykonywania. Wystąpienie tej klasy jest tworzone i zwracane przez przesłoniętą <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> metodę klasy niestandardowej. <xref:System.Xml.Xsl.XsltContext>  
  
 Komentarze do kodu opisują elementy członkowskie klasy.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 Z poprzednimi definicjami klas w zakresie, poniższy kod używa funkcji niestandardowej do zliczania znaków w elementach `Tasks.xml` dokumentu. Komentarze w kodzie opisują kod, który kompiluje funkcję niestandardową i uruchamia ją względem `Tasks.xml` dokumentu.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 W tym przykładzie są stosowane następujące dane XML.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
