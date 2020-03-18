---
title: Jak kontrolować prefiksy obszaru nazw (C#) (LINQ do XML)
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 9f43c0804d8c830fa75f1e1390cb578c5f5d5106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141380"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="12565-102">Jak kontrolować prefiksy obszaru nazw (C#) (LINQ do XML)</span><span class="sxs-lookup"><span data-stu-id="12565-102">How to control namespace prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="12565-103">W tym temacie opisano, jak można kontrolować prefiksy obszaru nazw podczas serializacji drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="12565-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="12565-104">W wielu sytuacjach nie jest konieczne kontrolowanie prefiksów obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="12565-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="12565-105">Jednak niektóre narzędzia programowania XML wymagają określonej kontroli prefiksów obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="12565-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="12565-106">Na przykład może być manipulowanie arkusz emitujący style XSLT lub dokument XAML zawierający osadzone wyrażenia XPath, które odwołują się do prefiksów określonych przestrzeni nazw; w takim przypadku ważne jest, aby dokument był serializowany z tymi określonymi prefiksami.</span><span class="sxs-lookup"><span data-stu-id="12565-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="12565-107">Jest to najczęstsza przyczyna kontrolowania prefiksów obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="12565-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="12565-108">Inną częstą przyczyną kontrolowania prefiksów obszaru nazw jest ręczne edytowanie dokumentu XML przez użytkowników i tworzenie prefiksów obszaru nazw, które są wygodne dla użytkownika do wpisania.</span><span class="sxs-lookup"><span data-stu-id="12565-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="12565-109">Na przykład może być generowanie dokumentu XSD.</span><span class="sxs-lookup"><span data-stu-id="12565-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="12565-110">Konwencje dotyczące schematów sugerują, że `xs` `xsd` używasz jednego lub prefiksu obszaru nazw schematu.</span><span class="sxs-lookup"><span data-stu-id="12565-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="12565-111">Aby sterować prefiksami obszaru nazw, należy wstawić atrybuty, które deklarują obszary nazw.</span><span class="sxs-lookup"><span data-stu-id="12565-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="12565-112">Jeśli deklarujesz przestrzenie nazw z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] określonymi prefiksami, spróbuje honorować prefiksy obszaru nazw podczas serializacji.</span><span class="sxs-lookup"><span data-stu-id="12565-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="12565-113">Aby utworzyć atrybut, który deklaruje obszar nazw z prefiksem, należy utworzyć atrybut, <xref:System.Xml.Linq.XNamespace.Xmlns%2A>w którym znajduje się obszar nazw atrybutu, a nazwa atrybutu jest prefiksem obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="12565-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="12565-114">Wartość atrybutu jest identyfikator URI obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="12565-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12565-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="12565-115">Example</span></span>  
 <span data-ttu-id="12565-116">W tym przykładzie zadeklarowane są dwie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="12565-116">This example declares two namespaces.</span></span> <span data-ttu-id="12565-117">Określa, że `http://www.adventure-works.com` obszar nazw ma prefiks `aw`, `www.fourthcoffee.com` i że obszar `fc`nazw ma prefiks .</span><span class="sxs-lookup"><span data-stu-id="12565-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
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
  
 <span data-ttu-id="12565-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="12565-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="12565-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12565-119">See also</span></span>

- [<span data-ttu-id="12565-120">Omówienie przestrzeni nazw (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="12565-120">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
