---
title: 'Porady: modyfikowanie dokumentu pakietu Office Open XML (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 467d489c-2b1b-453b-a757-8ac180e82a96
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a6bfa60cce332deef2a72da836f96dbe37e65d2a
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2018
---
# <a name="how-to-modify-an-office-open-xml-document-c"></a><span data-ttu-id="9aa44-102">Porady: modyfikowanie dokumentu pakietu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9aa44-102">How to: Modify an Office Open XML Document (C#)</span></span>
<span data-ttu-id="9aa44-103">W tym temacie przedstawiono przykład otwiera dokumentu pakietu Office Open XML, modyfikuje go i zapisuje go.</span><span class="sxs-lookup"><span data-stu-id="9aa44-103">This topic presents an example that opens an Office Open XML document, modifies it, and saves it.</span></span>  
  
 <span data-ttu-id="9aa44-104">Aby uzyskać więcej informacji dotyczących Office Open XML, zobacz [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) i [www.ericwhite.com](http://ericwhite.com/).</span><span class="sxs-lookup"><span data-stu-id="9aa44-104">For more information on Office Open XML, see [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) and [www.ericwhite.com](http://ericwhite.com/).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aa44-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="9aa44-105">Example</span></span>  
 <span data-ttu-id="9aa44-106">W tym przykładzie znajduje pierwszy element akapitu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9aa44-106">This example finds the first paragraph element in the document.</span></span> <span data-ttu-id="9aa44-107">Go odczytuje tekst z akapitu, a następnie usuwa cały tekst jest uruchamiany w akapitu.</span><span class="sxs-lookup"><span data-stu-id="9aa44-107">It retrieves the text from the paragraph, and then deletes all text runs in the paragraph.</span></span> <span data-ttu-id="9aa44-108">Tworzy nowy tekst Uruchom składający się z pierwszym tekst akapitu, który został przekonwertowany na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="9aa44-108">It creates a new text run that consists of the first paragraph text that has been converted to upper case.</span></span> <span data-ttu-id="9aa44-109">Następnie serializuje zmienione XML w pakiecie Open XML i zamyka.</span><span class="sxs-lookup"><span data-stu-id="9aa44-109">It then serializes the changed XML into the Open XML package and closes it.</span></span>  
  
 <span data-ttu-id="9aa44-110">W tym przykładzie użyto znaleziony w zestawie WindowsBase klasy.</span><span class="sxs-lookup"><span data-stu-id="9aa44-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="9aa44-111">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9aa44-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace =  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                XDocument xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                PackagePart stylePart = null;  
                XDocument styleDoc = null;  
  
                if (styleRelation != null)  
                {  
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
  
                XElement paraNode = xDoc  
                                    .Root  
                                    .Element(w + "body")  
                                    .Descendants(w + "p")  
                                    .FirstOrDefault();  
  
                string paraText = ParagraphText(paraNode);  
  
                // remove all text runs  
                paraNode.Descendants(w + "r").Remove();  
  
                paraNode.Add(  
                    new XElement(w + "r",  
                        new XElement(w + "t", paraText.ToUpper())  
                    )  
                );  
  
                //  Save the XML into the package  
                using (XmlWriter xw =  
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write)))  
                {  
                    xDoc.Save(xw);  
                }  
  
                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper());  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="9aa44-112">Po otwarciu `SampleDoc.docx` po uruchomieniu tego programu, zobaczysz, że ten program przekonwertować akapitu w dokumencie wielkimi literami.</span><span class="sxs-lookup"><span data-stu-id="9aa44-112">If you open `SampleDoc.docx` after running this program, you can see that this program converted the first paragraph in the document to upper case.</span></span>  
  
 <span data-ttu-id="9aa44-113">Uruchomienia z przykładowy dokument Open XML opisanego w [tworzenie źródło dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), w tym przykładzie tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="9aa44-113">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```  
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<  
```  
  
## <a name="see-also"></a><span data-ttu-id="9aa44-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9aa44-114">See Also</span></span>  
 [<span data-ttu-id="9aa44-115">Zaawansowane techniki zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9aa44-115">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
