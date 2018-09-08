---
title: Refaktoryzacja przy użyciu metody rozszerzenia (C#)
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: 08c37923792e1ac6ee922bf052d39fb63b1685c7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201053"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="ee272-102">Refaktoryzacja przy użyciu metody rozszerzenia (C#)</span><span class="sxs-lookup"><span data-stu-id="ee272-102">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="ee272-103">W tym przykładzie opiera się na poprzednim przykładzie [pobieranie tekstu akapitów (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), przez refaktoryzacji łączenia ciągów przy użyciu czystej funkcji, który jest implementowany jako metodę rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ee272-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="ee272-104">W poprzednim przykładzie użyto <xref:System.Linq.Enumerable.Aggregate%2A> standardowego operatora zapytania na łączenie wielu ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="ee272-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="ee272-105">Jednak jest bardziej wygodne do zapisania metodę rozszerzenia, aby to zrobić, ponieważ wynikowy zapytania mniejsze i bardziej proste.</span><span class="sxs-lookup"><span data-stu-id="ee272-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee272-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee272-106">Example</span></span>  
 <span data-ttu-id="ee272-107">W tym przykładzie przetwarza dokumentu WordprocessingML pobieranie akapitów, styl każdego akapitu, a tekst każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="ee272-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="ee272-108">W tym przykładzie opiera się na poprzednich przykładach w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="ee272-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="ee272-109">Przykład zawiera wiele przeciążeń `StringConcatenate` metody.</span><span class="sxs-lookup"><span data-stu-id="ee272-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="ee272-110">Można znaleźć instrukcje dotyczące tworzenia dokumentu źródłowego, w tym przykładzie w [tworzenie źródłowego dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ee272-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="ee272-111">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="ee272-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="ee272-112">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ee272-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
```  
  
## <a name="example"></a><span data-ttu-id="ee272-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee272-113">Example</span></span>  
 <span data-ttu-id="ee272-114">Istnieją cztery przeciążenia `StringConcatenate` metody.</span><span class="sxs-lookup"><span data-stu-id="ee272-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="ee272-115">Kilkoma przeciążeniami po prostu kolekcji ciągów i zwraca jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="ee272-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="ee272-116">Innego przeciążenia metody może potrwać kolekcji dowolnego typu i delegata tego projektów z pojedynczego kolekcji na ciąg.</span><span class="sxs-lookup"><span data-stu-id="ee272-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="ee272-117">Istnieją dwa więcej przeciążenia metody, które pozwalają na określenie ciągu separatora.</span><span class="sxs-lookup"><span data-stu-id="ee272-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="ee272-118">W poniższym kodzie użyto wszystkie cztery przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="ee272-118">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="ee272-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ee272-119">This example produces the following output:</span></span>  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="ee272-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee272-120">Example</span></span>  
 <span data-ttu-id="ee272-121">Teraz można zmodyfikować przykładu, aby korzystać z zalet nowej metody rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="ee272-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para  
                       .ParagraphNode  
                       .Elements(w + "r")  
                       .Elements(w + "t")  
                       .StringConcatenate(e => (string)e)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="ee272-122">Ten przykład generuje następujące dane wyjściowe po zastosowaniu do dokumentu opisano w [tworzenie źródłowego dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ee272-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="ee272-123">Należy pamiętać, że ta Refaktoryzacja jest wariant Refaktoryzacja do czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="ee272-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="ee272-124">Następny temat przedstawiono koncepcję wyprowadzenie do czystych funkcji bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="ee272-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ee272-125">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ee272-125">Next Steps</span></span>  
 <span data-ttu-id="ee272-126">W kolejnym przykładzie pokazano sposób Refaktoryzuj ten kod w inny sposób, przy użyciu czystej funkcji:</span><span class="sxs-lookup"><span data-stu-id="ee272-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
-   [<span data-ttu-id="ee272-127">Refaktoryzacja przy użyciu czystej funkcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee272-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee272-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee272-128">See Also</span></span>

- [<span data-ttu-id="ee272-129">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="ee272-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
- [<span data-ttu-id="ee272-130">Refaktoryzacja do czystych funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="ee272-130">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
