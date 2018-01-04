---
title: "Odwołania do obiektów międzyoperacyjnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d74c54d29f7da085d9d87bf37cc93078726f308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="interoperable-object-references"></a><span data-ttu-id="50102-102">Odwołania do obiektów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="50102-102">Interoperable Object References</span></span>
<span data-ttu-id="50102-103">Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje obiekty według wartości.</span><span class="sxs-lookup"><span data-stu-id="50102-103">By default the <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="50102-104">Można użyć <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> właściwości nakazać serializator kontraktu danych, aby zachować odwołania do obiektu podczas serializacji obiektów tego typu.</span><span class="sxs-lookup"><span data-stu-id="50102-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the Data Contract Serializer to preserve object references when serializing objects of the type.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="50102-105">Wygenerowany XML</span><span class="sxs-lookup"><span data-stu-id="50102-105">Generated XML</span></span>  
 <span data-ttu-id="50102-106">Na przykład rozważmy następujący obiekt:</span><span class="sxs-lookup"><span data-stu-id="50102-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="50102-107">Z <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> ustawioną `false` (ustawienie domyślne), zostanie wygenerowany następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="50102-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="50102-108">Z <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> ustawioną `true`, generowany jest następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="50102-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 <span data-ttu-id="50102-109">Jednak <xref:System.Runtime.Serialization.XsdDataContractExporter> nie opisano `id` i `ref` atrybutów w jego schematu, nawet wtedy, gdy `preserveObjectReferences` właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="50102-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> does not describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="50102-110">Przy użyciu IsReference</span><span class="sxs-lookup"><span data-stu-id="50102-110">Using IsReference</span></span>  
 <span data-ttu-id="50102-111">Aby wygenerować informacje obiektu, która jest nieprawidłowa według schematu zawierającego jego opis, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do typu, a następnie ustaw <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flaga `true`.</span><span class="sxs-lookup"><span data-stu-id="50102-111">To generate object reference information that is valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="50102-112">Przy użyciu `IsReference` w klasie poprzedniego przykładu `X`:</span><span class="sxs-lookup"><span data-stu-id="50102-112">Using `IsReference` in the previous example class `X`:</span></span>  
  
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
  
 <span data-ttu-id="50102-113">Wygenerowany kod XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="50102-113">The generated XML is as follows:</span></span>  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 <span data-ttu-id="50102-114">Przy użyciu `IsReference` zapewnia zgodność na komunikat dwustronną komunikację.</span><span class="sxs-lookup"><span data-stu-id="50102-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="50102-115">Bez niego gdy typem jest generowany na podstawie schematu, wysyłanych jako plik XML dla typu nie jest zawsze zgodny z pierwotnie zakłada, że schemat.</span><span class="sxs-lookup"><span data-stu-id="50102-115">Without it, when a type is generated from schema, what is sent back as XML for that type is not necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="50102-116">Innymi słowy mimo że `id` i `ref` atrybuty przeprowadzono serializacji, oryginalnego schematu może mieć pozbawiona tych atrybutów (lub wszystkie atrybuty) występuje w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="50102-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="50102-117">Z `IsReference` zastosowano do elementu członkowskiego danych, element członkowski w dalszym ciągu rozpoznana jako "referenceable" when roundtripped.</span><span class="sxs-lookup"><span data-stu-id="50102-117">With `IsReference` applied to a data member, the member continues to be recognized as "referenceable" when roundtripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50102-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50102-118">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
