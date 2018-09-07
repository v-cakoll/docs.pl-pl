---
title: Wczytywanie dokumentu XML do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9031f5df0d0f48dc2844cdfd0654ee4ab876cc22
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44046005"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="45cab-102">Wczytywanie dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="45cab-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="45cab-103">Informacje o XML jest do odczytu do pamięci z różnych formatów.</span><span class="sxs-lookup"><span data-stu-id="45cab-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="45cab-104">Może być odczytany z ciągu, strumienia, adres URL, czytnika tekstu lub klasę pochodną <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="45cab-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="45cab-105"><xref:System.Xml.XmlDocument.Load%2A> Metoda udostępnia dokument do pamięci i ma skonfigurowane przeciążone metody dostępne dla pobierają dane z każdego z różnych formatów.</span><span class="sxs-lookup"><span data-stu-id="45cab-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="45cab-106">Istnieje również <xref:System.Xml.XmlDocument.LoadXml%2A> metodę, która odczytuje XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="45cab-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="45cab-107">Różne <xref:System.Xml.XmlDocument.Load%2A> metody wpływają na węzły, które są tworzone po załadowaniu XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="45cab-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="45cab-108">W poniższej tabeli przedstawiono różnice między część <xref:System.Xml.XmlDocument.Load%2A> metody i tematy, które ich dotyczą.</span><span class="sxs-lookup"><span data-stu-id="45cab-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="45cab-109">Temat</span><span class="sxs-lookup"><span data-stu-id="45cab-109">Subject</span></span>|<span data-ttu-id="45cab-110">Temat</span><span class="sxs-lookup"><span data-stu-id="45cab-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="45cab-111">Tworzenie węzły odstępów</span><span class="sxs-lookup"><span data-stu-id="45cab-111">Creation of white space nodes</span></span>|<span data-ttu-id="45cab-112">Obiekt używany do załadowania modelu DOM ma to wpływu na biały i istotnych białych węzłów generowane w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="45cab-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="45cab-113">Aby uzyskać więcej informacji, zobacz [biały znak i znaczące biały znak obsługi podczas ładowania modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="45cab-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="45cab-114">Podczas ładowania XML, zaczynając od określonego węzła lub ładowania całego dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="45cab-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="45cab-115">Za pomocą <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> danych metody mogą być ładowane z określonego węzła do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="45cab-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="45cab-116">Aby uzyskać więcej informacji, zobacz [ładowanie danych z czytnika](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="45cab-116">For more information, see [Load Data from a Reader](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="45cab-117">Walidacja kodu XML w postaci, w jakiej jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="45cab-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="45cab-118">Mogą być sprawdzone dane XML załadowane do modelu DOM, ponieważ jest on ładowany.</span><span class="sxs-lookup"><span data-stu-id="45cab-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="45cab-119">Jest to realizowane przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="45cab-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="45cab-120">Aby uzyskać więcej informacji na temat sprawdzania poprawności XML, ponieważ jest on ładowany zobacz [Weryfikowanie dokumentu XML w modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="45cab-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="45cab-121">W poniższym przykładzie pokazano XML ładowany z <xref:System.Xml.XmlDocument.LoadXml%2A> metody i danych, następnie zapisywane do pliku tekstowego o nazwie `data.xml`.</span><span class="sxs-lookup"><span data-stu-id="45cab-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="45cab-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45cab-122">See also</span></span>

- [<span data-ttu-id="45cab-123">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="45cab-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
