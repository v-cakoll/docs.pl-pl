---
title: Usuwanie elementów, atrybutów i węzłów z drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: f3091c3f46d8b3283c961fffd4d1f0ce991083ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711983"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>Usuwanie elementów, atrybutów i węzłów z drzewa XML (C#)
Możesz zmodyfikować drzewa XML, usunięcie elementów, atrybutów i innych typów węzłów.  
  
 Usuwanie dokumentu XML pojedynczy element lub jeden atrybut jest bardzo proste. Jednak podczas usuwania kolekcji elementów lub atrybutów, należy najpierw zmaterializowania kolekcji do listy, a następnie usuń z listy elementów lub atrybutów. Najlepszym rozwiązaniem jest użycie <xref:System.Xml.Linq.Extensions.Remove%2A> metodę rozszerzenia, które wykona to dla Ciebie.  
  
 Głównym powodem w ten sposób jest uzyskane większość kolekcje, które możesz pobrać z drzewa XML za pomocą odroczonego wykonania. Jeśli użytkownik nie najpierw zmaterializowania je do listy lub jeśli nie używasz metody rozszerzenia, jest możliwość napotkania klasę usterek. Aby uzyskać więcej informacji, zobacz [mieszane deklaratywne usterki kodu kodu/Imperatywne (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Następujące metody usuń węzły i atrybuty z drzewa XML.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Usuwa <xref:System.Xml.Linq.XAttribute> od jego elementu nadrzędnego.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Usuwa węzły podrzędne z <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Usuwa zawartość i atrybutów z <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Usuwa atrybuty <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|W przypadku przekazania `null` wartości, a następnie usuwa atrybut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|W przypadku przekazania `null` wartości, a następnie usuwa element podrzędny.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Usuwa <xref:System.Xml.Linq.XNode> od jego elementu nadrzędnego.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Usuwa każdego atrybutu lub elementu w kolekcji źródłowej, z jego elementu nadrzędnego.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W tym przykładzie przedstawiono trzy sposoby usuwania elementów. Po pierwsze Usuwa pojedynczy element. Po drugie, pobiera kolekcję elementów, materializuje je przy użyciu <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operatora i usuwa kolekcji. Na koniec pobiera kolekcję elementów i usuwa je przy użyciu <xref:System.Xml.Linq.Extensions.Remove%2A> — metoda rozszerzenia.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Linq.Enumerable.ToList%2A> operatora, zobacz [konwertowanie typów danych (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).  
  
### <a name="code"></a>Kod  
  
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
  
 Należy zauważyć, że pierwszy element podwójnym została usunięta z `Child1`. Wszystkie elementy podrzędne zostały usunięte z `Child2` i `Child3`.  
  
## <a name="see-also"></a>Zobacz także

- [Modyfikowanie drzew XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
