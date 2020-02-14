---
title: Message. WriteStartHeaders — Metoda (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214862"
---
# <a name="messagewritestartheaders-method"></a>Message. WriteStartHeaders — Metoda

Zapisuje nagłówek startowy w pliku XML przez wywołanie metody <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType>.

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a>Parametry

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  Składnik zapisywania, który jest używany do zapisywania nagłówka startowego w pliku XML.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `Message.WriteStartHeaders` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.ServiceModel.Channels>

**Zestaw:** System. ServiceModel. dll

**.NET Framework wersje:** Dostępne od 3,0.
