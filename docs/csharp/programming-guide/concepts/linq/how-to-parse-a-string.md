---
title: 'Instrukcje: analizowanie ciągu (C#)'
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 16310e37afec950c372c7b47637986bb0eb399b8
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956607"
---
# <a name="how-to-parse-a-string-c"></a>Instrukcje: analizowanie ciągu (C#)

W tym temacie pokazano, jak przeanalizować ciąg w celu utworzenia drzewa C#XML w.

## <a name="example"></a>Przykład

Poniższy C# kod ilustruje sposób analizowania ciągu XML:

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

Węzeł główny `Contacts` ma dwa węzły `Contact`. Aby uzyskać dostęp do określonych danych w analizowanym formacie XML, należy użyć metody [XElement. elementy ()](xref:System.Xml.Linq.XContainer.Elements) , która w tym przypadku zwraca elementy podrzędne węzła głównego `Contacts`. Poniższy przykład drukuje pierwszy węzeł `Contact` do konsoli:

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Znajdowanie elementu z określonym atrybutem (C#)](how-to-find-an-element-with-a-specific-attribute.md)
