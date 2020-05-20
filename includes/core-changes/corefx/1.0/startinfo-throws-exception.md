---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420434"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a>Proces. element StartInfo zgłasza InvalidOperationException dla procesów, które nie zostały uruchomione

Odczytywanie <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> właściwości procesów, w których kod nie został uruchomiony, zgłasza <xref:System.InvalidOperationException> .

#### <a name="change-description"></a>Zmień opis

W .NET Framework dostęp do <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> właściwości dla procesów, których kod nie został uruchomiony, zwraca fikcyjny <xref:System.Diagnostics.ProcessStartInfo> obiekt. Fikcyjny obiekt zawiera wartości domyślne dla wszystkich jego właściwości z wyjątkiem <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> .

Począwszy od platformy .NET Core 1,0, jeśli odczytasz <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> Właściwość dla procesu, który nie został uruchomiony (oznacza to przez wywołanie <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ), <xref:System.InvalidOperationException> jest zgłaszany.

#### <a name="version-introduced"></a>Wprowadzona wersja

1.0

#### <a name="recommended-action"></a>Zalecana akcja

Nie uzyskuj dostępu do <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> właściwości dla procesów, w których kod nie został uruchomiony. Na przykład nie należy odczytywać tej właściwości dla procesów zwracanych przez <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
