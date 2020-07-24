---
title: Jak analizować ciąg (C#)
description: Dowiedz się, jak analizować ciąg w celu utworzenia drzewa XML w języku C#. Dowiedz się, jak uzyskać dostęp do określonych danych w analizowanym formacie XML.
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: a4664e090b6a44c52c519e61b66ccdc5d59a71f1
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104814"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="d5638-104">Jak analizować ciąg (C#)</span><span class="sxs-lookup"><span data-stu-id="d5638-104">How to parse a string (C#)</span></span>

<span data-ttu-id="d5638-105">W tym temacie pokazano, jak przeanalizować ciąg w celu utworzenia drzewa XML w języku C#.</span><span class="sxs-lookup"><span data-stu-id="d5638-105">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="d5638-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5638-106">Example</span></span>

<span data-ttu-id="d5638-107">Poniższy kod w języku C# pokazuje, jak analizować ciąg XML:</span><span class="sxs-lookup"><span data-stu-id="d5638-107">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="d5638-108">Węzeł główny `Contacts` ma dwa `Contact` węzły.</span><span class="sxs-lookup"><span data-stu-id="d5638-108">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="d5638-109">Aby uzyskać dostęp do określonych danych w analizowanym formacie XML, należy użyć metody [XElement. elementy ()](xref:System.Xml.Linq.XContainer.Elements) , która w tym przypadku zwraca elementy podrzędne `Contacts` węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="d5638-109">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="d5638-110">Poniższy przykład drukuje pierwszy `Contact` węzeł konsoli:</span><span class="sxs-lookup"><span data-stu-id="d5638-110">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="d5638-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5638-111">See also</span></span>

- [<span data-ttu-id="d5638-112">Jak znaleźć element z określonym atrybutem (C#)</span><span class="sxs-lookup"><span data-stu-id="d5638-112">How to find an element with a specific attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)
