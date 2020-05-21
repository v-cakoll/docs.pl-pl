---
ms.openlocfilehash: 00c32c10f77995284264e795d386f699082dcb84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721257"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Niestandardowe wystąpienia EncoderFallbackBuffer nie mogą podlegać rekursywnie

<xref:System.Text.EncoderFallbackBuffer>Wystąpienia niestandardowe nie mogą podlegać rekursywnie. Implementacja <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi skutkować sekwencją znaków, która umożliwia konwersję na kodowanie docelowe. W przeciwnym razie wystąpi wyjątek.

#### <a name="change-description"></a>Zmień opis

Podczas operacji transkodowania typu "Character-to-Byte" środowisko uruchomieniowe wykrywa nieprawidłowo uformowane lub niewymienialne sekwencje UTF-16 i dostarcza te znaki do <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metody. `Fallback`Metoda określa, które znaki mają być zastępowane dla oryginalnych danych nieprzekonwertowanych. te znaki są opróżniane przez wywołanie <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> pętli.

Środowisko uruchomieniowe następnie próbuje transkodowanie te znaki podstawiania do kodowania docelowego. Jeśli ta operacja zakończy się pomyślnie, środowisko uruchomieniowe kontynuuje transkodowanie z miejsca, w którym jest pozostawione w oryginalnym ciągu wejściowym.

W programie .NET Core w wersji zapoznawczej 7 i starszych wersjach niestandardowe implementacje <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> mogą zwracać sekwencje znaków, które nie są konwertowane na kodowanie docelowe. Jeśli podstawiane znaki nie mogą być transkodowane do kodowania docelowego, środowisko uruchomieniowe wywołuje <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metodę raz ponownie z znakami podstawiania, oczekiwanie <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> metody do zwrócenia nowej sekwencji podstawiania. Ten proces jest kontynuowany do momentu, gdy środowisko uruchomieniowe ostatecznie zobaczy dobrze sformułowane, Zastępcze podstawienie lub dopóki nie zostanie osiągnięta maksymalna liczba rekursji.

Począwszy od platformy .NET Core 3,0, niestandardowe implementacje programu <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> muszą zwracać sekwencje znaków, które są konwertowane na kodowanie docelowe. Jeśli podstawiane znaki nie mogą być transkodowane do kodowania docelowego, <xref:System.ArgumentException> zostanie zgłoszony. Środowisko wykonawcze nie będzie już powodowało wywołań cyklicznych do <xref:System.Text.EncoderFallbackBuffer> wystąpienia.

To zachowanie ma zastosowanie tylko wtedy, gdy spełnione są wszystkie trzy z następujących warunków:

- Środowisko uruchomieniowe wykrywa źle sformułowaną sekwencję UTF-16 lub sekwencję UTF-16, której nie można przekonwertować na kodowanie docelowe.
- Określono niestandardową <xref:System.Text.EncoderFallback> .
- Niestandardowa <xref:System.Text.EncoderFallback> próbuje zastąpić nową sekwencję UTF-16 źle sformułowaną lub nieprzekonwertowaną.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Większość deweloperów nie musi podejmować wszelkie działania.

Jeśli aplikacja używa <xref:System.Text.EncoderFallback> klas niestandardowych i <xref:System.Text.EncoderFallbackBuffer> , należy upewnić się, że implementacja <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> wypełnia bufor rezerwowy przy użyciu poprawnie sformułowanych danych UTF-16, które są bezpośrednio konwertowane na kodowanie docelowe, gdy <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> Metoda jest wywoływana po raz pierwszy przez środowisko uruchomieniowe.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
