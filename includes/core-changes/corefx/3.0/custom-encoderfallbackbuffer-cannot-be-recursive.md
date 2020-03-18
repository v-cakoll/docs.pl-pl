---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568157"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Niestandardowe wystąpienia Buforu ConerFallbackBuffer nie mogą wycofać się cyklicznie

Wystąpienia <xref:System.Text.EncoderFallbackBuffer> niestandardowe nie mogą wycofać się cyklicznie. Implementacja <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi spowodować sekwencję znaków, która jest konwertowalna do kodowania docelowego. W przeciwnym razie wystąpi wyjątek.

#### <a name="change-description"></a>Zmień opis

Podczas operacji transkodowania między znakami do bajtów program runtime wykrywa źle sformułowane lub niekonwertowalne sekwencje UTF-16 i udostępnia te znaki <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> do metody. Metoda `Fallback` określa, które znaki powinny być zastępowane oryginalnymi danymi niewymienialnymi, <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> a te znaki są opróżniane przez wywoływanie w pętli.

Następnie czas wykonywania próbuje przekodować te znaki podstawienia do kodowania docelowego. Jeśli ta operacja zakończy się pomyślnie, czas wykonywania kontynuuje transkodowanie od miejsca, w którym zostało wyłączone w oryginalnym ciągu wejściowym.

W .NET Core Preview 7 i wcześniejszych <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> wersjach implementacje niestandardowe mogą zwracać sekwencje znaków, które nie są konwertowalne do kodowania docelowego. Jeśli podstawione znaki nie mogą być transkodowane do kodowania <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> docelowego, czas wykonywania wywołuje metodę ponownie ze <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> znakami podstawienia, oczekując, że metoda zwróci nową sekwencję podstawienia. Ten proces jest kontynuowany, dopóki czas wykonywania ostatecznie widzi dobrze sformułowane, kabriolet podstawienia lub do momentu osiągnięcia maksymalnej liczby rekursji.

Począwszy od .NET Core 3.0, implementacje niestandardowe <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi zwracać sekwencje znaków, które są konwertowalne do kodowania docelowego. Jeśli podstawione znaki nie mogą być transkodowane <xref:System.ArgumentException> do kodowania docelowego, zgłaszany jest obiekt. Czas wykonywania nie będzie już wykonywać wywołania <xref:System.Text.EncoderFallbackBuffer> cykliczne do wystąpienia.

To zachowanie ma zastosowanie tylko wtedy, gdy spełnione są wszystkie trzy z następujących warunków:

- Program runtime wykrywa źle sformułowaną sekwencję UTF-16 lub sekwencję UTF-16, której nie można przekonwertować na kodowanie docelowe.
- Określono <xref:System.Text.EncoderFallback> niestandardowy.
- Niestandardowe <xref:System.Text.EncoderFallback> próbuje zastąpić nową nieukształtowaną lub niewymienialną sekwencję UTF-16.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Większość programistów nie musi podejmować żadnych działań.

Jeśli aplikacja używa <xref:System.Text.EncoderFallback> niestandardowego i <xref:System.Text.EncoderFallbackBuffer> klasy, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> upewnij się, że implementacja wypełnia bufor rezerwowy dobrze sformułowanymi danymi UTF-16, które są bezpośrednio konwertowalne do kodowania docelowego, gdy <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> metoda jest po raz pierwszy wywoływana przez program runtime.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
