---
title: Kroki procesu serializacji
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: ef81ecc7ca177fa9360f53a6b66015412d282065
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084921"
---
# <a name="steps-in-the-serialization-process"></a>Kroki procesu serializacji
Gdy <xref:System.Runtime.Serialization.Formatter.Serialize*> wywoływana jest metoda [program formatujący](xref:System.Runtime.Serialization.Formatter), przechodzi serializacji obiektów według następującej reguły:

- Dokonuje określić, czy element formatujący selektora znaków. Jeśli element formatujący Sprawdź, czy selektor dwuskładnikowego obsługi obiektów określonego typu. Jeśli selektor obsługuje typ obiektu <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> jest wywoływana w selektorze znaków.

- Jeśli nie ma żadnych selektor znaków lub jeśli nie obsługuje typ obiektu, dokonuje do określenia, czy obiekt jest oznaczony za pomocą [Serializable](xref:System.SerializableAttribute) atrybutu. Jeśli obiekt nie jest <xref:System.Runtime.Serialization.SerializationException> zgłaszany.

- Jeśli obiekt jest oznaczony odpowiednio, sprawdź, czy obiekt implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu. Jeśli obiekt ma, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> jest wywoływana w obiekcie.
  
- Jeśli obiekt nie implementuje <xref:System.Runtime.Serialization.ISerializable>, jest używana domyślna zasada serializacji, serializacji wszystkie pola niezaznaczonych jako [NonSerialized](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Zobacz także

- [Serializacja binarna](binary-serialization.md)  
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
