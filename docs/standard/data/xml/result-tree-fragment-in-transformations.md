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
ms.openlocfilehash: 1a4b585fe34a841061f8e5bab7cb18a58f53cfe8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="38e5a-102">Wynikowego fragmentu drzewa w przekształcenia</span><span class="sxs-lookup"><span data-stu-id="38e5a-102">Result Tree Fragment in Transformations</span></span>
> [!NOTE]
>  <span data-ttu-id="38e5a-103"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38e5a-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="38e5a-104">Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="38e5a-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="38e5a-105">Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="38e5a-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="38e5a-106">Wynik drzewa fragmenty, znanej także jako wynik drzewa fragmenty są nic więcej niż specjalny typ zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="38e5a-107">Można wykonywać żadnych funkcji na nich, które mogą być wykonywane na zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="38e5a-108">Lub możesz również przeprowadzić konwersję wynikowego fragmentu drzewa ustawić za pomocą węzła `node-set()` działać, a następnie użyć go w dowolnym miejscu, że zestaw węzłów może być używany.</span><span class="sxs-lookup"><span data-stu-id="38e5a-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>  
  
 <span data-ttu-id="38e5a-109">Wynikowego fragmentu drzewa jest tworzony w wyniku użycia `<xsl:variable>` lub `<xsl:param>` elementu w szczególny sposób w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="38e5a-110">Składnia `variable` i `parameter` elementy wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="38e5a-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>  
  
```xml  
<xsl:param name=Qname select= XPath Expression >  
    template body  
</xsl:param>  
  
<xsl:variable name=Qname select=XPath Expression >  
    template body  
</xsl:variable>  
```  
  
 <span data-ttu-id="38e5a-111">Aby uzyskać `parameter` elementu, wartość jest przypisywana nazwa kwalifikowana (`Qname`) na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="38e5a-112">Można przypisać wartości domyślnej parametru zwracając zawartości z wyrażenia XML Path Language (XPath) w `select` atrybutu lub przez przypisanie zawartość treści szablonu.</span><span class="sxs-lookup"><span data-stu-id="38e5a-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="38e5a-113">Aby uzyskać `variable` , wartość jest również przypisany element na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="38e5a-114">Przypisz go przez zwrócenie zawartości z wyrażenia XPath w `select` atrybutu lub przez przypisanie zawartość treści szablonu.</span><span class="sxs-lookup"><span data-stu-id="38e5a-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="38e5a-115">Dla obu `parameter` i `variable` elementy, jeśli wartość jest przypisywany przez wyrażenie XPath, następnie jeden z czterech podstawowych typów XPath, zostanie zwrócony: wartość logiczna, ciąg, liczba lub zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="38e5a-116">Gdy wartość jest podana przy użyciu treści pusty szablon, zwracany typ danych z systemem innym niż XPath i który będzie wynikowego fragmentu drzewa.</span><span class="sxs-lookup"><span data-stu-id="38e5a-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>  
  
 <span data-ttu-id="38e5a-117">Gdy zmienna jest powiązana z wynikowego fragmentu drzewa zamiast co cztery podstawowe typy danych języka XPath, jest to czas tylko że kwerenda XPath zwraca typ, który nie jest jednym z czterech typów obiektów języka XPath.</span><span class="sxs-lookup"><span data-stu-id="38e5a-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="38e5a-118">Wynik fragmenty drzewa i ich zachowanie omówiono w specyfikacji sieci World Wide Web konsorcjum W3C w www.w3.org/XSLT, sekcji 11.1 wynik drzewa fragmenty sekcji 11.6 przekazywanie parametrów szablonów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-118">Result tree fragments and their behavior are discussed in the World Wide Web Consortium (W3C) specification at www.w3.org/XSLT, section 11.1 Result Tree Fragments through section 11.6 Passing Parameters to Templates.</span></span> <span data-ttu-id="38e5a-119">Ponadto sekcji wprowadzenie 1 omówiono, jak szablony mogą zawierać elementy z przestrzeni nazw XSLT, które zwraca lub tworzy wynik fragmenty drzewa.</span><span class="sxs-lookup"><span data-stu-id="38e5a-119">Also, section 1 Introduction discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>  
  
 <span data-ttu-id="38e5a-120">Wynikowego fragmentu drzewa w koncepcji, zachowuje się jak ustawić niczego nie więcej niż jednym węźle głównym węzłem.</span><span class="sxs-lookup"><span data-stu-id="38e5a-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="38e5a-121">Jednak pozostałe węzły zwracane są węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="38e5a-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="38e5a-122">Aby programowo Zobacz węzły podrzędne, skopiuj wynikowego fragmentu drzewa do drzewa wyników przy użyciu `<xsl:copy-of>` elementu.</span><span class="sxs-lookup"><span data-stu-id="38e5a-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="38e5a-123">Podczas kopiowania z jest wykonywana, wszystkie węzły podrzędne są również kopiowane do drzewa wynik w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="38e5a-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="38e5a-124">Dopóki `copy` lub `copy-of` jest używana, wynikowego fragmentu drzewa nie jest częścią drzewa wynik lub dane wyjściowe z transformacji.</span><span class="sxs-lookup"><span data-stu-id="38e5a-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>  
  
 <span data-ttu-id="38e5a-125">Aby przejść przez węzły zwrócony wynikowego fragmentu drzewa <xref:System.Xml.XPath.XPathNavigator> jest używany.</span><span class="sxs-lookup"><span data-stu-id="38e5a-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="38e5a-126">Poniższy przykładowy kod przedstawia sposób tworzenia wynikowego fragmentu drzewa w arkuszu stylów przez wywołanie funkcji z parametrem `fragment`, który zawiera kod XML.</span><span class="sxs-lookup"><span data-stu-id="38e5a-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>  
  
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
  
 <span data-ttu-id="38e5a-127">Oto inny przykład przedstawiający zmiennej, która jest w formacie tekstu sformatowanego (RTF), i w związku z tym Ustaw typ wynikowego fragmentu drzewa, które nie są konwertowane na węźle.</span><span class="sxs-lookup"><span data-stu-id="38e5a-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="38e5a-128">Zamiast tego została przekazana do funkcji skryptu i <xref:System.Xml.XPath.XPathNavigator> służy do przechodzenia przez węzły.</span><span class="sxs-lookup"><span data-stu-id="38e5a-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>  
  
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
  
 <span data-ttu-id="38e5a-129">Wynik transformacji XML dowolnego z tego arkusza stylów przedstawiono w następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="38e5a-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>  
  
