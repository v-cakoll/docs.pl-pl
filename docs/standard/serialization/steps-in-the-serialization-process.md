---
title: Kroki procesu serializacji
description: Proces serializacji rozpoczyna się, gdy wywoływana jest metoda serializacji w programie formatującego. W tym artykule opisano sekwencję zdarzeń.
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: 1f749b9102182e78bc3fda436cf386a9f5759d5a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "83379097"
---
# <a name="steps-in-the-serialization-process"></a>Kroki procesu serializacji
Gdy <xref:System.Runtime.Serialization.Formatter.Serialize%2A> Metoda jest wywoływana w programie [formatującego](xref:System.Runtime.Serialization.Formatter), serializacja obiektu odbywa się zgodnie z następującą sekwencją reguł:

- Dokonuje określić, czy element formatujący selektora znaków. Jeśli element formatujący Sprawdź, czy selektor dwuskładnikowego obsługi obiektów określonego typu. Jeśli selektor obsługuje typ obiektu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> jest wywoływana w selektorze surogatu.

- Jeśli nie ma selektora zastępcy lub jeśli nie obsługuje typu obiektu, sprawdza się w celu ustalenia, czy obiekt jest oznaczony atrybutem [możliwym do serializacji](xref:System.SerializableAttribute) . Jeśli obiekt nie jest, <xref:System.Runtime.Serialization.SerializationException> jest zgłaszany.

- Jeśli obiekt jest odpowiednio oznaczony, sprawdź, czy obiekt implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs. Jeśli obiekt <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> jest wywoływana dla obiektu.
  
- Jeśli obiekt nie jest zaimplementowany <xref:System.Runtime.Serialization.ISerializable> , używane są domyślne zasady serializacji, czyli Serializowanie wszystkich pól, które nie są oznaczone jako [nieserializowane](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Zobacz także

- [Serializacja binarna](binary-serialization.md)
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
