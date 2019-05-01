---
title: Wynikowy fragment drzewa w przekształceniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4835536dd3ae815fbe7e50582b94caefb1fc9082
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027067"
---
# <a name="result-tree-fragment-in-transformations"></a>Wynikowy fragment drzewa w przekształceniach

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.

 Fragmenty drzewa wynik, znany także jako fragmenty drzewa wynik to nic więcej niż specjalny rodzaj zestawu węzłów. Dowolnej funkcji, można wykonywać na nich, które mogą być wykonywane w zestawie węzłów. Alternatywnie można również przeprowadzić konwersję wynikowego fragmentu drzewa, do węzła, można ustawić przy użyciu `node-set()` działać, a następnie użyć go w dowolnym miejscu, że zestaw węzłów może być używany.

 Wynikowego fragmentu drzewa jest tworzona w wyniku użycia `<xsl:variable>` lub `<xsl:param>` elementu w szczególny sposób w arkusza stylów. Składnia `variable` i `parameter` elementów jest następująca:

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

Aby uzyskać `parameter` elementu, wartość jest przypisywana do kwalifikowanej nazwy (`Qname`) na kilka sposobów. Można przypisać wartości domyślnej parametru, zwracając zawartości przy użyciu wyrażenia języka ścieżki XML (XPath) w `select` atrybutu lub przez przypisanie zawartość treści szablonu.

Aby uzyskać `variable` , wartość jest również przypisany element na kilka sposobów. Można ją przypisać, zwracając zawartości przy użyciu wyrażenia XPath w `select` atrybutu lub przez przypisanie zawartość treści szablonu.

Dla obu `parameter` i `variable` elementów, jeśli wartość jest przypisywany przez wyrażenie XPath następnie zestawu obejmującego cztery podstawowe typy XPath zostaną zwrócone: Ustaw atrybut typu wartość logiczna, ciąg, liczba lub węzeł. Gdy wartość znajduje się za pomocą treści szablonu pusta, zwracany typ danych bez XPath, który będzie wynikowego fragmentu drzewa.

Gdy zmienna jest powiązana z wynikowego fragmentu drzewa, zamiast jednej z czterech podstawowych typów danych XPath, to jest jedyny raz, że zapytanie XPath zwraca typ, który nie jest jedną z czterech typów obiektów języka XPath. Fragmenty drzewa wynik i ich zachowania, które zostały omówione w [Specyfikacja konsorcjum World Wide Web Consortium (W3C)](https://www.w3.org/TR/xslt-10/), [sekcji 11.1 fragmenty drzewa wynik](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) za pośrednictwem [sekcji 11.6 przekazywanie Parametry szablonów](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates). Ponadto [sekcji 1 wprowadzenie](https://www.w3.org/TR/xslt-10/#section-Introduction) w tym artykule omówiono, jak szablony mogą zawierać elementy z przestrzeni nazw XSLT, które zwracają lub utworzyć fragmenty drzewa wynik.

Wynikowego fragmentu drzewa w koncepcji, zachowuje się jak węzłem niczego nie więcej niż jednym węźle głównym. Jednak pozostałe węzły, zwracane są węzły podrzędne. Aby programowo zobaczyć węzły podrzędne, skopiuj wynikowego fragmentu drzewa do drzewa wynik przy użyciu `<xsl:copy-of>` elementu. Podczas kopiowania z jest wykonywana, wszystkie węzły podrzędne również są kopiowane do drzewa wynik w sekwencji. Do momentu `copy` lub `copy-of` jest używany, wynikowego fragmentu drzewa nie jest częścią drzewa wynik lub dane wyjściowe transformacji.

Iterowanie zwracany węzłów wynikowego fragmentu drzewa <xref:System.Xml.XPath.XPathNavigator> jest używany. Poniższy przykładowy kod przedstawia sposób tworzenia wynikowego fragmentu drzewa w arkuszu stylów, wywołując funkcję z parametrem `fragment`, który zawiera kod XML.

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

Oto inny przykład przedstawiający zmiennej, która jest w formacie tekstu sformatowanego (RTF), a w związku z tym, Ustaw typ wynikowego fragmentu drzewa, które nie są konwertowane na węzeł. Zamiast tego jest przekazywany do funkcji skryptu i <xref:System.Xml.XPath.XPathNavigator> służy do nawigowania w węzłach.

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

Wynik przekształcania żadnego kodu XML za pomocą tego arkusza stylów jest wyświetlany w następujących danych wyjściowych.

## <a name="output"></a>Dane wyjściowe

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

Jak wspomniano powyżej, `node-set` funkcja umożliwia konwertowanie wynikowego fragmentu drzewa w zestawie węzłów. Węzeł wynikowy zawiera zawsze jeden węzeł, który jest węzeł główny drzewa. Po skonwertowaniu wynikowego fragmentu drzewa do węzła ustawiona, używania go w dowolnym miejscu zestawu węzłów regularne jest używane, takie jak instrukcji for each, lub w wartości `select` atrybutu. Następujące wiersze kodu przedstawiają fragmentu konwertowane do węzła zestawu i używane jako zestaw węzłów:

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

Po przekonwertowaniu fragmentu do zestawu węzłów, nie są już używane <xref:System.Xml.XPath.XPathNavigator> do nawigacji nad nim. Dla zestawu węzłów, możesz użyć <xref:System.Xml.XPath.XPathNodeIterator> zamiast tego.

W poniższym przykładzie `$var` to zmienna, która jest węzeł drzewa w arkuszu stylów. Dla każdej instrukcji, w połączeniu z `node-set` funkcji i umożliwia użytkownikom do wykonywania iteracji tego drzewa jako zestaw węzłów.

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

Oto kolejny przykład zmiennej, która jest w formacie RTF, a więc z typu wynikowego fragmentu drzewa, który jest konwertowany na węzłem, przed przesłaniem do funkcji skryptu jako klasa XPathNodeIterator.

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

Poniżej znajduje się wynik Przekształcanie XML za pomocą tego arkusza stylów:

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XPath.XPathNodeIterator>
- [Przekształcenia XSLT przy użyciu klasy XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
