---
title: Selektywne serializacji
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f583c0c7f2895b16ac0aea883dd98b4768179127
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="selective-serialization"></a>Selektywne serializacji
Klasa często zawiera pola, które nie powinny być serializowane. Załóżmy na przykład, że identyfikator wątku w klasie są przechowywane w zmiennej członkowskiej. Podczas deserializacji jest klasa, wątek przechowywane identyfikator kiedy została wykonana serializacja klasy nie może być uruchomiony; Dlatego serializacji tej wartości nie ma sensu. Zmienne Członkowskie uniemożliwi serializowana oznaczając je za pomocą [NonSerialized](xref:System.NonSerializedAttribute) atrybutu w następujący sposób.  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Jeśli to możliwe należy obiekt zawierający dane dotyczące zabezpieczeń nonserializable. Jeśli obiekt musi być serializowany, zastosuj `NonSerialized` atrybutu określonych pól, które przechowują dane poufne. Nie można wykluczyć te pola z serializacji, należy pamiętać, że dane, które przechowują są widoczne dla żadnego kodu, który ma uprawnienia do serializacji. Aby uzyskać więcej informacji na temat pisania kodu serializacji bezpieczny, zobacz [zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Zobacz także  
 [Serializacja binarna](binary-serialization.md)  
 [XML i serializacji SOAP](xml-and-soap-serialization.md)  
 [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)