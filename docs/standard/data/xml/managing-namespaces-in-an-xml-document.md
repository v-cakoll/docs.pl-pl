---
title: Zarządzanie przestrzeniami nazw w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: b60e773183bd008c99022946a2ec53932234fe23
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289151"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="170ca-102">Zarządzanie przestrzeniami nazw w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="170ca-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="170ca-103">Przestrzenie nazw XML kojarzą nazwy elementów i atrybutów w dokumencie XML z niestandardowymi i wstępnie zdefiniowanymi identyfikatorami URI.</span><span class="sxs-lookup"><span data-stu-id="170ca-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="170ca-104">Aby utworzyć te skojarzenia, należy zdefiniować prefiksy dla identyfikatorów URI przestrzeni nazw, a następnie użyć tych prefiksów do kwalifikowania nazw elementów i atrybutów w danych XML.</span><span class="sxs-lookup"><span data-stu-id="170ca-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="170ca-105">Przestrzenie nazw uniemożliwiają kolizje nazw elementów i atrybutów, a elementy i atrybuty o tej samej nazwie mogą być obsługiwane i sprawdzane inaczej.</span><span class="sxs-lookup"><span data-stu-id="170ca-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>
## <a name="declaring-namespaces"></a><span data-ttu-id="170ca-106">Deklarowanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="170ca-106">Declaring namespaces</span></span>  
 <span data-ttu-id="170ca-107">Aby zadeklarować przestrzeń nazw dla elementu, należy użyć `xmlns:` atrybutu:</span><span class="sxs-lookup"><span data-stu-id="170ca-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="170ca-108">gdzie `<name>` jest prefiks przestrzeni nazw i `<"uri">` jest identyfikatorem URI, który identyfikuje przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="170ca-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="170ca-109">Po zadeklarowaniu prefiksu można go użyć do kwalifikowania elementów i atrybutów w dokumencie XML i kojarzenia ich z identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="170ca-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="170ca-110">Ponieważ prefiks przestrzeni nazw jest używany w całym dokumencie, powinien mieć krótki czas.</span><span class="sxs-lookup"><span data-stu-id="170ca-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="170ca-111">Ten przykład definiuje dwa `BOOK` elementy.</span><span class="sxs-lookup"><span data-stu-id="170ca-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="170ca-112">Pierwszy element jest kwalifikowana przez prefiks, `mybook` , a drugi element jest kwalifikowana przez prefiks, `bb` .</span><span class="sxs-lookup"><span data-stu-id="170ca-112">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="170ca-113">Każdy prefiks jest skojarzony z innym identyfikatorem URI przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="170ca-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 <span data-ttu-id="170ca-114">Aby wyrównać, że element jest częścią określonego obszaru nazw, Dodaj do niego prefiks przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="170ca-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="170ca-115">Na przykład jeśli `Author` element należy do `mybook` przestrzeni nazw, zostanie zadeklarowany jako `<mybook:Author>` .</span><span class="sxs-lookup"><span data-stu-id="170ca-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>
