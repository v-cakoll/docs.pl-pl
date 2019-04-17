---
title: Odwołania do obiektów międzyoperacyjnych
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: ada9084f6ac3c97dc641571c0cb8379a2fac68a8
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610642"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="66b3b-102">Odwołania do obiektów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="66b3b-102">Interoperable object references</span></span>
<span data-ttu-id="66b3b-103">Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje obiektów według wartości.</span><span class="sxs-lookup"><span data-stu-id="66b3b-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="66b3b-104">Możesz użyć <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> właściwości w celu poinstruowania serializator kontraktu danych, aby zachować odwołania do obiektu podczas serializacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="66b3b-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="66b3b-105">Wygenerowany kod XML</span><span class="sxs-lookup"><span data-stu-id="66b3b-105">Generated XML</span></span>  
 <span data-ttu-id="66b3b-106">Na przykład należy wziąć pod uwagę następujący obiekt:</span><span class="sxs-lookup"><span data-stu-id="66b3b-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="66b3b-107">Za pomocą <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> równa `false` (ustawienie domyślne), następujący kod XML jest generowany:</span><span class="sxs-lookup"><span data-stu-id="66b3b-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="66b3b-108">Za pomocą <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> równa `true`, generowany jest następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="66b3b-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="66b3b-109">Jednak <xref:System.Runtime.Serialization.XsdDataContractExporter> nie zawiera opisu `id` i `ref` atrybutów w jego schematu, nawet wtedy, gdy `preserveObjectReferences` właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="66b3b-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="66b3b-110">Za pomocą IsReference</span><span class="sxs-lookup"><span data-stu-id="66b3b-110">Using IsReference</span></span>  
 <span data-ttu-id="66b3b-111">Aby wygenerować informacje obiektu, który jest nieprawidłowa według schematu, który ją opisuje, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu, a następnie ustaw <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flaga `true`.</span><span class="sxs-lookup"><span data-stu-id="66b3b-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="66b3b-112">Poniższy przykład modyfikuje klasy `X` w poprzednim przykładzie, dodając `IsReference`:</span><span class="sxs-lookup"><span data-stu-id="66b3b-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
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

 <span data-ttu-id="66b3b-113">Wygenerowany kod XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="66b3b-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A> 
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="66b3b-114">Za pomocą `IsReference` zapewnia zgodność na komunikat Pełna zgodnooć wersji.</span><span class="sxs-lookup"><span data-stu-id="66b3b-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="66b3b-115">Bez niego gdy typ jest generowany na podstawie schematu XML danych wyjściowych czy typ nie jest zawsze zgodny ze schematem pierwotnie zakłada, że.</span><span class="sxs-lookup"><span data-stu-id="66b3b-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="66b3b-116">Innymi słowy mimo że `id` i `ref` atrybuty zostały zaszeregowane, oryginalnym schematem może mieć pozbawiona tych atrybutów (lub wszystkie atrybuty) występuje w kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="66b3b-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="66b3b-117">Za pomocą `IsReference` stosowany do składowej danych, należy w dalszym ciągu być uznane za *którego można się odwoływać* podczas-zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="66b3b-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b3b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66b3b-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
