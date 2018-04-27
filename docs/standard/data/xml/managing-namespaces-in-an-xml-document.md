---
title: Zarządzanie przestrzeni nazw w dokumencie XML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
caps.latest.revision: 5
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 211d4f2ee3f47e1defdc8a3bd4fc81618fa3fefd
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="32607-102">Zarządzanie przestrzeni nazw w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="32607-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="32607-103">Przestrzenie nazw XML skojarzenia elementu oraz nazwy atrybutów w dokumencie XML z wstępnie zdefiniowanych i niestandardowych identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="32607-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="32607-104">Aby utworzyć skojarzenia, zdefiniuj prefiksów identyfikatorów URI przestrzeni nazw i używać tych prefiksów na kwalifikować się nazw elementów i atrybutów w danych XML.</span><span class="sxs-lookup"><span data-stu-id="32607-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="32607-105">Przestrzenie nazw uniknąć konfliktów nazw elementów i atrybutów, a następnie włącz elementów i atrybutów o tej samej nazwie, można go obsłużyć ani zweryfikowany inaczej.</span><span class="sxs-lookup"><span data-stu-id="32607-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a><span data-ttu-id="32607-106">Deklarowanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="32607-106">Declaring namespaces</span></span>  
 <span data-ttu-id="32607-107">Deklarowanie przestrzeni nazw dla elementu, należy użyć `xmlns:` atrybutu:</span><span class="sxs-lookup"><span data-stu-id="32607-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="32607-108">gdzie `<name>` jest prefiks przestrzeni nazw i `<"uri">` jest identyfikator URI, który identyfikuje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="32607-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="32607-109">Po deklaracji prefiksu służy ona do uprawnione elementów i atrybutów w dokumencie XML i skojarzyć je z identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="32607-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="32607-110">Ponieważ prefiks przestrzeni nazw jest używana w całym dokumencie, należy go krótkich długości.</span><span class="sxs-lookup"><span data-stu-id="32607-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="32607-111">W tym przykładzie definiuje dwie `BOOK` elementów.</span><span class="sxs-lookup"><span data-stu-id="32607-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="32607-112">Pierwszy element elementu kwalifikuje się według prefiksu, `mybook`, a drugi element kwalifikuje się według prefiksu, `bb`.</span><span class="sxs-lookup"><span data-stu-id="32607-112">The first element element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="32607-113">Każdy prefiks jest skojarzona z inną przestrzeń nazw identyfikatora URI:</span><span class="sxs-lookup"><span data-stu-id="32607-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 <span data-ttu-id="32607-114">Aby wskazują, że element jest częścią określonego obszaru nazw, Dodaj prefiks przestrzeni nazw do niego.</span><span class="sxs-lookup"><span data-stu-id="32607-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="32607-115">Na przykład jeśli `Author` element należy do `mybook` przestrzeni nazw jest zadeklarowana jako `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="32607-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a><span data-ttu-id="32607-116">Zakresu deklaracji</span><span class="sxs-lookup"><span data-stu-id="32607-116">Declaration scope</span></span>  
 <span data-ttu-id="32607-117">Przestrzeń nazw ma zastosowanie w punkcie deklaracji aż do zakończenia elementu został zadeklarowany w.</span><span class="sxs-lookup"><span data-stu-id="32607-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="32607-118">W tym przykładzie przestrzeń nazw zdefiniowana w `BOOK` element nie ma zastosowania do elementów poza `BOOK` element, taki jak `Publisher` elementu:</span><span class="sxs-lookup"><span data-stu-id="32607-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 <span data-ttu-id="32607-119">Przestrzeń nazw musi być zadeklarowana przed użyciem, ale nie ma być wyświetlany w górnej części dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="32607-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="32607-120">Użycie kilku obszarów nazw w dokumencie XML, można zdefiniować jako domyślna przestrzeń nazw, można utworzyć dokumentu czyszcząca wyglądającej jednej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="32607-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="32607-121">Domyślna przestrzeń nazw jest zadeklarowana w elemencie głównym i ma zastosowanie do wszystkich elementów niekwalifikowane w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="32607-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="32607-122">Domyślne obszary nazw dotyczą tylko elementy nie atrybutów.</span><span class="sxs-lookup"><span data-stu-id="32607-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="32607-123">Aby użyć domyślnej przestrzeni nazw, Pomiń prefiks i dwukropka z deklaracją elementu:</span><span class="sxs-lookup"><span data-stu-id="32607-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="32607-124">Zarządzanie przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="32607-124">Managing namespaces</span></span>  
 <span data-ttu-id="32607-125"><xref:System.Xml.XmlNamespaceManager> Klasy przechowuje zbiór URI przestrzeni nazw i prefiksy oraz umożliwia wyszukiwania, dodawanie i usuwanie przestrzeni nazw z tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="32607-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="32607-126">W niektórych kontekstach ta klasa jest wymagane w celu zapewnienia lepszej wydajności przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="32607-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="32607-127">Na przykład <xref:System.Xml.Xsl.XsltContext> klasy używa <xref:System.Xml.XmlNamespaceManager> obsługę języka XPath.</span><span class="sxs-lookup"><span data-stu-id="32607-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="32607-128">Menedżer przestrzeni nazw nie sprawdzają poprawność wszystkie przestrzenie nazw, ale założono, że prefiksy i przestrzenie nazw już została zweryfikowana i jest zgodny ze [przestrzenie nazw W3C](https://www.w3.org/TR/REC-xml-names/) specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="32607-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32607-129">[LINQ do XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) nie używa <xref:System.Xml.XmlNamespaceManager> do zarządzania obszarami nazw.</span><span class="sxs-lookup"><span data-stu-id="32607-129">[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) doesn't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="32607-130">Zobacz [Praca z przestrzeni nazw XML](https://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) w dokumentacji LINQ informacji o zarządzaniu przestrzeni nazw w przypadku korzystania z LINQ do XML.</span><span class="sxs-lookup"><span data-stu-id="32607-130">See [Working with XML Namespaces](https://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="32607-131">Poniżej przedstawiono niektóre zadania zarządzania i wyszukiwania można wykonywać za pomocą <xref:System.Xml.XmlNamespaceManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="32607-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="32607-132">Aby uzyskać dodatkowe informacje i przykłady skorzystaj z łączy na stronie dla każdej metody lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="32607-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="32607-133">Do</span><span class="sxs-lookup"><span data-stu-id="32607-133">To</span></span>|<span data-ttu-id="32607-134">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="32607-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="32607-135">Dodawanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="32607-135">Add a namespace</span></span>|<span data-ttu-id="32607-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32607-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="32607-137">Usuń przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="32607-137">Remove a namespace</span></span>|<span data-ttu-id="32607-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32607-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="32607-139">Znajdź identyfikator URI dla domyślnej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="32607-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="32607-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Właściwość</span><span class="sxs-lookup"><span data-stu-id="32607-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="32607-141">Znajdź identyfikator URI dla prefiksu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="32607-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="32607-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32607-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="32607-143">Znajdź prefiks dla identyfikatora URI przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="32607-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="32607-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32607-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="32607-145">Pobierz listę przestrzeni nazw w bieżącym węźle</span><span class="sxs-lookup"><span data-stu-id="32607-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="32607-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32607-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="32607-147">Zakres przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="32607-147">Scope a namespace</span></span>|<span data-ttu-id="32607-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> i <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody</span><span class="sxs-lookup"><span data-stu-id="32607-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="32607-149">Sprawdź, czy prefiks jest zdefiniowana w bieżącym zakresie</span><span class="sxs-lookup"><span data-stu-id="32607-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="32607-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32607-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="32607-151">Pobierz tabelę nazwę używaną do odszukania prefiksy oraz identyfikatorów URI</span><span class="sxs-lookup"><span data-stu-id="32607-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="32607-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> Właściwość</span><span class="sxs-lookup"><span data-stu-id="32607-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32607-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32607-153">See Also</span></span>  
 <xref:System.Xml.XmlNamespaceManager>  
 [<span data-ttu-id="32607-154">Dokumenty i dane XML</span><span class="sxs-lookup"><span data-stu-id="32607-154">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
