---
title: Jak przeanalizować ciąg (C#)
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 79821eb9e5cd7187ac3c2a93f85eaae45c5c48ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345812"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="26590-102">Jak przeanalizować ciąg (C#)</span><span class="sxs-lookup"><span data-stu-id="26590-102">How to parse a string (C#)</span></span>

<span data-ttu-id="26590-103">W tym temacie pokazano, jak przeanalizować ciąg w celu utworzenia drzewa C#XML w.</span><span class="sxs-lookup"><span data-stu-id="26590-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="26590-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="26590-104">Example</span></span>

<span data-ttu-id="26590-105">Poniższy C# kod ilustruje sposób analizowania ciągu XML:</span><span class="sxs-lookup"><span data-stu-id="26590-105">The following C# code shows how to parse an XML string:</span></span>

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type=""mobile"">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>");
Console.WriteLine(contacts);
```

<span data-ttu-id="26590-106">Węzeł główny `Contacts` ma dwa węzły `Contact`.</span><span class="sxs-lookup"><span data-stu-id="26590-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="26590-107">Aby uzyskać dostęp do określonych danych w analizowanym formacie XML, należy użyć metody [XElement. elementy ()](xref:System.Xml.Linq.XContainer.Elements) , która w tym przypadku zwraca elementy podrzędne głównego węzła `Contacts`.</span><span class="sxs-lookup"><span data-stu-id="26590-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="26590-108">Poniższy przykład drukuje pierwszy węzeł `Contact` w konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="26590-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="26590-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26590-109">See also</span></span>

- [<span data-ttu-id="26590-110">Jak znaleźć element z określonym atrybutem (C#)</span><span class="sxs-lookup"><span data-stu-id="26590-110">How to find an element with a specific attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)
