---
title: Serializacja selektywna
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: af608031a661037b89c9783ac2451a6b536f9cd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731390"
---
# <a name="selective-serialization"></a>Serializacja selektywna
Klasa często zawiera pola, które nie powinny być serializowane. Załóżmy na przykład, że klasa przechowuje identyfikator wątku w zmiennej składowej. Gdy klasa jest przeprowadzona, wątek przechowywane identyfikator po klasie serializacja została wykonana już nie może być uruchomiony; Dzięki serializację tej wartości nie ma sensu. Możesz uniemożliwić zmienne elementu członkowskiego serializowanego, oznaczając je [NonSerialized](xref:System.NonSerializedAttribute) atrybutu w następujący sposób.  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Jeśli to możliwe należy obiekt zawierający dane dotyczące zabezpieczeń nonserializable. Jeśli obiekt musi być Zserializowany, zastosuj `NonSerialized` atrybutu w określonych polach przechowujących dane poufne. Jeśli nie wyklucza te pola z serializacji, należy pamiętać, że dane, które są przechowywane są narażone na wszelki kod, który ma uprawnienia do wykonywania serializacji. Aby uzyskać więcej informacji na temat pisania kodu serializacji bezpiecznego zobacz [zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Zobacz także

- [Serializacja binarna](binary-serialization.md)
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)
