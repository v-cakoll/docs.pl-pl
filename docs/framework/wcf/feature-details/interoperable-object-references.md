---
title: Odwołania do obiektów międzyoperacyjnych
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 5d2f7d93544cafab7cfe5d8dcbb8a4c5d5c5b576
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582428"
---
# <a name="interoperable-object-references"></a>Odwołania do obiektów międzyoperacyjnych
Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje obiektów według wartości. Możesz użyć <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> właściwości w celu poinstruowania serializator kontraktu danych, aby zachować odwołania do obiektu podczas serializowania obiektów tego typu.  
  
## <a name="generated-xml"></a>Wygenerowany kod XML  
 Na przykład należy wziąć pod uwagę następujący obiekt:  
  
```  
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
   <B ref="1" />  
</X>  
```  
  
 Jednak <xref:System.Runtime.Serialization.XsdDataContractExporter> nie opisano `id` i `ref` atrybutów w jego schematu, nawet wtedy, gdy `preserveObjectReferences` właściwość jest ustawiona na `true`.  
  
## <a name="using-isreference"></a>Za pomocą IsReference  
 Aby wygenerować informacje obiektu, który jest nieprawidłowa według schematu, który ją opisuje, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu, a następnie ustaw <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flaga `true`. Za pomocą `IsReference` w klasie poprzedniego przykładu `X`:  
  
 `[DataContract(IsReference=true)] public class X`  
  
 `{`  
  
 `SomeClass someInstance = new SomeClass();`  
  
 `[DataMember]`  
  
 `public SomeClass A = someInstance;`  
  
 `[DataMember]`  
  
 `public SomeClass B = someInstance;`  
  
 `}`  
  
 `public class SomeClass`  
  
 `{`  
  
 `}`  
  
 Wygenerowany kod XML jest następująca:  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 Za pomocą `IsReference` zapewnia zgodność na komunikat Pełna zgodnooć wersji. Bez niego gdy typem jest generowany na podstawie schematu, co jest wysyłane ponownie jako plik XML dla typ nie jest zawsze zgodny ze schematem pierwotnie zakłada, że. Innymi słowy mimo że `id` i `ref` atrybuty zostały zaszeregowane, oryginalnym schematem może mieć pozbawiona tych atrybutów (lub wszystkie atrybuty) występuje w kodzie XML. Za pomocą `IsReference` stosowany do składowej danych, należy w dalszym ciągu być uznane za "którego można się odwoływać" gdy roundtripped.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
