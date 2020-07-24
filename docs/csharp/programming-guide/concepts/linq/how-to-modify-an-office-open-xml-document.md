---
title: Jak zmodyfikować dokument Office Open XML (C#)
description: Dowiedz się, jak otworzyć dokument pakietu Office Open XML, zmodyfikować go i zapisać. Ten przykład w języku C# używa klas znalezionych w zestawie 'Windowsbase.
ms.date: 07/20/2015
ms.assetid: 467d489c-2b1b-453b-a757-8ac180e82a96
ms.openlocfilehash: 1155851696a0a6ed651c5f84290a3879e73276db
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104818"
---
# <a name="how-to-modify-an-office-open-xml-document-c"></a><span data-ttu-id="f6fe8-104">Jak zmodyfikować dokument Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f6fe8-104">How to modify an Office Open XML document (C#)</span></span>
<span data-ttu-id="f6fe8-105">W tym temacie przedstawiono przykład, który powoduje otwarcie dokumentu Office Open XML, zmodyfikowanie go i zapisanie.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-105">This topic presents an example that opens an Office Open XML document, modifies it, and saves it.</span></span>  
  
 <span data-ttu-id="f6fe8-106">Aby uzyskać więcej informacji na temat pakietu Office Open XML, zobacz [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) i [www.ericwhite.com](http://ericwhite.com/).</span><span class="sxs-lookup"><span data-stu-id="f6fe8-106">For more information on Office Open XML, see [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) and [www.ericwhite.com](http://ericwhite.com/).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6fe8-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6fe8-107">Example</span></span>  
 <span data-ttu-id="f6fe8-108">Ten przykład umożliwia znalezienie pierwszego elementu akapitu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-108">This example finds the first paragraph element in the document.</span></span> <span data-ttu-id="f6fe8-109">Pobiera tekst z akapitu, a następnie usuwa wszystkie uruchomienia tekstu w akapicie.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-109">It retrieves the text from the paragraph, and then deletes all text runs in the paragraph.</span></span> <span data-ttu-id="f6fe8-110">Tworzy nowe uruchomienie tekstu, które składa się z pierwszego tekstu akapitu, który został przekonwertowany na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-110">It creates a new text run that consists of the first paragraph text that has been converted to upper case.</span></span> <span data-ttu-id="f6fe8-111">Następnie program serializacji zmieniony kod XML do otwartego pakietu XML i zamyka go.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-111">It then serializes the changed XML into the Open XML package and closes it.</span></span>  
  
 <span data-ttu-id="f6fe8-112">Ten przykład używa klas znalezionych w zestawie 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-112">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="f6fe8-113">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-113">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="f6fe8-114">Jeśli otworzysz `SampleDoc.docx` po uruchomieniu tego programu, możesz zobaczyć, że ten program przekonwertował pierwszy akapit w dokumencie na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-114">If you open `SampleDoc.docx` after running this program, you can see that this program converted the first paragraph in the document to upper case.</span></span>  
  
 <span data-ttu-id="f6fe8-115">W przypadku uruchomienia z przykładowym otwartym dokumentem XML opisanym w temacie [Tworzenie źródłowego dokumentu Office Open XML (C#)](./creating-the-source-office-open-xml-document.md)ten przykład generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f6fe8-115">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```output  
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<  
```  
