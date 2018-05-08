---
title: Odwołania do obiektów międzyoperacyjnych
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: eeedd39ec14a6758395aee1f4c3b8ab26a0c2ffd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interoperable-object-references"></a>Odwołania do obiektów międzyoperacyjnych
Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje obiekty według wartości. Można użyć <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> właściwości nakazać serializator kontraktu danych, aby zachować odwołania do obiektu podczas serializacji obiektów tego typu.  
  
## <a name="generated-xml"></a>Wygenerowany XML  
 Na przykład rozważmy następujący obiekt:  
  
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
  
 Z <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> ustawioną `false` (ustawienie domyślne), zostanie wygenerowany następujący kod XML:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 Z <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> ustawioną `true`, generowany jest następujący kod XML:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 Jednak <xref:System.Runtime.Serialization.XsdDataContractExporter> nie opisano `id` i `ref` atrybutów w jego schematu, nawet wtedy, gdy `preserveObjectReferences` właściwość jest ustawiona na `true`.  
  
## <a name="using-isreference"></a>Przy użyciu IsReference  
 Aby wygenerować informacje obiektu, która jest nieprawidłowa według schematu zawierającego jego opis, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do typu, a następnie ustaw <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flaga `true`. Przy użyciu `IsReference` w klasie poprzedniego przykładu `X`:  
  
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
  
 Przy użyciu `IsReference` zapewnia zgodność na komunikat dwustronną komunikację. Bez niego gdy typem jest generowany na podstawie schematu, wysyłanych jako plik XML dla typu nie jest zawsze zgodny z pierwotnie zakłada, że schemat. Innymi słowy mimo że `id` i `ref` atrybuty przeprowadzono serializacji, oryginalnego schematu może mieć pozbawiona tych atrybutów (lub wszystkie atrybuty) występuje w pliku XML. Z `IsReference` zastosowano do elementu członkowskiego danych, element członkowski w dalszym ciągu rozpoznana jako "referenceable" when roundtripped.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
