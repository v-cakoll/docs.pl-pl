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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61952025"
---
# <a name="user-defined-functions-and-variables"></a>Funkcje i zmienne zdefiniowane przez użytkownika
<xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, które są używane do interakcji z <xref:System.Xml.XPath.XPathDocument> danych. Można uzupełnić standardowych funkcji XPath, implementując rozszerzenia funkcje i zmienne do wykorzystania przez wyrażenia kwerendy XPath. <xref:System.Xml.XPath.XPathExpression.SetContext%2A> Metoda może akceptować kontekst zdefiniowane przez użytkownika pochodzi od <xref:System.Xml.Xsl.XsltContext>. Funkcje zdefiniowane przez użytkownika są rozwiązywane przez niestandardowe kontekstu.  
  
 Rozszerzenie funkcji i zmiennych, może być przydatne w zapobieganiu ataki przez iniekcję kodu XML. W tych scenariuszach danych wejściowych użytkownika jest przypisane do niestandardowych zmiennych, a następnie przetwarzany przez funkcji rozszerzenia nie jako nieprzetworzone dane wejściowe połączonych za pomocą instrukcji przetwarzania. Rozszerzenie funkcje i zmienne zawierają dane wejściowe użytkownika tak, aby tylko działa na dane XML zgodnie z założeniami przez projektanta.  
  
 Aby korzystać z rozszerzeń zaimplementować niestandardowy <xref:System.Xml.Xsl.XsltContext> klasy wraz z interfejsów <xref:System.Xml.Xsl.IXsltContextFunction> i <xref:System.Xml.Xsl.IXsltContextVariable> obsługujące rozszerzenia funkcje i zmienne. <xref:System.Xml.XPath.XPathExpression> Dodaje dane wejściowe użytkownika z jego <xref:System.Xml.Xsl.XsltArgumentList> niestandardowe <xref:System.Xml.Xsl.XsltContext>.  
  
 <xref:System.Xml.XPath.XPathExpression> Reprezentuje skompilowaną zapytanie <xref:System.Xml.XPath.XPathNavigator> używa do znalezienia i przetwarzania węzły identyfikowane przez wyrażenie.  
  
 W poniższym przykładzie pokazano implementację klasy kontekstowego pochodzące z <xref:System.Xml.Xsl.XsltContext>. Komentarze w kodzie opisano elementy członkowskie klasy i ich użycie w funkcji niestandardowych. Implementacje funkcji i zmiennych i przykładowej aplikacji, która korzysta z tych implementacji postępuj zgodnie z tym segmencie kodu.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Poniższy kod implementuje <xref:System.Xml.Xsl.IXsltContextFunction>. Klasa, która implementuje <xref:System.Xml.Xsl.IXsltContextFunction> rozpoznaje i wykonuje funkcje zdefiniowane przez użytkownika. W tym przykładzie użyto funkcji identyfikowane za pomocą deklaracji: `private int CountChar(string title, char charTocount)`.  
  
 Komentarze w kodzie opisano elementy członkowskie klasy.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Poniższy kod implementuje <xref:System.Xml.Xsl.IXsltContextVariable>. Ta klasa jest rozpoznawany jako odwołania do zmiennych zdefiniowanych przez użytkownika w wyrażenia kwerendy XPath w czasie wykonywania. Wystąpienie tej klasy jest tworzony i zwracany przez zastąpione <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> metoda niestandardowa <xref:System.Xml.Xsl.XsltContext> klasy.  
  
 Komentarze w kodzie opisano składowych klasy.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 Przy użyciu poprzednich definicje klas w zakresie w poniższym kodzie użyto funkcję niestandardową do liczba znaków w elementach `Tasks.xml` dokumentu. Komentarze w kodzie opis kodu, który kompiluje funkcję niestandardową i uruchamia go przed `Tasks.xml` dokumentu.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 W tym przykładzie użyto następujących danych XML.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
