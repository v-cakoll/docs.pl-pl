---
title: Odwołania do obiektów międzyoperacyjnych
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 9cbbd5a34269a7c4a5c33d72487a02df21f2f0fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222708"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="c82ba-102">Odwołania do obiektów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="c82ba-102">Interoperable Object References</span></span>
<span data-ttu-id="c82ba-103">Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje obiektów według wartości.</span><span class="sxs-lookup"><span data-stu-id="c82ba-103">By default the <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="c82ba-104">Możesz użyć <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> właściwości w celu poinstruowania serializator kontraktu danych, aby zachować odwołania do obiektu podczas serializowania obiektów tego typu.</span><span class="sxs-lookup"><span data-stu-id="c82ba-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the Data Contract Serializer to preserve object references when serializing objects of the type.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="c82ba-105">Wygenerowany kod XML</span><span class="sxs-lookup"><span data-stu-id="c82ba-105">Generated XML</span></span>  
 <span data-ttu-id="c82ba-106">Na przykład należy wziąć pod uwagę następujący obiekt:</span><span class="sxs-lookup"><span data-stu-id="c82ba-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="c82ba-107">Za pomocą <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> równa `false` (ustawienie domyślne), następujący kod XML jest generowany:</span><span class="sxs-lookup"><span data-stu-id="c82ba-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="c82ba-108">Za pomocą <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> równa `true`, generowany jest następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="c82ba-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 <span data-ttu-id="c82ba-109">Jednak <xref:System.Runtime.Serialization.XsdDataContractExporter> nie opisano `id` i `ref` atrybutów w jego schematu, nawet wtedy, gdy `preserveObjectReferences` właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="c82ba-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> does not describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="c82ba-110">Za pomocą IsReference</span><span class="sxs-lookup"><span data-stu-id="c82ba-110">Using IsReference</span></span>  
 <span data-ttu-id="c82ba-111">Aby wygenerować informacje obiektu, który jest nieprawidłowa według schematu, który ją opisuje, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu, a następnie ustaw <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flaga `true`.</span><span class="sxs-lookup"><span data-stu-id="c82ba-111">To generate object reference information that is valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="c82ba-112">Za pomocą `IsReference` w klasie poprzedniego przykładu `X`:</span><span class="sxs-lookup"><span data-stu-id="c82ba-112">Using `IsReference` in the previous example class `X`:</span></span>  
  
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
  
 <span data-ttu-id="c82ba-113">Wygenerowany kod XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="c82ba-113">The generated XML is as follows:</span></span>  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 <span data-ttu-id="c82ba-114">Za pomocą `IsReference` zapewnia zgodność na komunikat Pełna zgodnooć wersji.</span><span class="sxs-lookup"><span data-stu-id="c82ba-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="c82ba-115">Bez niego gdy typem jest generowany na podstawie schematu, co jest wysyłane ponownie jako plik XML dla typ nie jest zawsze zgodny ze schematem pierwotnie zakłada, że.</span><span class="sxs-lookup"><span data-stu-id="c82ba-115">Without it, when a type is generated from schema, what is sent back as XML for that type is not necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="c82ba-116">Innymi słowy mimo że `id` i `ref` atrybuty zostały zaszeregowane, oryginalnym schematem może mieć pozbawiona tych atrybutów (lub wszystkie atrybuty) występuje w kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="c82ba-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="c82ba-117">Za pomocą `IsReference` stosowany do składowej danych, należy w dalszym ciągu być uznane za "którego można się odwoływać" gdy roundtripped.</span><span class="sxs-lookup"><span data-stu-id="c82ba-117">With `IsReference` applied to a data member, the member continues to be recognized as "referenceable" when roundtripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c82ba-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c82ba-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
