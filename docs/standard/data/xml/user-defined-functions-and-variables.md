---
title: Funkcje i zmienne zdefiniowane przez użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2ce474dac44de1ac72811ecd3bc294ba57ce40a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570474"
---
# <a name="user-defined-functions-and-variables"></a>Funkcje i zmienne zdefiniowane przez użytkownika
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, które są używane do interakcji z <xref:System.Xml.XPath.XPathDocument> danych. Standardowe funkcje XPath można uzupełnić zaimplementowanie rozszerzenia funkcje i zmienne do użytku przez wyrażenia zapytania XPath. <xref:System.Xml.XPath.XPathExpression.SetContext%2A> Metody może zaakceptować kontekst zdefiniowane przez użytkownika pochodzące z <xref:System.Xml.Xsl.XsltContext>. Funkcje zdefiniowane przez użytkownika są rozpoznawane przez kontekst niestandardowych.  
  
 Rozszerzenie funkcji i zmiennych, może być przydatne w zapobieganiu atakom iniekcji kodu XML. W tych scenariuszach danych wejściowych użytkownika jest przypisany do niestandardowych zmiennych i przetwarzane przez funkcje rozszerzeń nie jako nieprzetworzone dane wejściowe, połączony z instrukcji przetwarzania. Rozszerzenie funkcje i zmienne zawierają dane wejściowe użytkownika tak, aby tylko pełnił w danych XML zgodnie z założeniami przez projektanta.  
  
 Aby korzystać z rozszerzeń zaimplementowania niestandardowego <xref:System.Xml.Xsl.XsltContext> klasy wraz z interfejsów <xref:System.Xml.Xsl.IXsltContextFunction> i <xref:System.Xml.Xsl.IXsltContextVariable> obsługujących rozszerzenia funkcje i zmienne. <xref:System.Xml.XPath.XPathExpression> Dodaje dane wejściowe użytkownika z jego <xref:System.Xml.Xsl.XsltArgumentList> niestandardowe <xref:System.Xml.Xsl.XsltContext>.  
  
 <xref:System.Xml.XPath.XPathExpression> Reprezentuje skompilowane zapytanie <xref:System.Xml.XPath.XPathNavigator> używa do znalezienia i przetworzyć węzłów zidentyfikowane przez wyrażenie.  
  
 W poniższym przykładzie przedstawiono Implementacja klasy kontekstowych pochodną <xref:System.Xml.Xsl.XsltContext>. Komentarze w kodzie opisano elementy członkowskie klasy i ich użycie w funkcji niestandardowych. Implementacje funkcji i zmiennej i przykładowej aplikacji, która używa tych implementacji wykonaj ten segment kodu.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Poniższy kod implementuje <xref:System.Xml.Xsl.IXsltContextFunction>. Klasa implementująca <xref:System.Xml.Xsl.IXsltContextFunction> rozpoznaje i wykonuje funkcje zdefiniowane przez użytkownika. W tym przykładzie użyto funkcji określone przez deklarację: `private int CountChar(string title, char charTocount)`.  
  
 Komentarze w kodzie opisano elementy członkowskie klasy.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Poniższy kod implementuje <xref:System.Xml.Xsl.IXsltContextVariable>. Ta klasa jest rozpoznawany jako odwołań do zmiennych zdefiniowanych przez użytkownika w wyrażeniach kwerend XPath w czasie wykonywania. Wystąpienia tej klasy jest tworzone i zwrócony przez przesłoniętych <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> metoda niestandardowa <xref:System.Xml.Xsl.XsltContext> klasy.  
  
 Komentarze w kodzie opisano elementy członkowskie klasy.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 Z poprzednich definicje klas w zakresie następujący kod funkcja niestandardowych liczba znaków w elementach `Tasks.xml` dokumentu. Komentarze w kodzie opisano kod funkcji niestandardowej kompiluje i uruchamia go przed `Tasks.xml` dokumentu.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 W tym przykładzie używane są następujące dane XML.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
