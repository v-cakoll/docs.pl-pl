---
title: Serializacja selektywna
description: W tym artykule pokazano, jak oznaczyć pola przy użyciu nieserializowanego atrybutu, który uniemożliwia Serializowanie tego pola.
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: c7203c4ea13c65f8d88c55de96988d3b1d9e9611
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379161"
---
# <a name="selective-serialization"></a><span data-ttu-id="9ba1b-103">Serializacja selektywna</span><span class="sxs-lookup"><span data-stu-id="9ba1b-103">Selective serialization</span></span>
<span data-ttu-id="9ba1b-104">Klasa często zawiera pola, które nie powinny być serializowane.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-104">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="9ba1b-105">Załóżmy na przykład, że klasa przechowuje identyfikator wątku w zmiennej składowej.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-105">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="9ba1b-106">Podczas deserializacji klasy wątek przechowuje identyfikator, dla którego Serializacja klasy może nie być już uruchomiona; Dlatego Serializacja tej wartości nie ma sensu.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-106">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="9ba1b-107">Można zapobiec serializacji zmiennych składowych poprzez oznaczenie ich przy użyciu atrybutu [Nieserializowanego](xref:System.NonSerializedAttribute) w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-107">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="9ba1b-108">Jeśli to możliwe należy obiekt zawierający dane dotyczące zabezpieczeń nonserializable.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-108">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="9ba1b-109">Jeśli obiekt musi być serializowany, Zastosuj `NonSerialized` atrybut do określonych pól, w których są przechowywane poufne dane.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-109">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="9ba1b-110">Jeśli nie wykluczasz tych pól z serializacji, pamiętaj, że dane, które są przechowywane, są uwidocznione w dowolnym kodzie, który ma uprawnienia do serializacji.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-110">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="9ba1b-111">Aby uzyskać więcej informacji na temat pisania kodu serializacji bezpiecznego, zobacz [zabezpieczenia i Serializacja](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="9ba1b-111">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="9ba1b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ba1b-112">See also</span></span>

- [<span data-ttu-id="9ba1b-113">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="9ba1b-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="9ba1b-114">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="9ba1b-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="9ba1b-115">Zabezpieczenia i serializacja</span><span class="sxs-lookup"><span data-stu-id="9ba1b-115">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