## <a name="output"></a><span data-ttu-id="38e5a-130">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="38e5a-130">Output</span></span>  
  
```xml  
<first_book xmlns:user="urn:books">Book1</first_book>  
```  
  
 <span data-ttu-id="38e5a-131">Jak wspomniano powyżej, `node-set` funkcja umożliwia konwertowanie wynikowego fragmentu drzewa na zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="38e5a-132">Wynikowa węzeł zawsze zawiera jeden węzeł, który jest węzła głównego drzewa.</span><span class="sxs-lookup"><span data-stu-id="38e5a-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="38e5a-133">Jeśli Konwertuj wynikowego fragmentu drzewa do węzła ustawiona, możesz użyć jej gdziekolwiek jest używany zestaw węzłów regularne, takie jak dla każdej instrukcji lub w wartości `select` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="38e5a-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="38e5a-134">Następujące wiersze kodu Pokaż fragmentu konwertowanej do węzła ustaw i używane jako zestawu węzłów:</span><span class="sxs-lookup"><span data-stu-id="38e5a-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>  
  
 `<xsl:for-each select="msxsl:node-set($node-fragment)">`  
  
 `<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`  
  
 <span data-ttu-id="38e5a-135">Gdy fragment jest konwertowana na zestaw węzłów, nie są już używane <xref:System.Xml.XPath.XPathNavigator> do nawigacji nad nim.</span><span class="sxs-lookup"><span data-stu-id="38e5a-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="38e5a-136">Dla zestawu węzłów, możesz użyć <xref:System.Xml.XPath.XPathNodeIterator> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="38e5a-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>  
  
 <span data-ttu-id="38e5a-137">W poniższym przykładzie `$var` jest zmienna, która jest węzeł drzewa w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="38e5a-138">Dla każdej instrukcji połączone z `node-set` funkcji umożliwia użytkownikowi iteracja tego drzewa jako zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="38e5a-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>  
  
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
  
 <span data-ttu-id="38e5a-139">Kolejny przykład zmiennej, która jest w formacie RTF, a więc typu wynikowego fragmentu drzewa, który jest przekonwertowana na węzeł ustawiona przed przesłaniem do funkcji skryptu jako XPathNodeIterator.</span><span class="sxs-lookup"><span data-stu-id="38e5a-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>  
  
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
  
 <span data-ttu-id="38e5a-140">Poniżej znajduje się wynik transformacji XML z tego arkusza stylów:</span><span class="sxs-lookup"><span data-stu-id="38e5a-140">The following is the result of transforming XML with this style sheet:</span></span>  
  
```xml  
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38e5a-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38e5a-141">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="38e5a-142">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="38e5a-142">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="38e5a-143">Klasa XslTransform implementuje procesorze XSLT</span><span class="sxs-lookup"><span data-stu-id="38e5a-143">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
