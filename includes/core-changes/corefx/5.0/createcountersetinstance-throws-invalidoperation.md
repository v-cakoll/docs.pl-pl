---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144487"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>Element CounterSet. CreateCounterSetInstance teraz zgłasza InvalidOperationException, jeśli wystąpienie już istnieje

Począwszy od programu .NET 5,0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> zgłasza <xref:System.InvalidOperationException> zamiast tego, <xref:System.ArgumentException> czy zestaw liczników już istnieje.

#### <a name="change-description"></a>Zmień opis

W .NET Framework i .NET Core 1,0 do 3,1 można utworzyć wystąpienie zestawu liczników przez wywołanie <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> . Jeśli jednak zestaw liczników już istnieje, metoda zgłasza <xref:System.ArgumentException> wyjątek.

W przypadku programu .NET 5,0 i jego nowszych wersji, gdy wywoływany <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> jest zestaw liczników, <xref:System.InvalidOperationException> zgłaszany jest wyjątek.

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 5

#### <a name="recommended-action"></a>Zalecana akcja

W przypadku przechwytywania <xref:System.ArgumentException> wyjątków w aplikacji podczas wywoływania <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> należy rozważyć również przechwycenie <xref:System.InvalidOperationException> wyjątków.

> [!NOTE]
> <xref:System.ArgumentException>Nie zaleca się przechwytywania wyjątków.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
