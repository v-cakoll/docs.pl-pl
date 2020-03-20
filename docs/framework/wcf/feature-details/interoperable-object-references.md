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
# <a name="interoperable-object-references"></a><span data-ttu-id="9e261-102">Interoperacyjne odwołania do obiektów</span><span class="sxs-lookup"><span data-stu-id="9e261-102">Interoperable object references</span></span>
<span data-ttu-id="9e261-103">Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje obiekty według wartości.</span><span class="sxs-lookup"><span data-stu-id="9e261-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="9e261-104">Można użyć <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> właściwości, aby poinstruować serializatora kontraktu danych, aby zachować odwołania do obiektów podczas serializacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="9e261-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="9e261-105">Wygenerowany kod XML</span><span class="sxs-lookup"><span data-stu-id="9e261-105">Generated XML</span></span>  
 <span data-ttu-id="9e261-106">Na przykład należy wziąć pod uwagę następujący obiekt:</span><span class="sxs-lookup"><span data-stu-id="9e261-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="9e261-107">Przy <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> ustawieniu `false` na (domyślnie) generowany jest następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="9e261-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="9e261-108">Z <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> ustawioną na `true`, generowany jest następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="9e261-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="9e261-109"><xref:System.Runtime.Serialization.XsdDataContractExporter> Jednak nie opisuje `id` i `ref` atrybuty w jego schematu, nawet wtedy, gdy `preserveObjectReferences` właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="9e261-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="9e261-110">Korzystanie z isreference</span><span class="sxs-lookup"><span data-stu-id="9e261-110">Using IsReference</span></span>  
 <span data-ttu-id="9e261-111">Aby wygenerować informacje o odwołaniu do obiektu, które <xref:System.Runtime.Serialization.DataContractAttribute> są prawidłowe zgodnie ze <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> schematem, który go opisuje, zastosuj atrybut do typu i ustaw flagę na `true`.</span><span class="sxs-lookup"><span data-stu-id="9e261-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="9e261-112">Poniższy przykład modyfikuje klasę `X` w `IsReference`poprzednim przykładzie, dodając:</span><span class="sxs-lookup"><span data-stu-id="9e261-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
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

 <span data-ttu-id="9e261-113">Wygenerowany kod XML jest następujący:</span><span class="sxs-lookup"><span data-stu-id="9e261-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="9e261-114">Korzystanie `IsReference` zapewnia zgodność z komunikatami zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="9e261-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="9e261-115">Bez niego, gdy typ jest generowany ze schematu, dane wyjściowe XML dla tego typu nie musi być zgodne ze schematem pierwotnie zakładane.</span><span class="sxs-lookup"><span data-stu-id="9e261-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="9e261-116">Innymi słowy, mimo `id` `ref` że atrybuty i zostały serializowane, oryginalny schemat mógł zablokować te atrybuty (lub wszystkie atrybuty) z występujących w XML.</span><span class="sxs-lookup"><span data-stu-id="9e261-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="9e261-117">Po `IsReference` zastosowaniu do elementu członkowskiego danych element członkowski nadal jest rozpoznawany jako *odnośny,* gdy zaokrąglone potknięte.</span><span class="sxs-lookup"><span data-stu-id="9e261-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e261-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e261-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
