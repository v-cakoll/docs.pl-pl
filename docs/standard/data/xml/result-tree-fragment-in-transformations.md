---
title: Wynikowy fragment drzewa w przekształceniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
ms.openlocfilehash: e454c1194e8c280042857f106e22d0d0509417e3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156364"
---
# <a name="result-tree-fragment-in-transformations"></a>Wynikowy fragment drzewa w przekształceniach

> [!NOTE]
> Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0. Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) .

 Fragmenty drzewa wyników, znane także jako fragmenty drzewa wyników, nie są dłuższe niż specjalny typ zestawu węzłów. Można wykonać dowolną z nich funkcję, którą można wykonać w zestawie węzłów. Można również skonwertować fragment drzewa wynikowy do zestawu węzłów przy użyciu funkcji `node-set()`, a następnie użyć jej w dowolnym miejscu, w którym można użyć zestawu węzłów.

 Fragment drzewa wynik jest tworzony w wyniku użycia elementu `<xsl:variable>` lub `<xsl:param>` w określony sposób w arkuszu stylów. Składnia dla `variable` i `parameter` elementów jest następująca:

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

Dla elementu `parameter` wartość jest przypisywana do kwalifikowanej nazwy (`Qname`) na kilka sposobów. Do parametru można przypisać wartość domyślną, zwracając zawartość z wyrażenia XML Path Language (XPath) w atrybucie `select` lub przypisując jej zawartość treści szablonu.

Dla elementu `variable` wartość jest również przypisywana na kilka sposobów. Można ją przypisać, zwracając zawartość z wyrażenia XPath w atrybucie `select` lub przypisując jej zawartość treści szablonu.

W przypadku `parameter` i `variable` elementów, jeśli wartość jest przypisana przez wyrażenie XPath, zostanie zwrócony jeden z czterech podstawowych typów XPath: wartość logiczna, ciąg, liczba lub zestaw węzłów. Gdy wartość jest podawana przy użyciu niepustej treści szablonu, zwracany jest typ danych inny niż XPath, który będzie fragmentem drzewa wyników.

Gdy zmienna jest powiązana z fragmentem drzewa wyników zamiast jednego z czterech podstawowych typów danych XPath, jest to jedyna godzina, o której zapytanie XPath zwraca typ, który nie jest jednym z czterech typów obiektów XPath. Fragmenty drzewa wyników i ich zachowanie zostały omówione w [specyfikacji organizacja World Wide Web Consortium (W3C)](https://www.w3.org/TR/xslt-10/), [sekcja 11,1 fragmenty drzewa wyników](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) w [sekcji 11,6 Przekazywanie parametrów do szablonów](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates). Ponadto w [sekcji 1](https://www.w3.org/TR/xslt-10/#section-Introduction) opisano sposób, w jaki szablony mogą zawierać elementy z przestrzeni nazw XSLT, które zwracają lub tworzą fragmenty drzewa wyników.

Fragment drzewa wyników, w koncepcji, zachowuje się jak zestaw węzłów bez więcej niż jeden węzeł główny. Pozostałe zwrócone węzły są jednak węzłami podrzędnymi. Aby programowo wyświetlić węzły podrzędne, skopiuj fragment drzewa wynik do drzewa wynik przy użyciu elementu `<xsl:copy-of>`. Gdy wykonywana jest kopia, wszystkie węzły podrzędne są również kopiowane do drzewa wynik w sekwencji. Dopóki nie zostanie użyta `copy` lub `copy-of`, fragment drzewa wyników nie jest częścią drzewa wyników ani danych wyjściowych transformacji.

Aby wykonać iterację w zwróconych węzłach fragmentu drzewa wyników, zostanie użyta <xref:System.Xml.XPath.XPathNavigator>. Poniższy przykład kodu pokazuje, jak utworzyć fragment drzewa wyników w arkuszu stylów, wywołując funkcję z parametrem `fragment`, który zawiera kod XML.

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

Oto kolejny przykład pokazujący zmienną, która jest w formacie tekstu sformatowanego (RTF), a tym samym typ fragmentu drzewa wyników, który nie jest konwertowany na zestaw węzłów. Zamiast tego jest przenoszona do funkcji skryptu, a <xref:System.Xml.XPath.XPathNavigator> jest używany do nawigowania po węzłach.

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

Wynik przekształcenia dowolnego kodu XML z tym arkuszem stylów jest przedstawiony w następujących danych wyjściowych.

## <a name="output"></a>Dane wyjściowe

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

Jak wspomniano powyżej, funkcja `node-set` umożliwia konwertowanie fragmentu drzewa wynikowego na zestaw węzłów. Węzeł z wynikiem zawsze zawiera pojedynczy węzeł, który jest węzłem głównym drzewa. W przypadku konwertowania fragmentu drzewa wyników do zestawu węzłów, można go użyć wszędzie tam, gdzie jest używany zwykły zestaw węzłów, na przykład w instrukcji for-each lub w wartości atrybutu `select`. Następujące wiersze kodu pokazują fragment konwertowany na zestaw węzłów i używany jako zestaw węzłów:

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

Gdy fragment jest konwertowany na zestaw węzłów, nie jest już używany <xref:System.Xml.XPath.XPathNavigator> do nawigowania po nim. W przypadku zestawu węzłów zamiast tego użyj <xref:System.Xml.XPath.XPathNodeIterator>.

W poniższym przykładzie `$var` jest zmienną, która jest drzewem węzła w arkuszu stylów. Instrukcja for-each, w połączeniu z funkcją `node-set`, umożliwia użytkownikowi iterację w tym drzewie jako zestaw węzłów.

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

Oto inny przykład zmiennej, która znajduje się w formacie RTF, a w związku z tym fragment drzewa wyników, który jest konwertowany na zestaw węzłów przed przekazaniem do funkcji skryptu jako XPathNodeIterator.

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

Poniżej przedstawiono wynik przekształcenia XML z tym arkuszem stylów:

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XPath.XPathNodeIterator>
- [Przekształcenia XSLT przy użyciu klasy XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
