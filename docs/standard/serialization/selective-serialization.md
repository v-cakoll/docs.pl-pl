---
title: Serializacja selektywna
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: 74e21045ec70faf6ee82200a15362d51edf61433
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186005"
---
# <a name="selective-serialization"></a><span data-ttu-id="d6ea0-102">Serializacja selektywna</span><span class="sxs-lookup"><span data-stu-id="d6ea0-102">Selective serialization</span></span>
<span data-ttu-id="d6ea0-103">Klasa często zawiera pola, które nie powinny być serializowane.</span><span class="sxs-lookup"><span data-stu-id="d6ea0-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="d6ea0-104">Załóżmy na przykład, że klasa przechowuje identyfikator wątku w zmiennej składowej.</span><span class="sxs-lookup"><span data-stu-id="d6ea0-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="d6ea0-105">Gdy klasa jest przeprowadzona, wątek przechowywane identyfikator po klasie serializacja została wykonana już nie może być uruchomiony; Dzięki serializację tej wartości nie ma sensu.</span><span class="sxs-lookup"><span data-stu-id="d6ea0-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="d6ea0-106">Możesz uniemożliwić zmienne elementu członkowskiego serializowanego, oznaczając je [NonSerialized](xref:System.NonSerializedAttribute) atrybutu w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d6ea0-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="d6ea0-107">Jeśli to możliwe należy obiekt zawierający dane dotyczące zabezpieczeń nonserializable.</span><span class="sxs-lookup"><span data-stu-id="d6ea0-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="d6ea0-108">Jeśli obiekt musi być Zserializowany, zastosuj `NonSerialized` atrybutu w określonych polach przechowujących dane poufne.</span><span class="sxs-lookup"><span data-stu-id="d6ea0-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="d6ea0-109">Jeśli nie wyklucza te pola z serializacji, należy pamiętać, że dane, które są przechowywane są narażone na wszelki kod, który ma uprawnienia do wykonywania serializacji.</span><span class="sxs-lookup"><span data-stu-id="d6ea0-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="d6ea0-110">Aby uzyskać więcej informacji na temat pisania kodu serializacji bezpiecznego zobacz [zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="d6ea0-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="d6ea0-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6ea0-111">See also</span></span>

- [<span data-ttu-id="d6ea0-112">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="d6ea0-112">Binary Serialization</span></span>](binary-serialization.md)  
- [<span data-ttu-id="d6ea0-113">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="d6ea0-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
- [<span data-ttu-id="d6ea0-114">Zabezpieczenia i serializacja</span><span class="sxs-lookup"><span data-stu-id="d6ea0-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
