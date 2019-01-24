---
title: Wywołania zwrotne serializacji z tolerancją dla wersji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: fdd9108417068204b6d7ec2e4cc9ae54a160d7fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616351"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="cba81-102">Wywołania zwrotne serializacji z tolerancją dla wersji</span><span class="sxs-lookup"><span data-stu-id="cba81-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="cba81-103">Model programowania kontraktu danych w pełni obsługuje serializacji z tolerancją wersji metody wywołania zwrotnego, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> klasy pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="cba81-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="cba81-104">Atrybuty z tolerancją dla wersji</span><span class="sxs-lookup"><span data-stu-id="cba81-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="cba81-105">Istnieją cztery atrybuty wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="cba81-105">There are four callback attributes.</span></span> <span data-ttu-id="cba81-106">Każdy atrybut można stosować do metody wywołującej przez aparat serializacji/deserializacji w różnym czasie.</span><span class="sxs-lookup"><span data-stu-id="cba81-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="cba81-107">W poniższej tabeli opisano, kiedy należy używać każdego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cba81-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="cba81-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cba81-108">Attribute</span></span>|<span data-ttu-id="cba81-109">Gdy odpowiednia metoda jest wywoływana</span><span class="sxs-lookup"><span data-stu-id="cba81-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="cba81-110">Wywołuje się przed rozpoczęciem serializacji typu.</span><span class="sxs-lookup"><span data-stu-id="cba81-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="cba81-111">Wywoływane po serializacji typu.</span><span class="sxs-lookup"><span data-stu-id="cba81-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="cba81-112">Wywoływane przed deserializacji typie.</span><span class="sxs-lookup"><span data-stu-id="cba81-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="cba81-113">Wywoływane po deserializacji typie.</span><span class="sxs-lookup"><span data-stu-id="cba81-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="cba81-114">Metody muszą zaakceptować <xref:System.Runtime.Serialization.StreamingContext> parametru.</span><span class="sxs-lookup"><span data-stu-id="cba81-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="cba81-115">Te metody są głównie przeznaczone do użytku z wersji lub inicjowania.</span><span class="sxs-lookup"><span data-stu-id="cba81-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="cba81-116">Podczas deserializacji konstruktory nie są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="cba81-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="cba81-117">W związku z tym elementy członkowskie danych może nie być poprawnie zainicjować (do wartości domyślnych zamierzone) Jeśli dla tych członków brakuje danych w strumieniu przychodzące, na przykład, jeśli dane pochodzą z poprzedniej wersji typu, w którym brakuje niektórych elementów członkowskich danych.</span><span class="sxs-lookup"><span data-stu-id="cba81-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="cba81-118">Aby rozwiązać ten problem, należy użyć metody wywołania zwrotnego oznaczone <xref:System.Runtime.Serialization.OnDeserializingAttribute>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cba81-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="cba81-119">Można oznaczyć tylko jednej metody na typ z każdym z poprzednich atrybutów wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="cba81-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="cba81-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="cba81-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="cba81-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cba81-121">See also</span></span>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="cba81-122">Serializacja z tolerancją wersji</span><span class="sxs-lookup"><span data-stu-id="cba81-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)
