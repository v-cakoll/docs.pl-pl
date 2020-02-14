---
title: Message. BodyToString — Metoda (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215504"
---
# <a name="messagebodytostring-method"></a>Message. BodyToString — Metoda

Konwertuje treść komunikatu na ciąg, wywołując metodę <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType>.

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>Parametry

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  Składnik zapisywania służący do konwertowania treści komunikatu na ciąg.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `Message.BodyToString` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.ServiceModel.Channels>

**Zestaw:** System. ServiceModel. dll

**.NET Framework wersje:** Dostępne od 3,0.
