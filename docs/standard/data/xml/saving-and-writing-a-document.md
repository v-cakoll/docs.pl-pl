---
title: Zapisywanie dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 40d031c06f0b76668a634fac46b8defccce62f01
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289047"
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="e5e47-102">Zapisywanie dokumentu</span><span class="sxs-lookup"><span data-stu-id="e5e47-102">Saving and Writing a Document</span></span>
<span data-ttu-id="e5e47-103">Podczas ładowania i zapisywania <xref:System.Xml.XmlDocument> , zapisany dokument może różnić się od oryginału w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e5e47-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
- <span data-ttu-id="e5e47-104">Jeśli <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> Właściwość jest ustawiona na `true` przed <xref:System.Xml.XmlDocument.Save%2A> wywołaniem metody, biały znak w dokumencie jest zachowywany w danych wyjściowych; Jeśli ta właściwość ma wartość `false` , <xref:System.Xml.XmlDocument> Funkcja autowcięć wyprowadza dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e5e47-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
- <span data-ttu-id="e5e47-105">Wszystkie odstępy między atrybutami są skracane do pojedynczego znaku spacji.</span><span class="sxs-lookup"><span data-stu-id="e5e47-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
- <span data-ttu-id="e5e47-106">Odstęp między elementami jest zmieniany.</span><span class="sxs-lookup"><span data-stu-id="e5e47-106">The white space between elements is changed.</span></span> <span data-ttu-id="e5e47-107">Znaczący biały znak jest zachowywany i nieznaczący biały znak nie jest.</span><span class="sxs-lookup"><span data-stu-id="e5e47-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="e5e47-108">Ale gdy dokument zostanie zapisany, będzie używać <xref:System.Xml.XmlTextWriter> trybu **wcięć** domyślnie, aby starannie drukować dane wyjściowe, aby zwiększyć jego czytelność.</span><span class="sxs-lookup"><span data-stu-id="e5e47-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
- <span data-ttu-id="e5e47-109">Znak cudzysłowu używany wokół wartości atrybutów jest domyślnie zmieniany na podwójny cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="e5e47-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="e5e47-110">Można użyć <xref:System.Xml.XmlTextReader.QuoteChar%2A> właściwości w <xref:System.Xml.XmlTextWriter> celu ustawienia znaku cudzysłowu na podwójny cudzysłów lub pojedynczy cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="e5e47-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
- <span data-ttu-id="e5e47-111">Domyślnie jednostki znaków numerycznych, takie jak `{` są rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="e5e47-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
- <span data-ttu-id="e5e47-112">Znacznik kolejności bajtów znaleziony w dokumencie wejściowym nie jest zachowywany.</span><span class="sxs-lookup"><span data-stu-id="e5e47-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="e5e47-113">KOD UCS-2 jest zapisywany jako UTF-8, chyba że jawnie utworzysz deklarację XML, która określa inne kodowanie.</span><span class="sxs-lookup"><span data-stu-id="e5e47-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
- <span data-ttu-id="e5e47-114">Jeśli chcesz zapisać do <xref:System.Xml.XmlDocument> pliku lub strumienia, wypisane dane wyjściowe są takie same jak zawartość dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e5e47-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="e5e47-115">Oznacza to, że <xref:System.Xml.XmlDeclaration> jest napisane tylko wtedy, gdy znajduje się w dokumencie, a kodowanie używane podczas pisania dokumentu jest tym samym kodowaniem, które znajduje się w węźle deklaracji.</span><span class="sxs-lookup"><span data-stu-id="e5e47-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="e5e47-116">Pisanie xmldeklaracji</span><span class="sxs-lookup"><span data-stu-id="e5e47-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="e5e47-117"><xref:System.Xml.XmlDocument>I <xref:System.Xml.XmlDeclaration> elementy członkowskie <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlNode.InnerXml%2A> , i <xref:System.Xml.XmlNode.WriteTo%2A> , oprócz <xref:System.Xml.XmlDocument> metod <xref:System.Xml.XmlDocument.Save%2A> i <xref:System.Xml.XmlDocument.WriteContentTo%2A> , tworzą deklarację XML.</span><span class="sxs-lookup"><span data-stu-id="e5e47-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="e5e47-118">Dla <xref:System.Xml.XmlDocument> właściwości <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDocument.InnerXml%2A> , i metody,, <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.WriteTo%2A> i,,, i,,, i,,,,,,,, i,,,,,,,,, i, <xref:System.Xml.XmlDocument.WriteContentTo%2A> są pobierane <xref:System.Xml.XmlDeclaration></span><span class="sxs-lookup"><span data-stu-id="e5e47-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="e5e47-119">Jeśli nie ma <xref:System.Xml.XmlDeclaration> węzła, <xref:System.Xml.XmlDeclaration> nie jest zapisywana. Jeśli w węźle nie ma kodowania <xref:System.Xml.XmlDeclaration> , kodowanie nie jest zapisywane w deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="e5e47-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="e5e47-120"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType>Metody i <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> zawsze zapisują <xref:System.Xml.XmlDeclaration> .</span><span class="sxs-lookup"><span data-stu-id="e5e47-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="e5e47-121">Te metody przyjmują kodowanie z składnika zapisywania, do którego się zapisuje.</span><span class="sxs-lookup"><span data-stu-id="e5e47-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="e5e47-122">Oznacza to, że wartość kodowania w składniku zapisywania zastępuje kodowanie w dokumencie i w <xref:System.Xml.XmlDeclaration> .</span><span class="sxs-lookup"><span data-stu-id="e5e47-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="e5e47-123">Na przykład poniższy kod nie zapisuje kodowania w deklaracji XML, która znajduje się w pliku wyjściowym `out.xml` .</span><span class="sxs-lookup"><span data-stu-id="e5e47-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
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
  
 <span data-ttu-id="e5e47-124">Dla <xref:System.Xml.XmlDocument.Save%2A> metody, deklaracja XML jest zapisywana przy użyciu <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metody w <xref:System.Xml.XmlWriter> klasie.</span><span class="sxs-lookup"><span data-stu-id="e5e47-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="e5e47-125">W związku z tym, zastąpienie <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metody powoduje zmianę sposobu zapisywania początku dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e5e47-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="e5e47-126">W przypadku <xref:System.Xml.XmlDeclaration> elementów członkowskich <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDeclaration.WriteTo%2A> , i <xref:System.Xml.XmlNode.InnerXml%2A> , jeśli <xref:System.Xml.XmlDeclaration.Encoding%2A> Właściwość nie jest ustawiona, kodowanie nie jest zapisywana. W przeciwnym razie kodowanie wpisane w deklaracji XML jest takie samo jak kodowanie znalezione we <xref:System.Xml.XmlDeclaration.Encoding%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5e47-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="e5e47-127">Zapisywanie zawartości dokumentu przy użyciu właściwości OuterXml</span><span class="sxs-lookup"><span data-stu-id="e5e47-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="e5e47-128"><xref:System.Xml.XmlNode.OuterXml%2A>Właściwość jest rozszerzeniem Microsoft dla standardów Document Object Model XML (organizacja World Wide Web Consortium W3C).</span><span class="sxs-lookup"><span data-stu-id="e5e47-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="e5e47-129"><xref:System.Xml.XmlNode.OuterXml%2A>Właściwość służy do uzyskiwania adiustacji całego dokumentu XML lub tylko znaczników jednego węzła i jego węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e5e47-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="e5e47-130"><xref:System.Xml.XmlNode.OuterXml%2A>zwraca znacznik reprezentujący dany węzeł i wszystkie jego węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="e5e47-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="e5e47-131">Poniższy przykład kodu pokazuje, jak zapisać dokument w całości jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="e5e47-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
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
  
 <span data-ttu-id="e5e47-132">Poniższy przykład kodu pokazuje, jak zapisać tylko element dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e5e47-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="e5e47-133">Z kolei można użyć <xref:System.Xml.XmlNode.InnerText%2A> właściwości, jeśli chcesz, aby zawartość węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e5e47-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e47-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5e47-134">See also</span></span>

- [<span data-ttu-id="e5e47-135">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="e5e47-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
