---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620277"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Karty strumienia WinRT nie są długie wywołania FlushAsync automatycznie przy zamykaniu

#### <a name="details"></a>Szczegóły

W aplikacjach ze sklepu Windows środowisko wykonawcze systemu Windows karty usługi Stream nie wywołują już metody FlushAsync z metody Dispose.

#### <a name="suggestion"></a>Sugestia

Ta zmiana powinna być niewidoczna. Deweloperzy mogą przywrócić poprzednie zachowanie, pisząc kod podobny do tego:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Przezroczyste|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
