---
title: Kroki procesu serializacji
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2709af8e63428db2165ecd1256bce4f6690ae0a6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="3972a-102">Kroki procesu serializacji</span><span class="sxs-lookup"><span data-stu-id="3972a-102">Steps in the serialization process</span></span>
<span data-ttu-id="3972a-103">Gdy <xref:System.Runtime.Serialization.Formatter.Serialize*> wywoływana jest metoda [program formatujący](xref:System.Runtime.Serialization.Formatter), serializacji obiektu będzie kontynuowana zgodnie z następującej reguły:</span><span class="sxs-lookup"><span data-stu-id="3972a-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize*> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="3972a-104">Dokonuje określić, czy element formatujący selektora znaków.</span><span class="sxs-lookup"><span data-stu-id="3972a-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="3972a-105">Jeśli element formatujący Sprawdź, czy selektor dwuskładnikowego obsługi obiektów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="3972a-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="3972a-106">Jeśli selektor obsługuje typ obiektu <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> jest wywoływana w selektorze dwuskładnikowego.</span><span class="sxs-lookup"><span data-stu-id="3972a-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="3972a-107">Jeśli selektor nie surogat nie istnieje lub jeśli nie obsługuje typu obiektu, dokonuje ustalenie, czy obiekt jest oznaczony atrybutem [Serializable](xref:System.SerializableAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3972a-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="3972a-108">Jeśli obiekt nie jest <xref:System.Runtime.Serialization.SerializationException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="3972a-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="3972a-109">Jeśli obiekt jest odpowiednio oznaczone, sprawdź, czy obiekt implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3972a-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="3972a-110">Jeśli obiekt jest, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> jest wywoływana dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="3972a-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> is called on the object.</span></span>
  
- <span data-ttu-id="3972a-111">Jeśli obiekt nie implementuje <xref:System.Runtime.Serialization.ISerializable>, domyślne zasady serializacji jest używana, nie serializacji wszystkie pola oznaczone jako [NonSerialized](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="3972a-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="3972a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3972a-112">See Also</span></span>  
 [<span data-ttu-id="3972a-113">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="3972a-113">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="3972a-114">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="3972a-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)