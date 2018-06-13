---
title: Selektywne serializacji
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: 6a91501c4c3763250a64c9849694bc4e5fa4829f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581540"
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
 [Serializacja XML i SOAP](xml-and-soap-serialization.md)  
 [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)