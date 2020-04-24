---
title: Serializacja selektywna
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: cc5d7964d5f3268f08721593fefc07e3eff853ca
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159601"
---
# <a name="selective-serialization"></a>Serializacja selektywna
Klasa często zawiera pola, które nie powinny być serializowane. Załóżmy na przykład, że klasa przechowuje identyfikator wątku w zmiennej składowej. Podczas deserializacji klasy wątek przechowuje identyfikator, dla którego Serializacja klasy może nie być już uruchomiona; Dlatego Serializacja tej wartości nie ma sensu. Można zapobiec serializacji zmiennych składowych poprzez oznaczenie ich przy użyciu atrybutu [Nieserializowanego](xref:System.NonSerializedAttribute) w następujący sposób.  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Jeśli to możliwe należy obiekt zawierający dane dotyczące zabezpieczeń nonserializable. Jeśli obiekt musi być serializowany, Zastosuj `NonSerialized` atrybut do określonych pól, w których są przechowywane poufne dane. Jeśli nie wykluczasz tych pól z serializacji, pamiętaj, że dane, które są przechowywane, są uwidocznione w dowolnym kodzie, który ma uprawnienia do serializacji. Aby uzyskać więcej informacji na temat pisania kodu serializacji bezpiecznego, zobacz [zabezpieczenia i Serializacja](../../../docs/framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Zobacz też

- [Serializacja binarna](binary-serialization.md)
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)