## <a name="declaration-scope"></a><span data-ttu-id="170ca-116">Zakres deklaracji</span><span class="sxs-lookup"><span data-stu-id="170ca-116">Declaration scope</span></span>  
 <span data-ttu-id="170ca-117">Przestrzeń nazw zaczyna się od jej punktu deklaracji do końca elementu, w którym został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="170ca-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="170ca-118">W tym przykładzie przestrzeń nazw zdefiniowana w `BOOK` elemencie nie ma zastosowania do elementów poza `BOOK` elementem, takich jak `Publisher` element:</span><span class="sxs-lookup"><span data-stu-id="170ca-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
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
  
 <span data-ttu-id="170ca-119">Przestrzeń nazw musi być zadeklarowana, zanim będzie można jej użyć, ale nie musi być wyświetlana u góry dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="170ca-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="170ca-120">W przypadku używania wielu przestrzeni nazw w dokumencie XML, można zdefiniować jeden obszar nazw jako domyślną przestrzeń nazw, aby utworzyć przejrzysty dokument szukania.</span><span class="sxs-lookup"><span data-stu-id="170ca-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="170ca-121">Domyślna przestrzeń nazw jest zadeklarowana w elemencie głównym i ma zastosowanie do wszystkich niekwalifikowanych elementów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="170ca-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="170ca-122">Domyślne przestrzenie nazw mają zastosowanie tylko do elementów, a nie do atrybutów.</span><span class="sxs-lookup"><span data-stu-id="170ca-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="170ca-123">Aby użyć domyślnej przestrzeni nazw, Pomiń prefiks i dwukropek z deklaracji w elemencie:</span><span class="sxs-lookup"><span data-stu-id="170ca-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="170ca-124">Zarządzanie przestrzeniami nazw</span><span class="sxs-lookup"><span data-stu-id="170ca-124">Managing namespaces</span></span>  
 <span data-ttu-id="170ca-125"><xref:System.Xml.XmlNamespaceManager>Klasa przechowuje kolekcję identyfikatorów URI przestrzeni nazw i ich prefiksów, a następnie umożliwia wyszukiwanie, Dodawanie i usuwanie przestrzeni nazw z tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="170ca-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="170ca-126">W niektórych kontekstach Ta klasa jest wymagana w celu uzyskania lepszej wydajności przetwarzania kodu XML.</span><span class="sxs-lookup"><span data-stu-id="170ca-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="170ca-127">Na przykład <xref:System.Xml.Xsl.XsltContext> Klasa używa <xref:System.Xml.XmlNamespaceManager> dla obsługi XPath.</span><span class="sxs-lookup"><span data-stu-id="170ca-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="170ca-128">Menedżer przestrzeni nazw nie wykonuje żadnych walidacji w przestrzeniach nazw, ale zakłada, że prefiksy i przestrzenie nazw zostały już zweryfikowane i są zgodne ze specyfikacją [przestrzeni nazw W3C](https://www.w3.org/TR/REC-xml-names/) .</span><span class="sxs-lookup"><span data-stu-id="170ca-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="170ca-129">LINQ TO XML w [C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) nie używać <xref:System.Xml.XmlNamespaceManager> do zarządzania przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="170ca-129">LINQ TO XML in [C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="170ca-130">Zobacz [Praca z przestrzeniami nazw XML (C#)](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) i [Praca z przestrzeniami nazw XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) w dokumentacji LINQ, aby uzyskać informacje na temat zarządzania przestrzeniami nazw przy użyciu LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="170ca-130">See [Working with XML Namespaces (C#)](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) and [Working with XML Namespaces (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="170ca-131">Poniżej przedstawiono niektóre zadania zarządzania i wyszukiwania, które można wykonać za pomocą <xref:System.Xml.XmlNamespaceManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="170ca-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="170ca-132">Aby uzyskać więcej informacji i przykładów, postępuj zgodnie z linkami do strony odniesienia dla każdej metody lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="170ca-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="170ca-133">Do</span><span class="sxs-lookup"><span data-stu-id="170ca-133">To</span></span>|<span data-ttu-id="170ca-134">Użycie</span><span class="sxs-lookup"><span data-stu-id="170ca-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="170ca-135">Dodawanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="170ca-135">Add a namespace</span></span>|<span data-ttu-id="170ca-136">Metoda <xref:System.Xml.XmlNamespaceManager.AddNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="170ca-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="170ca-137">Usuwanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="170ca-137">Remove a namespace</span></span>|<span data-ttu-id="170ca-138">Metoda <xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="170ca-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="170ca-139">Znajdź identyfikator URI dla domyślnej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="170ca-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="170ca-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A>wartość</span><span class="sxs-lookup"><span data-stu-id="170ca-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="170ca-141">Znajdź identyfikator URI dla prefiksu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="170ca-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="170ca-142">Metoda <xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="170ca-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="170ca-143">Znajdź prefiks dla identyfikatora URI przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="170ca-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="170ca-144">Metoda <xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A></span><span class="sxs-lookup"><span data-stu-id="170ca-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="170ca-145">Pobierz listę przestrzeni nazw w bieżącym węźle</span><span class="sxs-lookup"><span data-stu-id="170ca-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="170ca-146">Metoda <xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A></span><span class="sxs-lookup"><span data-stu-id="170ca-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="170ca-147">Określanie zakresu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="170ca-147">Scope a namespace</span></span>|<span data-ttu-id="170ca-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A>i <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody</span><span class="sxs-lookup"><span data-stu-id="170ca-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="170ca-149">Sprawdź, czy prefiks jest zdefiniowany w bieżącym zakresie</span><span class="sxs-lookup"><span data-stu-id="170ca-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="170ca-150">Metoda <xref:System.Xml.XmlNamespaceManager.HasNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="170ca-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="170ca-151">Pobierz tabelę nazw służącą do wyszukiwania prefiksów i identyfikatorów URI</span><span class="sxs-lookup"><span data-stu-id="170ca-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="170ca-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A>wartość</span><span class="sxs-lookup"><span data-stu-id="170ca-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="170ca-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="170ca-153">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="170ca-154">Dokumenty i dane XML</span><span class="sxs-lookup"><span data-stu-id="170ca-154">XML Documents and Data</span></span>](index.md)
