---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394269"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Buforowanie: Usunięto Właściwość CompactOnMemoryPressure

W wersji ASP.NET Core 3,0 usunięto [przestarzałe interfejsy API MemoryCacheOptions](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).

#### <a name="change-description"></a>Zmień opis

Ta zmiana to kontynuacja dla elementu [ASPNET/buforowanie # 221](https://github.com/aspnet/Caching/issues/221). W przypadku dyskusji zobacz [ASPNET/Extensions # 1062](https://github.com/aspnet/Extensions/issues/1062).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Właściwość `MemoryCacheOptions.CompactOnMemoryPressure` była dostępna.

#### <a name="new-behavior"></a>Nowe zachowanie

Właściwość `MemoryCacheOptions.CompactOnMemoryPressure` została usunięta.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Automatyczne kompaktowanie pamięci podręcznej powodowało problemy. Aby uniknąć nieoczekiwanego zachowania, pamięć podręczna powinna być kompaktowana tylko wtedy, gdy jest to konieczne.

#### <a name="recommended-action"></a>Zalecana akcja

Aby skompaktować pamięć podręczną, downcast do `MemoryCache` i Wywołaj `Compact` w razie potrzeby.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
