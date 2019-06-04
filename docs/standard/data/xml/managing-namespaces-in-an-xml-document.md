---
title: Zarządzanie przestrzeniami nazw w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83ea398f18ab02840ea811c74a6053dba11a3baa
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490889"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="510eb-102">Zarządzanie przestrzeniami nazw w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="510eb-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="510eb-103">Obszary nazw XML skojarzyć nazw elementów i atrybutów w dokumencie XML przy użyciu wstępnie zdefiniowanych i niestandardowych identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="510eb-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="510eb-104">Aby utworzyć te skojarzenia, zdefiniuj prefiksów identyfikatorów URI przestrzeni nazw, a używać tych prefiksów do kwalifikowania nazwy elementów i atrybutów w danych XML.</span><span class="sxs-lookup"><span data-stu-id="510eb-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="510eb-105">Przestrzenie nazw zapobiec kolizjom nazw elementów i atrybutów i umożliwić elementów i atrybutów o tej samej nazwie i obsługi sprawdzania poprawności w różny sposób.</span><span class="sxs-lookup"><span data-stu-id="510eb-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a><span data-ttu-id="510eb-106">Deklarowanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="510eb-106">Declaring namespaces</span></span>  
 <span data-ttu-id="510eb-107">Aby zadeklarować przestrzeni nazw w elemencie, należy użyć `xmlns:` atrybutu:</span><span class="sxs-lookup"><span data-stu-id="510eb-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="510eb-108">gdzie `<name>` jest prefiks przestrzeni nazw i `<"uri">` jest identyfikator URI, który identyfikuje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="510eb-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="510eb-109">Po zadeklarowaniu prefiks służy do kwalifikowania elementów i atrybutów w dokumencie XML i skojarzyć je z identyfikatora URI obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="510eb-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="510eb-110">Ponieważ prefiks przestrzeni nazw są używane w całym dokumencie, powinno być krótki długości.</span><span class="sxs-lookup"><span data-stu-id="510eb-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="510eb-111">W tym przykładzie definiuje dwa `BOOK` elementów.</span><span class="sxs-lookup"><span data-stu-id="510eb-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="510eb-112">Pierwszy element kwalifikuje się według prefiksu, `mybook`, a drugi element kwalifikuje się według prefiksu, `bb`.</span><span class="sxs-lookup"><span data-stu-id="510eb-112">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="510eb-113">Prefiksu dla każdego jest skojarzona z innej przestrzeni nazw identyfikatora URI:</span><span class="sxs-lookup"><span data-stu-id="510eb-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 <span data-ttu-id="510eb-114">Oznaczającego, czy element jest częścią określonego obszaru nazw, należy dodać do niej prefiks przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="510eb-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="510eb-115">Na przykład jeśli `Author` element należy do `mybook` przestrzeni nazw jest zadeklarowana jako `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="510eb-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a><span data-ttu-id="510eb-116">Zakresem deklaracji</span><span class="sxs-lookup"><span data-stu-id="510eb-116">Declaration scope</span></span>  
 <span data-ttu-id="510eb-117">Przestrzeń nazw jest efektywne w punkcie deklaracji, aż do zakończenia tego elementu został zadeklarowany w.</span><span class="sxs-lookup"><span data-stu-id="510eb-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="510eb-118">W tym przykładzie przestrzeń nazw zdefiniowana w `BOOK` element nie ma zastosowania do elementów poza `BOOK` element, taki jak `Publisher` elementu:</span><span class="sxs-lookup"><span data-stu-id="510eb-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
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
  
 <span data-ttu-id="510eb-119">Przestrzeń nazw musi być zadeklarowana przed użyciem, ale nie ma być wyświetlany w górnej części dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="510eb-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="510eb-120">Gdy używasz wiele przestrzeni nazw w dokumencie XML, można zdefiniować jedną przestrzeń nazw jako domyślny obszar nazw, można utworzyć czyszcząca wyglądających dokumentu.</span><span class="sxs-lookup"><span data-stu-id="510eb-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="510eb-121">Domyślny obszar nazw jest zadeklarowany w elemencie głównym i ma zastosowanie do wszystkich elementów niekwalifikowanej w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="510eb-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="510eb-122">Domyślne obszary nazw dotyczą tylko elementów nie do atrybutów.</span><span class="sxs-lookup"><span data-stu-id="510eb-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="510eb-123">Aby użyć domyślnej przestrzeni nazw, Pomiń prefiks i dwukropek, od deklaracji dla elementu:</span><span class="sxs-lookup"><span data-stu-id="510eb-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="510eb-124">Zarządzanie przestrzeniami nazw</span><span class="sxs-lookup"><span data-stu-id="510eb-124">Managing namespaces</span></span>  
 <span data-ttu-id="510eb-125"><xref:System.Xml.XmlNamespaceManager> Klasa przechowuje kolekcję URI przestrzeni nazw i prefiksy i pozwalają, dodawania i usuwania przestrzeni nazw z tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="510eb-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="510eb-126">W niektórych kontekstach ta klasa jest wymagana w celu zapewnienia lepszej wydajności przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="510eb-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="510eb-127">Na przykład <xref:System.Xml.Xsl.XsltContext> klasy używa <xref:System.Xml.XmlNamespaceManager> obsługę języka XPath.</span><span class="sxs-lookup"><span data-stu-id="510eb-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="510eb-128">Menedżer przestrzeni nazw nie wykonuje żadnych sprawdzania poprawności w przypadku przestrzeni nazw, ale założono, że prefiksy i przestrzenie nazw już zweryfikowana i są zgodne z [przestrzenie nazw W3C](https://www.w3.org/TR/REC-xml-names/) specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="510eb-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="510eb-129">LINQ do XML w [ C# ](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [języka Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) nie używaj <xref:System.Xml.XmlNamespaceManager> do zarządzania przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="510eb-129">LINQ TO XML in [C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="510eb-130">Zobacz [Praca z przestrzeniami nazw XML (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) i [Praca z przestrzeniami nazw XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) w dokumentacji programu LINQ, informacje o zarządzaniu przestrzeni nazw w przypadku korzystania z LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="510eb-130">See [Working with XML Namespaces (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) and [Working with XML Namespaces (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="510eb-131">Poniżej przedstawiono niektóre z zadań zarządzania i wyszukiwania, można wykonywać za pomocą <xref:System.Xml.XmlNamespaceManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="510eb-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="510eb-132">Aby uzyskać więcej informacji i przykładów skorzystaj z linków na stronie dokumentacji każda metoda lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="510eb-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="510eb-133">Zadanie</span><span class="sxs-lookup"><span data-stu-id="510eb-133">To</span></span>|<span data-ttu-id="510eb-134">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="510eb-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="510eb-135">Dodawanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="510eb-135">Add a namespace</span></span>|<span data-ttu-id="510eb-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="510eb-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="510eb-137">Usuwanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="510eb-137">Remove a namespace</span></span>|<span data-ttu-id="510eb-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="510eb-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="510eb-139">Znajdź identyfikator URI dla domyślnej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="510eb-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="510eb-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Właściwość</span><span class="sxs-lookup"><span data-stu-id="510eb-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="510eb-141">Znajdź identyfikator URI dla prefiksu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="510eb-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="510eb-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="510eb-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="510eb-143">Znajdź prefiks dla identyfikatora URI obszaru nazw</span><span class="sxs-lookup"><span data-stu-id="510eb-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="510eb-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="510eb-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="510eb-145">Pobierz listę przestrzeni nazw w bieżącym węźle</span><span class="sxs-lookup"><span data-stu-id="510eb-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="510eb-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="510eb-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="510eb-147">Określanie zakresu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="510eb-147">Scope a namespace</span></span>|<span data-ttu-id="510eb-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> i <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody</span><span class="sxs-lookup"><span data-stu-id="510eb-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="510eb-149">Sprawdź, czy prefiks, który jest zdefiniowany w bieżącym zakresie</span><span class="sxs-lookup"><span data-stu-id="510eb-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="510eb-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="510eb-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="510eb-151">Pobierz tabelę nazw używany do wyszukiwania prefiksy i identyfikatory URI</span><span class="sxs-lookup"><span data-stu-id="510eb-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="510eb-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> Właściwość</span><span class="sxs-lookup"><span data-stu-id="510eb-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="510eb-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="510eb-153">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="510eb-154">Dokumenty i dane XML</span><span class="sxs-lookup"><span data-stu-id="510eb-154">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
