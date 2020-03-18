---
title: Usuwanie elementów, atrybutów i węzłów z drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591261"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>Usuwanie elementów, atrybutów i węzłów z drzewa XML (C#)

Można zmodyfikować drzewo XML, usuwając elementy, atrybuty i inne typy węzłów.

Usuwanie pojedynczego elementu lub pojedynczego atrybutu z dokumentu XML jest proste. Jednak podczas usuwania kolekcji elementów lub atrybutów, należy najpierw materializować kolekcji do listy, a następnie usunąć elementy lub atrybuty z listy. Najlepszym rozwiązaniem jest użycie <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozszerzenia, która zrobi to za Ciebie.

Głównym powodem tego jest to, że większość kolekcji, które można pobrać z drzewa XML są uzyskują przy użyciu odroczonego wykonania. Jeśli najpierw nie zmaterializujesz ich na liście lub jeśli nie użyjesz metod rozszerzenia, można napotkać pewną klasę błędów. Aby uzyskać więcej informacji, zobacz [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).

Następujące metody usuwają węzły i atrybuty z drzewa XML.

|Metoda|Opis|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Usuwa element <xref:System.Xml.Linq.XAttribute> nadrzędny.|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Usuwa węzły podrzędne <xref:System.Xml.Linq.XContainer>z pliku .|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Usuwa zawartość i atrybuty <xref:System.Xml.Linq.XElement>z pliku .|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Usuwa atrybuty pliku <xref:System.Xml.Linq.XElement>.|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Jeśli przekażesz `null` wartość, a następnie usuwa atrybut.|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Jeśli przejdziesz `null` dla wartości, a następnie usuwa element podrzędny.|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Usuwa element <xref:System.Xml.Linq.XNode> nadrzędny.|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Usuwa każdy atrybut lub element w kolekcji źródłowej z jego elementu nadrzędnego.|

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W tym przykładzie przedstawiono trzy podejścia do usuwania elementów. Po pierwsze usuwa pojedynczy element. Po drugie pobiera kolekcję elementów, materializuje je <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> za pomocą operatora i usuwa kolekcję. Na koniec pobiera kolekcję elementów i usuwa <xref:System.Xml.Linq.Extensions.Remove%2A> je za pomocą metody rozszerzenia.

Aby uzyskać więcej <xref:System.Linq.Enumerable.ToList%2A> informacji na temat operatora, zobacz [Konwertowanie typów danych (C#)](./converting-data-types.md).

### <a name="code"></a>Code

```csharp
XElement root = XElement.Parse(@"<Root>
    <Child1>
        <GrandChild1/>
        <GrandChild2/>
        <GrandChild3/>
    </Child1>
    <Child2>
        <GrandChild4/>
        <GrandChild5/>
        <GrandChild6/>
    </Child2>
    <Child3>
        <GrandChild7/>
        <GrandChild8/>
        <GrandChild9/>
    </Child3>
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

### <a name="comments"></a>Komentarze

Ten kod generuje następujące dane wyjściowe:

```xml
<Root>
  <Child1>
    <GrandChild2 />
    <GrandChild3 />
  </Child1>
  <Child2 />
  <Child3 />
</Root>
```

Należy zauważyć, że pierwszy element `Child1`wnuka został usunięty z . Wszystkie elementy wnuków zostały `Child2` usunięte `Child3`z i z .
