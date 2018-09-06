---
title: 'Porady: kontrolowanie prefiksów Namespace (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: dd2a91fde868425cadbc395d6db0f913e2be600f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868568"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="60cdc-102">Porady: kontrolowanie prefiksów Namespace (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="60cdc-102">How to: Control Namespace Prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="60cdc-103">W tym temacie opisano, jak kontrolować prefiksy przestrzeni nazw podczas serializacji drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="60cdc-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="60cdc-104">W wielu sytuacjach nie jest konieczne kontrolowanie prefiksów przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="60cdc-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="60cdc-105">Jednak niektórych narzędzi do programowania XML Wymagaj sterowania prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="60cdc-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="60cdc-106">Na przykład użytkownik może być manipulowanie arkusz stylów XSLT lub dokumentu XAML, który zawiera osadzone wyrażenia XPath, które odwołują się do prefiksy przestrzeni nazw określonych; w tym przypadku jest ważne, że dokument można było serializować ją przy tych prefiksów.</span><span class="sxs-lookup"><span data-stu-id="60cdc-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="60cdc-107">Jest to najbardziej typowe przyczyny kontrolowanie prefiksów przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="60cdc-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="60cdc-108">Inny typową przyczyną kontrolowanie prefiksów przestrzeni nazw jest, że użytkownicy mają ręcznie edytować dokumentu XML, a chcesz utworzyć prefiksy przestrzeni nazw, które są w dogodnym dla użytkownika o wpisanie.</span><span class="sxs-lookup"><span data-stu-id="60cdc-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="60cdc-109">Na przykład użytkownik może generować dokumentu XSD.</span><span class="sxs-lookup"><span data-stu-id="60cdc-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="60cdc-110">Konwencje dotyczące schematów sugerują, użyj jednej `xs` lub `xsd` jako prefiksu dla przestrzeni nazw schematu.</span><span class="sxs-lookup"><span data-stu-id="60cdc-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="60cdc-111">Aby kontrolować prefiksy przestrzeni nazw, należy wstawić atrybuty, które deklarują przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="60cdc-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="60cdc-112">W przypadku przestrzeni nazw z specyficzne prefiksy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podejmie próbę uznaje prefiksy przestrzeni nazw podczas serializacji.</span><span class="sxs-lookup"><span data-stu-id="60cdc-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="60cdc-113">Aby utworzyć atrybut, który deklaruje przestrzeni nazw z prefiksem, Utwórz atrybut w przypadku przestrzeni nazw nazwa atrybutu <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, a nazwą atrybutu jest prefiks przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="60cdc-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="60cdc-114">Wartość atrybutu jest identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="60cdc-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60cdc-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="60cdc-115">Example</span></span>  
 <span data-ttu-id="60cdc-116">Ten przykład deklaruje dwie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="60cdc-116">This example declares two namespaces.</span></span> <span data-ttu-id="60cdc-117">Określa, że `http://www.adventure-works.com` przestrzeń nazw ma prefiks `aw`oraz że `www.fourthcoffee.com` przestrzeń nazw ma prefiks `fc`.</span><span class="sxs-lookup"><span data-stu-id="60cdc-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="60cdc-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="60cdc-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="60cdc-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60cdc-119">See Also</span></span>

- [<span data-ttu-id="60cdc-120">Praca z przestrzeniami nazw XML (C#)</span><span class="sxs-lookup"><span data-stu-id="60cdc-120">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
