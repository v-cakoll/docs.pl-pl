---
title: Kroki procesu serializacji
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: b697e8c590d0865b26eaa9f66a333504a5faece2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517360"
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="cfc9d-102">Kroki procesu serializacji</span><span class="sxs-lookup"><span data-stu-id="cfc9d-102">Steps in the serialization process</span></span>
<span data-ttu-id="cfc9d-103">Gdy <xref:System.Runtime.Serialization.Formatter.Serialize*> wywoływana jest metoda [program formatujący](xref:System.Runtime.Serialization.Formatter), przechodzi serializacji obiektów według następującej reguły:</span><span class="sxs-lookup"><span data-stu-id="cfc9d-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize*> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="cfc9d-104">Dokonuje określić, czy element formatujący selektora znaków.</span><span class="sxs-lookup"><span data-stu-id="cfc9d-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="cfc9d-105">Jeśli element formatujący Sprawdź, czy selektor dwuskładnikowego obsługi obiektów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="cfc9d-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="cfc9d-106">Jeśli selektor obsługuje typ obiektu <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> jest wywoływana w selektorze znaków.</span><span class="sxs-lookup"><span data-stu-id="cfc9d-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="cfc9d-107">Jeśli nie ma żadnych selektor znaków lub jeśli nie obsługuje typ obiektu, dokonuje do określenia, czy obiekt jest oznaczony za pomocą [Serializable](xref:System.SerializableAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cfc9d-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="cfc9d-108">Jeśli obiekt nie jest <xref:System.Runtime.Serialization.SerializationException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="cfc9d-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="cfc9d-109">Jeśli obiekt jest oznaczony odpowiednio, sprawdź, czy obiekt implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cfc9d-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="cfc9d-110">Jeśli obiekt ma, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> jest wywoływana w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="cfc9d-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> is called on the object.</span></span>
  
- <span data-ttu-id="cfc9d-111">Jeśli obiekt nie implementuje <xref:System.Runtime.Serialization.ISerializable>, jest używana domyślna zasada serializacji, serializacji wszystkie pola niezaznaczonych jako [NonSerialized](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="cfc9d-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="cfc9d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfc9d-112">See also</span></span>

- [<span data-ttu-id="cfc9d-113">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="cfc9d-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="cfc9d-114">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="cfc9d-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
