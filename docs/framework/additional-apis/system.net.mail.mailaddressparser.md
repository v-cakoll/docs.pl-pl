---
title: MailAddressParser, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ff83f6946539fa262ccde980052627f98c75601d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051353"
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
