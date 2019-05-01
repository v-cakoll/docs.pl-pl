---
title: Odwołania do obiektów międzyoperacyjnych
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: ada9084f6ac3c97dc641571c0cb8379a2fac68a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918973"
---
# <a name="interoperable-object-references"></a>Odwołania do obiektów międzyoperacyjnych
Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje obiektów według wartości. Możesz użyć <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> właściwości w celu poinstruowania serializator kontraktu danych, aby zachować odwołania do obiektu podczas serializacji obiektów.  
  
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
  
 Za pomocą <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> równa `false` (ustawienie domyślne), następujący kod XML jest generowany:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 Za pomocą <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> równa `true`, generowany jest następujący kod XML:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 Jednak <xref:System.Runtime.Serialization.XsdDataContractExporter> nie zawiera opisu `id` i `ref` atrybutów w jego schematu, nawet wtedy, gdy `preserveObjectReferences` właściwość jest ustawiona na `true`.  
  
## <a name="using-isreference"></a>Za pomocą IsReference  
 Aby wygenerować informacje obiektu, który jest nieprawidłowa według schematu, który ją opisuje, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu, a następnie ustaw <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flaga `true`. Poniższy przykład modyfikuje klasy `X` w poprzednim przykładzie, dodając `IsReference`:  
  
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

 Wygenerowany kod XML jest następująca:  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A> 
    <B ref="1"></B>  
</X>
```  
  
 Za pomocą `IsReference` zapewnia zgodność na komunikat Pełna zgodnooć wersji. Bez niego gdy typ jest generowany na podstawie schematu XML danych wyjściowych czy typ nie jest zawsze zgodny ze schematem pierwotnie zakłada, że. Innymi słowy mimo że `id` i `ref` atrybuty zostały zaszeregowane, oryginalnym schematem może mieć pozbawiona tych atrybutów (lub wszystkie atrybuty) występuje w kodzie XML. Za pomocą `IsReference` stosowany do składowej danych, należy w dalszym ciągu być uznane za *którego można się odwoływać* podczas-zwrotnego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
