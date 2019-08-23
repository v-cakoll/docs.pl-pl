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
ms.openlocfilehash: 0736f94b1fe1a91b20ee76da673e0bc139aa802a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959554"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="c7186-102">Wywołania zwrotne serializacji z tolerancją dla wersji</span><span class="sxs-lookup"><span data-stu-id="c7186-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="c7186-103">Model programowania kontraktu danych w pełni obsługuje metody wywołania zwrotnego serializacji odporne na <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> wersje <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> , które obsługują klasy i.</span><span class="sxs-lookup"><span data-stu-id="c7186-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="c7186-104">Atrybuty odporne na wersje</span><span class="sxs-lookup"><span data-stu-id="c7186-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="c7186-105">Istnieją cztery atrybuty wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c7186-105">There are four callback attributes.</span></span> <span data-ttu-id="c7186-106">Każdy atrybut może być stosowany do metody, którą aparat serializacji/deserializacji wywołuje w różnym czasie.</span><span class="sxs-lookup"><span data-stu-id="c7186-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="c7186-107">W poniższej tabeli objaśniono, kiedy używać każdego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c7186-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="c7186-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c7186-108">Attribute</span></span>|<span data-ttu-id="c7186-109">Po wywołaniu odpowiedniej metody</span><span class="sxs-lookup"><span data-stu-id="c7186-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="c7186-110">Wywołuje się przed serializowaniem typu.</span><span class="sxs-lookup"><span data-stu-id="c7186-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="c7186-111">Wywołuje się po serializacji typu.</span><span class="sxs-lookup"><span data-stu-id="c7186-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="c7186-112">Wywołuje się przed deserializacji typu.</span><span class="sxs-lookup"><span data-stu-id="c7186-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="c7186-113">Wywołuje się po deserializacji typu.</span><span class="sxs-lookup"><span data-stu-id="c7186-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="c7186-114">Metody muszą akceptować <xref:System.Runtime.Serialization.StreamingContext> parametr.</span><span class="sxs-lookup"><span data-stu-id="c7186-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="c7186-115">Te metody są przeznaczone głównie do użytku z wersjami lub inicjalizacją.</span><span class="sxs-lookup"><span data-stu-id="c7186-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="c7186-116">Podczas deserializacji nie są wywoływane konstruktory.</span><span class="sxs-lookup"><span data-stu-id="c7186-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="c7186-117">W związku z tym elementy członkowskie danych mogą nie być prawidłowo zainicjowane (do zamierzonych wartości domyślnych), jeśli w strumieniu przychodzącym brakuje danych dla tych elementów członkowskich, na przykład jeśli dane pochodzą z poprzedniej wersji typu, w którym brakuje niektórych elementów członkowskich danych.</span><span class="sxs-lookup"><span data-stu-id="c7186-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="c7186-118">Aby rozwiązać ten wynik, użyj metody wywołania zwrotnego oznaczonej przy użyciu <xref:System.Runtime.Serialization.OnDeserializingAttribute>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c7186-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="c7186-119">Można oznaczyć tylko jedną metodę na typ z każdym z powyższych atrybutów wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c7186-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c7186-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7186-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="c7186-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7186-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="c7186-122">Serializacja z tolerancją wersji</span><span class="sxs-lookup"><span data-stu-id="c7186-122">Version Tolerant Serialization</span></span>](../../../standard/serialization/version-tolerant-serialization.md)
