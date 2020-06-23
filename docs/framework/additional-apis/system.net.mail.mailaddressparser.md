---
title: MailAddressParser, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990385"
---
# <a name="mailaddressparser-class"></a>MailAddressParser, klasa

Analizuje adresy e-mail zgodnie z opisem w dokumencie RFC 2822. Klasa ta nie może być dziedziczona.

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="parseaddress-method"></a>ParseAddress, Metoda

Analizuje pojedynczy adres e-mail z określonego ciągu.

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a>Parametry

`data` <xref:System.String>

Ciąg, który zawiera adres e-mail, który ma zostać przeanalizowany.

### <a name="return-value"></a>Wartość zwracana

<xref:System.Net.Mail.MailAddress>

Prawidłowy adres e-mail.

### <a name="exceptions"></a>Wyjątki

<xref:System.FormatException?displayProperty=nameWithType>

Adres e-mail jest nieprawidłowy.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)
