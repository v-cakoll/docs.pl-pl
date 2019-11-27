---
title: Message. WriteStartHeaders — Metoda (System. ServiceModel. Channels)
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: a2c82ee4029c7af0396219f5ded8c999fd01d65b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451179"
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
