---
title: Interoperacyjne odwołania do obiektów
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 0927f217a1666f8f27ca9c3e68f80a96b9c0f2b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184707"
---
# <a name="interoperable-object-references"></a>Interoperacyjne odwołania do obiektów
Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje obiekty według wartości. Można użyć <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> właściwości, aby poinstruować serializatora kontraktu danych, aby zachować odwołania do obiektów podczas serializacji obiektów.  
  
## <a name="generated-xml"></a>Wygenerowany kod XML  
 Na przykład należy wziąć pod uwagę następujący obiekt:  
  
```csharp  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass
{  
}  
```  
  
 Przy <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> ustawieniu `false` na (domyślnie) generowany jest następujący kod XML:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 Z <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> ustawioną na `true`, generowany jest następujący kod XML:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> Jednak nie opisuje `id` i `ref` atrybuty w jego schematu, nawet wtedy, gdy `preserveObjectReferences` właściwość jest ustawiona na `true`.  
  
## <a name="using-isreference"></a>Korzystanie z isreference  
 Aby wygenerować informacje o odwołaniu do obiektu, które <xref:System.Runtime.Serialization.DataContractAttribute> są prawidłowe zgodnie ze <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> schematem, który go opisuje, zastosuj atrybut do typu i ustaw flagę na `true`. Poniższy przykład modyfikuje klasę `X` w `IsReference`poprzednim przykładzie, dodając:  
  
```csharp
[DataContract(IsReference=true)]
public class X
{  
     SomeClass someInstance = new SomeClass();
     [DataMember]
     public SomeClass A = someInstance;
     [DataMember]
     public SomeClass B = someInstance;
}
  
public class SomeClass
{
}  
````

 Wygenerowany kod XML jest następujący:  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 Korzystanie `IsReference` zapewnia zgodność z komunikatami zaokrąglania. Bez niego, gdy typ jest generowany ze schematu, dane wyjściowe XML dla tego typu nie musi być zgodne ze schematem pierwotnie zakładane. Innymi słowy, mimo `id` `ref` że atrybuty i zostały serializowane, oryginalny schemat mógł zablokować te atrybuty (lub wszystkie atrybuty) z występujących w XML. Po `IsReference` zastosowaniu do elementu członkowskiego danych element członkowski nadal jest rozpoznawany jako *odnośny,* gdy zaokrąglone potknięte.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
