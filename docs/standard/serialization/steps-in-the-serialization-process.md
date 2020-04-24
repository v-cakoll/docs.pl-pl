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
# <a name="steps-in-the-serialization-process"></a>Kroki procesu serializacji
Gdy <xref:System.Runtime.Serialization.Formatter.Serialize%2A> Metoda jest wywoływana w programie [formatującego](xref:System.Runtime.Serialization.Formatter), serializacja obiektu odbywa się zgodnie z następującą sekwencją reguł:

- Dokonuje określić, czy element formatujący selektora znaków. Jeśli element formatujący Sprawdź, czy selektor dwuskładnikowego obsługi obiektów określonego typu. Jeśli selektor obsługuje typ obiektu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> jest wywoływana w selektorze surogatu.

- Jeśli nie ma selektora zastępcy lub jeśli nie obsługuje typu obiektu, sprawdza się w celu ustalenia, czy obiekt jest oznaczony atrybutem [możliwym do serializacji](xref:System.SerializableAttribute) . Jeśli obiekt nie jest, <xref:System.Runtime.Serialization.SerializationException> jest zgłaszany.

- Jeśli obiekt jest odpowiednio oznaczony, sprawdź, czy obiekt implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs. Jeśli obiekt <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> jest wywoływana dla obiektu.
  
- Jeśli obiekt nie jest zaimplementowany <xref:System.Runtime.Serialization.ISerializable>, używane są domyślne zasady serializacji, czyli Serializowanie wszystkich pól, które nie są oznaczone jako [nieserializowane](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Zobacz też

- [Serializacja binarna](binary-serialization.md)
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
