---
title: "Wynikowego fragmentu drzewa w przekształcenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 04e23f39f522fca7f69aa86be7036320a5698a60
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="result-tree-fragment-in-transformations"></a>Wynikowego fragmentu drzewa w przekształcenia
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 Wynik drzewa fragmenty, znanej także jako wynik drzewa fragmenty są nic więcej niż specjalny typ zestaw węzłów. Można wykonywać żadnych funkcji na nich, które mogą być wykonywane na zestaw węzłów. Lub możesz również przeprowadzić konwersję wynikowego fragmentu drzewa ustawić za pomocą węzła `node-set()` działać, a następnie użyć go w dowolnym miejscu, że zestaw węzłów może być używany.  
  
 Wynikowego fragmentu drzewa jest tworzony w wyniku użycia `<xsl:variable>` lub `<xsl:param>` elementu w szczególny sposób w arkuszu stylów. Składnia `variable` i `parameter` elementy wygląda następująco:  
  
```xml  
<xsl:param name=Qname select= XPath Expression >  
    template body  
</xsl:param>  
  
<xsl:variable name=Qname select=XPath Expression >  
    template body  
</xsl:variable>  
```  
  
 Aby uzyskać `parameter` elementu, wartość jest przypisywana nazwa kwalifikowana (`Qname`) na kilka sposobów. Można przypisać wartości domyślnej parametru zwracając zawartości z wyrażenia XML Path Language (XPath) w `select` atrybutu lub przez przypisanie zawartość treści szablonu.  
  
 Aby uzyskać `variable` , wartość jest również przypisany element na kilka sposobów. Przypisz go przez zwrócenie zawartości z wyrażenia XPath w `select` atrybutu lub przez przypisanie zawartość treści szablonu.  
  
 Dla obu `parameter` i `variable` elementy, jeśli wartość jest przypisywany przez wyrażenie XPath, następnie jeden z czterech podstawowych typów XPath, zostanie zwrócony: wartość logiczna, ciąg, liczba lub zestawu węzłów. Gdy wartość jest podana przy użyciu treści pusty szablon, zwracany typ danych z systemem innym niż XPath i który będzie wynikowego fragmentu drzewa.  
  
 Gdy zmienna jest powiązana z wynikowego fragmentu drzewa zamiast co cztery podstawowe typy danych języka XPath, jest to czas tylko że kwerenda XPath zwraca typ, który nie jest jednym z czterech typów obiektów języka XPath. Wynik fragmenty drzewa i ich zachowanie omówiono w specyfikacji sieci World Wide Web konsorcjum W3C w www.w3.org/XSLT, sekcji 11.1 wynik drzewa fragmenty sekcji 11.6 przekazywanie parametrów szablonów. Ponadto sekcji wprowadzenie 1 omówiono, jak szablony mogą zawierać elementy z przestrzeni nazw XSLT, które zwraca lub tworzy wynik fragmenty drzewa.  
  
 Wynikowego fragmentu drzewa w koncepcji, zachowuje się jak ustawić niczego nie więcej niż jednym węźle głównym węzłem. Jednak pozostałe węzły zwracane są węzłów podrzędnych. Aby programowo Zobacz węzły podrzędne, skopiuj wynikowego fragmentu drzewa do drzewa wyników przy użyciu `<xsl:copy-of>` elementu. Podczas kopiowania z jest wykonywana, wszystkie węzły podrzędne są również kopiowane do drzewa wynik w sekwencji. Dopóki `copy` lub `copy-of` jest używana, wynikowego fragmentu drzewa nie jest częścią drzewa wynik lub dane wyjściowe z transformacji.  
  
 Aby przejść przez węzły zwrócony wynikowego fragmentu drzewa <xref:System.Xml.XPath.XPathNavigator> jest używany. Poniższy przykładowy kod przedstawia sposób tworzenia wynikowego fragmentu drzewa w arkuszu stylów przez wywołanie funkcji z parametrem `fragment`, który zawiera kod XML.  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:var name="fragment">  
        <node1>  
            <node2/>  
        </node1>  
    <xsl:var>  
  
  <msxsl:script language="C#" implements-prefix="user">  
    function NodeFragment(XPathNavigator nav)  
    {  
      if (nav.HasSelection == false)  
        XPathNavigator.MoveToNext();  
      return;  
    }  
  </msxsl:script>  
  
    <xsl:template match="/">  
            <xsl:value-of select="user:NodeFragment(msxml:node-set($fragment))"/>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 Oto inny przykład przedstawiający zmiennej, która jest w formacie tekstu sformatowanego (RTF), i w związku z tym Ustaw typ wynikowego fragmentu drzewa, które nie są konwertowane na węźle. Zamiast tego została przekazana do funkcji skryptu i <xref:System.Xml.XPath.XPathNavigator> służy do przechodzenia przez węzły.  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNavigator nav)  
    {  
        bool b = nav.MoveToFirstChild();  
        if (b)  
            return nav.Value;  
        else  
            return "Does not exist";  
    }  
  
]]>  
  
</msxsl:script>  
  
<xsl:template match="/">  
    <first_book>  
        <xsl:value-of select="user:func($node-fragment)"/>  
    </first_book>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 Wynik transformacji XML dowolnego z tego arkusza stylów przedstawiono w następujących danych wyjściowych.  
  
## <a name="output"></a>Dane wyjściowe  
  
```xml  
<first_book xmlns:user="urn:books">Book1</first_book>  
```  
  
 Jak wspomniano powyżej, `node-set` funkcja umożliwia konwertowanie wynikowego fragmentu drzewa na zestaw węzłów. Wynikowa węzeł zawsze zawiera jeden węzeł, który jest węzła głównego drzewa. Jeśli Konwertuj wynikowego fragmentu drzewa do węzła ustawiona, możesz użyć jej gdziekolwiek jest używany zestaw węzłów regularne, takie jak dla każdej instrukcji lub w wartości `select` atrybutu. Następujące wiersze kodu Pokaż fragmentu konwertowanej do węzła ustaw i używane jako zestawu węzłów:  
  
 `<xsl:for-each select="msxsl:node-set($node-fragment)">`  
  
 `<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`  
  
 Gdy fragment jest konwertowana na zestaw węzłów, nie są już używane <xref:System.Xml.XPath.XPathNavigator> do nawigacji nad nim. Dla zestawu węzłów, możesz użyć <xref:System.Xml.XPath.XPathNodeIterator> zamiast tego.  
  
 W poniższym przykładzie `$var` jest zmienna, która jest węzeł drzewa w arkuszu stylów. Dla każdej instrukcji połączone z `node-set` funkcji umożliwia użytkownikowi iteracja tego drzewa jako zestawu węzłów.  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:variable name="states">  
        <node1>AL</node1>  
        <node1>CA</node1>  
        <node1>CO</node1>  
        <node1>WA</node1>  
    </xsl:variable>  
  
    <xsl:template match="/">  
            <xsl:for-each select="msxsl:node-set($states)"/>   
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 Kolejny przykład zmiennej, która jest w formacie RTF, a więc typu wynikowego fragmentu drzewa, który jest przekonwertowana na węzeł ustawiona przed przesłaniem do funkcji skryptu jako XPathNodeIterator.  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNodeIterator it)  
    {  
        it.MoveNext();   
        return it.Current.Value;   
        //it.Current returns XPathNavigator positioned on the current node  
    }  
  
]]>  
  
</msxsl:script>  
<xsl:template match="/">  
    <books>  
        <xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>  
    </books>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 Poniżej znajduje się wynik transformacji XML z tego arkusza stylów:  
  
```xml  
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
