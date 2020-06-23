---
title: UnsafeNclNativeMethods, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 46756a0d1d69b4768dbb8dcdd7ab098d3f1849bf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990358"
---
# <a name="unsafenclnativemethods-class"></a>UnsafeNclNativeMethods, klasa

Zawiera klasy służące do importowania niebezpiecznych metod sieci natywnych. Klasa ta nie może być dziedziczona.

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="nativepki-class"></a>Klasa NativePKI

Zawiera metody zaimportowane z crypt32.dll. Te metody obsługują certyfikaty przy użyciu protokołu Hypertext Transfer Protocol Secure (HTTPS). Klasa ta nie może być dziedziczona.

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a>NativePKI. FindClientCertificates — Metoda

Odnajduje dostępne certyfikaty klienta do wysłania do serwera.

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a>Wartość zwracana

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

Kolekcja dostępnych certyfikatów klienta.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)
