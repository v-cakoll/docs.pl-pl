---
title: Kroki procesu serializacji
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: f30dd550437e6bc1030c79865bf2edd2c0efbfa9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741050"
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="54c8c-102">Kroki procesu serializacji</span><span class="sxs-lookup"><span data-stu-id="54c8c-102">Steps in the serialization process</span></span>
<span data-ttu-id="54c8c-103">Gdy <xref:System.Runtime.Serialization.Formatter.Serialize%2A> Metoda jest wywoływana w programie [formatującego](xref:System.Runtime.Serialization.Formatter), serializacja obiektu odbywa się zgodnie z następującą sekwencją reguł:</span><span class="sxs-lookup"><span data-stu-id="54c8c-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="54c8c-104">Dokonuje określić, czy element formatujący selektora znaków.</span><span class="sxs-lookup"><span data-stu-id="54c8c-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="54c8c-105">Jeśli element formatujący Sprawdź, czy selektor dwuskładnikowego obsługi obiektów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="54c8c-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="54c8c-106">Jeśli selektor obsługuje typ obiektu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> jest wywoływana w selektorze surogatu.</span><span class="sxs-lookup"><span data-stu-id="54c8c-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="54c8c-107">Jeśli nie ma selektora zastępcy lub jeśli nie obsługuje typu obiektu, sprawdza się w celu ustalenia, czy obiekt jest oznaczony atrybutem [możliwym do serializacji](xref:System.SerializableAttribute) .</span><span class="sxs-lookup"><span data-stu-id="54c8c-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="54c8c-108">Jeśli obiekt nie jest, <xref:System.Runtime.Serialization.SerializationException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="54c8c-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="54c8c-109">Jeśli obiekt jest odpowiednio oznaczony, sprawdź, czy obiekt implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs.</span><span class="sxs-lookup"><span data-stu-id="54c8c-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="54c8c-110">Jeśli obiekt <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> jest wywoływana dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="54c8c-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> is called on the object.</span></span>
  
- <span data-ttu-id="54c8c-111">Jeśli obiekt nie jest zaimplementowany <xref:System.Runtime.Serialization.ISerializable>, używane są domyślne zasady serializacji, czyli Serializowanie wszystkich pól, które nie są oznaczone jako [nieserializowane](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="54c8c-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="54c8c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54c8c-112">See also</span></span>

- [<span data-ttu-id="54c8c-113">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="54c8c-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="54c8c-114">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="54c8c-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
