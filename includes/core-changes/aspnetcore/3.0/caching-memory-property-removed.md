---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901987"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Buforowanie: Usunięto Właściwość CompactOnMemoryPressure

W wersji ASP.NET Core 3,0 usunięto [przestarzałe interfejsy API MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).

#### <a name="change-description"></a>Zmień opis

Ta zmiana to kontynuacja dla elementu [ASPNET/buforowanie # 221](https://github.com/aspnet/Caching/issues/221). Aby zapoznać się z omówieniem, zobacz [dotnet/Extensions # 1062](https://github.com/dotnet/extensions/issues/1062).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`MemoryCacheOptions.CompactOnMemoryPressure`Właściwość była dostępna.

#### <a name="new-behavior"></a>Nowe zachowanie

`MemoryCacheOptions.CompactOnMemoryPressure` Właściwość została usunięta.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Automatyczne kompaktowanie pamięci podręcznej powodowało problemy. Aby uniknąć nieoczekiwanego zachowania, pamięć podręczna powinna być kompaktowana tylko wtedy, gdy jest to konieczne.

#### <a name="recommended-action"></a>Zalecana akcja

Aby skompaktować pamięć podręczną, `MemoryCache` downcast do `Compact` i Wywołaj w razie potrzeby.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
