---
title: Zakres domyślnych przestrzeni nazw w języku C# 1
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: bb0e111bfded0769c498b116f828711003036e33
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510442"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="3cc96-102">Zakres domyślnych przestrzeni nazw w języku C#</span><span class="sxs-lookup"><span data-stu-id="3cc96-102">Scope of Default Namespaces in C#</span></span>
<span data-ttu-id="3cc96-103">Domyślne obszary nazw, reprezentowany w drzewie XML nie są uwzględnione w zakresie zapytania.</span><span class="sxs-lookup"><span data-stu-id="3cc96-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="3cc96-104">Jeśli masz plik XML, który znajduje się w domyślnej przestrzeni nazw, nadal należy zadeklarować <xref:System.Xml.Linq.XNamespace> zmienną i łączą je z nazwą lokalną, można utworzyć kwalifikowane nazwy ma być używany w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="3cc96-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="3cc96-105">Jedną z najbardziej typowych problemów podczas wykonywania zapytań dotyczących drzew XML jest, że jeśli drzewa XML ma domyślny obszar nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie znajdowały się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3cc96-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="3cc96-106">Pierwszy zestaw przykładów w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest ładowany, że jest nieprawidłowo wysyłane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="3cc96-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="3cc96-107">Drugi zestaw przykładach pokazano niezbędnych poprawek, dzięki czemu można tworzyć zapytania XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3cc96-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cc96-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cc96-108">Example</span></span>  
 <span data-ttu-id="3cc96-109">W tym przykładzie pokazano tworzenie obiektu XML w przestrzeni nazw i ustaw zapytania, które zwraca żadnego wyniku.</span><span class="sxs-lookup"><span data-stu-id="3cc96-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3cc96-110">Kod</span><span class="sxs-lookup"><span data-stu-id="3cc96-110">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a><span data-ttu-id="3cc96-111">Komentarze</span><span class="sxs-lookup"><span data-stu-id="3cc96-111">Comments</span></span>  
 <span data-ttu-id="3cc96-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3cc96-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="3cc96-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cc96-113">Example</span></span>  
 <span data-ttu-id="3cc96-114">W tym przykładzie pokazano tworzenie obiektu XML w przestrzeni nazw i zapytanie, które są poprawnie kodowane.</span><span class="sxs-lookup"><span data-stu-id="3cc96-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="3cc96-115">W przeciwieństwie do kodowane niepoprawnie powyższym przykładzie właściwe podejście przy użyciu języka C# jest zadeklarowania i zainicjowania <xref:System.Xml.Linq.XNamespace> obiektu i z niej korzystać, podczas określania <xref:System.Xml.Linq.XName> obiektów.</span><span class="sxs-lookup"><span data-stu-id="3cc96-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="3cc96-116">W tym przypadku argument <xref:System.Xml.Linq.XElement.Elements%2A> metodą jest <xref:System.Xml.Linq.XName> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3cc96-116">In this case, the argument to the <xref:System.Xml.Linq.XElement.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3cc96-117">Kod</span><span class="sxs-lookup"><span data-stu-id="3cc96-117">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a><span data-ttu-id="3cc96-118">Komentarze</span><span class="sxs-lookup"><span data-stu-id="3cc96-118">Comments</span></span>  
 <span data-ttu-id="3cc96-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3cc96-119">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cc96-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3cc96-120">See Also</span></span>

- [<span data-ttu-id="3cc96-121">Praca z przestrzeniami nazw XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3cc96-121">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
