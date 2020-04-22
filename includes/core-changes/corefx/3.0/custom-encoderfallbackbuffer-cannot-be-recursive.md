---
ms.openlocfilehash: 820825f0545aa78729414c388385b339225b1235
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021669"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Niestandardowe enkoderFallbackBuffer wystąpienia nie mogą cofać się rekursywnie

Wystąpienia <xref:System.Text.EncoderFallbackBuffer> niestandardowe nie mogą cofać się rekursywnie. Implementacja <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi spowodować sekwencji znaków, który jest konwertowany na kodowanie docelowe. W przeciwnym razie wystąpi wyjątek.

#### <a name="change-description"></a>Zmień opis

Podczas operacji transkodowania typu znak-bajt środowisko wykonawcze wykrywa źle sformułowane lub nieprzekonalne sekwencje UTF-16 i udostępnia te znaki do <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metody. Metoda `Fallback` określa, które znaki powinny być zastępowane oryginalnymi danymi nieprzeszkłonowymi, a te znaki są opróżniane przez wywołanie <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> w pętli.

Środowisko wykonawcze następnie próbuje transkodować te znaki podstawienia do kodowania docelowego. Jeśli ta operacja zakończy się pomyślnie, środowisko wykonawcze kontynuuje transkodowanie, z którego zostało przerwane w oryginalnym ciągu wejściowym.

W .NET Core Preview 7 i wcześniejszych <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> wersjach niestandardowe implementacje mogą zwracać sekwencje znaków, które nie są konwerteralne do kodowania docelowego. Jeśli zastąpione znaki nie mogą być transkodowane do kodowania <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> docelowego, środowisko wykonawcze wywołuje <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> metodę ponownie ze znakami podstawienia, oczekując, że metoda zwraca nową sekwencję podstawiania. Ten proces jest kontynuowany, aż środowisko wykonawcze po pewnym czasie widzi dobrze sformułowane, konwersowane podstawienie lub do osiągnięcia maksymalnej liczby rekursji.

Począwszy od .NET Core 3.0, niestandardowe implementacje <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi zwracać sekwencje znaków, które są konwertowane do kodowania docelowego. Jeśli podstawione znaki nie mogą być transkodowane <xref:System.ArgumentException> do kodowania docelowego, jest generowany. Środowisko wykonawcze nie będzie już wykonywać wywołania cykliczne do <xref:System.Text.EncoderFallbackBuffer> wystąpienia.

To zachowanie ma zastosowanie tylko wtedy, gdy spełnione są wszystkie trzy z następujących warunków:

- Środowisko wykonawcze wykrywa źle sformułowaną sekwencję UTF-16 lub sekwencję UTF-16, których nie można przekonwertować na kodowanie docelowe.
- Określono <xref:System.Text.EncoderFallback> niestandardowe.
- Niestandardowe <xref:System.Text.EncoderFallback> próby zastąpienia nowej źle utworzonej lub nieprzekonalnej sekwencji UTF-16.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Większość programistów nie musi podejmować żadnych działań.

Jeśli aplikacja używa <xref:System.Text.EncoderFallback> niestandardowe <xref:System.Text.EncoderFallbackBuffer> i klasy, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> upewnij się, że implementacja wypełnia bufor rezerwowy z dobrze sformułowanych danych UTF-16, który jest bezpośrednio konwertowane do kodowania docelowego, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> gdy metoda jest po raz pierwszy wywoływana przez środowisko wykonawcze.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
