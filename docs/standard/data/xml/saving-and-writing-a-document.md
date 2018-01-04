---
title: Zapisywanie i zapisywania dokumentu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2138b9c47c6e41cd94e775eaed005d8a6fd976c9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="cc6b3-102">Zapisywanie i zapisywania dokumentu</span><span class="sxs-lookup"><span data-stu-id="cc6b3-102">Saving and Writing a Document</span></span>
<span data-ttu-id="cc6b3-103">Podczas ładowania i zapisać <xref:System.Xml.XmlDocument>, zapisanego dokumentu może różnić się od oryginału w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cc6b3-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
-   <span data-ttu-id="cc6b3-104">Jeśli <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> właściwość jest ustawiona na `true` przed <xref:System.Xml.XmlDocument.Save%2A> metoda jest wywoływana, biały znak w dokumencie są zachowywane w danych wyjściowych; Jeśli ta właściwość jest `false`, <xref:System.Xml.XmlDocument> wcięć automatycznie dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
-   <span data-ttu-id="cc6b3-105">Wszystkie biały znak między atrybutami, zostanie zmniejszona do pojedynczego spacją.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
-   <span data-ttu-id="cc6b3-106">Biały znak między elementami zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-106">The white space between elements is changed.</span></span> <span data-ttu-id="cc6b3-107">Znaczący biały znak są zachowywane i nie jest nieważny biały znak.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="cc6b3-108">Po zapisaniu dokumentu zostanie użyty, ale <xref:System.Xml.XmlTextWriter> **Indenting** tryb domyślnie starannie wydrukować dane wyjściowe, aby był bardziej czytelny.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
-   <span data-ttu-id="cc6b3-109">Znak cudzysłowu wokół wartości atrybutu jest zmieniany na podwójnego cudzysłowu domyślnie.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="cc6b3-110">Można użyć <xref:System.Xml.XmlTextReader.QuoteChar%2A> właściwość <xref:System.Xml.XmlTextWriter> można ustawić znaku cudzysłowu podwójnego cudzysłowu lub pojedynczy cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
-   <span data-ttu-id="cc6b3-111">Domyślnie, takich jak jednostki znaku numerycznego `{` zostaną rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
-   <span data-ttu-id="cc6b3-112">Znacznik kolejności bajtów w dokument wejściowy nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="cc6b3-113">UCS-2 jest zapisywany jako UTF-8, chyba że jawnie tworzenia deklaracji XML, który określa inne kodowanie.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
-   <span data-ttu-id="cc6b3-114">Jeśli chcesz zapisać <xref:System.Xml.XmlDocument> do pliku lub strumienia wyjściowego zapisany jest taka sama jak zawartość dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="cc6b3-115">Oznacza to, że <xref:System.Xml.XmlDeclaration> jest zapisywane tylko jeśli jest zawarte w dokumencie i kodowanie używane podczas zapisywania dokumentu jest tej samej kodowanie podane w węźle deklaracji.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="cc6b3-116">Zapisywanie XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="cc6b3-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="cc6b3-117"><xref:System.Xml.XmlDocument> i <xref:System.Xml.XmlDeclaration> członkami <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, i <xref:System.Xml.XmlNode.WriteTo%2A>, oprócz <xref:System.Xml.XmlDocument> metody <xref:System.Xml.XmlDocument.Save%2A> i <xref:System.Xml.XmlDocument.WriteContentTo%2A>, Utwórz deklarację XML.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="cc6b3-118">Dla <xref:System.Xml.XmlDocument> właściwości <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>i <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, i <xref:System.Xml.XmlDocument.WriteContentTo%2A> metod, kodowanie zapisana w deklaracji XML jest pobierana z <xref:System.Xml.XmlDeclaration> węzła.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="cc6b3-119">W przypadku nie <xref:System.Xml.XmlDeclaration> węzła, <xref:System.Xml.XmlDeclaration> nie jest zapisywany. Jeśli istnieje bez kodowania w <xref:System.Xml.XmlDeclaration> węzła, kodowanie jest nie zapisana w deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="cc6b3-120"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> i <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> metody zawsze zapisać <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="cc6b3-121">Te metody przyjmują kodowaniem edytor, który jest zapisywania.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="cc6b3-122">Oznacza to, że wartość kodowania w edytorze zastępuje kodowania dokumentu, a następnie w <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="cc6b3-123">Na przykład następujący kod nie zapisuje kodowanie w deklaracji XML znaleziono w pliku wyjściowym `out.xml`.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="cc6b3-124">Dla <xref:System.Xml.XmlDocument.Save%2A> metody deklaracja XML jest zapisywany przy użyciu <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda <xref:System.Xml.XmlWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="cc6b3-125">W związku z tym zastępowanie <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda zmienia sposób zapisywania początku dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="cc6b3-126">Dla <xref:System.Xml.XmlDeclaration> członkami <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, i <xref:System.Xml.XmlNode.InnerXml%2A>, jeśli <xref:System.Xml.XmlDeclaration.Encoding%2A> właściwość nie jest ustawiona, bez kodowania jest zapisywany. W przeciwnym razie kodowanie zapisana w deklaracji XML jest taki sam jak kodowanie znalezione w <xref:System.Xml.XmlDeclaration.Encoding%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="cc6b3-127">Zapisywanie zawartości dokumentu za pomocą właściwości OuterXml</span><span class="sxs-lookup"><span data-stu-id="cc6b3-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="cc6b3-128"><xref:System.Xml.XmlNode.OuterXml%2A> Właściwości to rozszerzenie Microsoft standardy sieci World Wide Web konsorcjum W3C XML modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="cc6b3-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="cc6b3-129"><xref:System.Xml.XmlNode.OuterXml%2A> Właściwość jest używana do pobrania znaczników całego dokumentu w formacie XML lub po prostu znaczników jeden węzeł i jego podrzędny węzłów.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="cc6b3-130"><xref:System.Xml.XmlNode.OuterXml%2A>Zwraca kod znaczników reprezentujący Podany węzeł i wszystkich jego węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="cc6b3-131">Poniższy przykładowy kod przedstawia sposób zapisywania dokumentu w całości w postaci ciągu.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="cc6b3-132">Poniższy przykład kodu pokazuje, jak zapisać element dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="cc6b3-133">Z kolei umożliwia <xref:System.Xml.XmlNode.InnerText%2A> właściwości, jeśli chcesz, aby zawartość węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="cc6b3-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6b3-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc6b3-134">See Also</span></span>  
 [<span data-ttu-id="cc6b3-135">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="cc6b3-135">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
