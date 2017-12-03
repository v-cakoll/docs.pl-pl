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
# <a name="steps-in-the-serialization-process"></a>Kroki procesu serializacji
Gdy <xref:System.Runtime.Serialization.Formatter.Serialize*> wywoływana jest metoda [program formatujący](xref:System.Runtime.Serialization.Formatter), serializacji obiektu będzie kontynuowana zgodnie z następującej reguły:

- Dokonuje określić, czy element formatujący selektora znaków. Jeśli element formatujący Sprawdź, czy selektor dwuskładnikowego obsługi obiektów określonego typu. Jeśli selektor obsługuje typ obiektu <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> jest wywoływana w selektorze dwuskładnikowego.

- Jeśli selektor nie surogat nie istnieje lub jeśli nie obsługuje typu obiektu, dokonuje ustalenie, czy obiekt jest oznaczony atrybutem [Serializable](xref:System.SerializableAttribute) atrybutu. Jeśli obiekt nie jest <xref:System.Runtime.Serialization.SerializationException> jest generowany.

- Jeśli obiekt jest odpowiednio oznaczone, sprawdź, czy obiekt implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu. Jeśli obiekt jest, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> jest wywoływana dla obiektu.
  
- Jeśli obiekt nie implementuje <xref:System.Runtime.Serialization.ISerializable>, domyślne zasady serializacji jest używana, nie serializacji wszystkie pola oznaczone jako [NonSerialized](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja binarna](binary-serialization.md)  
 [XML i serializacji SOAP](xml-and-soap-serialization.md)