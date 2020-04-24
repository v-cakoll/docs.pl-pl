---
title: Wczytywanie dokumentu XML do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 2e61a9ed1a1ccaa2f9f1543efa1d33c3fcf00061
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130829"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="aae39-102">Wczytywanie dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="aae39-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="aae39-103">Informacje XML są odczytywane w pamięci z różnych formatów.</span><span class="sxs-lookup"><span data-stu-id="aae39-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="aae39-104">Można go odczytać z ciągu, strumienia, adresu URL, czytnika tekstu lub klasy pochodnej <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="aae39-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="aae39-105"><xref:System.Xml.XmlDocument.Load%2A> Metoda przenosi dokument do pamięci i ma dostępne przeciążone metody, aby pobrać dane z każdego z różnych formatów.</span><span class="sxs-lookup"><span data-stu-id="aae39-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="aae39-106">Istnieje również <xref:System.Xml.XmlDocument.LoadXml%2A> Metoda, która odczytuje dane XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="aae39-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="aae39-107">Różne <xref:System.Xml.XmlDocument.Load%2A> metody mają wpływ na to, które węzły są tworzone podczas ładowania Document Object Model XML (dom).</span><span class="sxs-lookup"><span data-stu-id="aae39-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="aae39-108">W poniższej tabeli wymieniono różnice między niektórymi <xref:System.Xml.XmlDocument.Load%2A> metodami i tematami.</span><span class="sxs-lookup"><span data-stu-id="aae39-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="aae39-109">Podmiot</span><span class="sxs-lookup"><span data-stu-id="aae39-109">Subject</span></span>|<span data-ttu-id="aae39-110">Temat</span><span class="sxs-lookup"><span data-stu-id="aae39-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="aae39-111">Tworzenie białych węzłów spacji</span><span class="sxs-lookup"><span data-stu-id="aae39-111">Creation of white space nodes</span></span>|<span data-ttu-id="aae39-112">Obiekt użyty do załadowania modelu DOM ma wpływ na białe miejsce i znaczące węzły odstępu wygenerowane w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="aae39-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="aae39-113">Aby uzyskać więcej informacji, zobacz [biały znak i znaczący biały znak podczas ładowania modelu dom](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="aae39-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="aae39-114">Ładowanie kodu XML począwszy od określonego węzła lub ładowanie całego dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="aae39-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="aae39-115">Za pomocą <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> danych metody można ładować z określonego węzła do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="aae39-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="aae39-116">Aby uzyskać więcej informacji, zobacz [ładowanie danych z czytnika](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="aae39-116">For more information, see [Load Data from a Reader](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="aae39-117">Sprawdzanie poprawności kodu XML w trakcie jego ładowania</span><span class="sxs-lookup"><span data-stu-id="aae39-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="aae39-118">Dane XML ładowane do modelu DOM mogą być zweryfikowane w miarę ich ładowania.</span><span class="sxs-lookup"><span data-stu-id="aae39-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="aae39-119">Jest to realizowane przy użyciu walidacji <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="aae39-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="aae39-120">Aby uzyskać więcej informacji na temat walidacji kodu XML w trakcie jego ładowania, zobacz [Walidacja dokumentu XML w modelu dom](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="aae39-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="aae39-121">Poniższy przykład pokazuje, <xref:System.Xml.XmlDocument.LoadXml%2A> że kod XML jest ładowany przy użyciu metody, a dane są następnie zapisywane w pliku `data.xml`tekstowym o nazwie.</span><span class="sxs-lookup"><span data-stu-id="aae39-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="aae39-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aae39-122">See also</span></span>

- [<span data-ttu-id="aae39-123">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="aae39-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
