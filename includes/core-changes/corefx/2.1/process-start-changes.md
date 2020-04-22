---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021808"
---
### <a name="change-in-default-value-of-useshellexecute"></a>Zmiana wartości domyślnej UseShellExecute

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>ma wartość domyślną `false` na .NET Core. W programie .NET Framework `true`jego wartością domyślną jest .

#### <a name="change-description"></a>Zmień opis

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>umożliwia uruchomienie aplikacji bezpośrednio, na przykład z `Process.Start("mspaint.exe")` kodem takim jak uruchamia paint. Umożliwia również pośrednie uruchomienie skojarzonej <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> aplikacji, `true`jeśli jest ustawiona na . W programie .NET Framework <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> domyślną wartością `true`jest `Process.Start("mytextfile.txt")` , co oznacza, że kod, taki jak uruchomienie Notatnika, jeśli skojarzono pliki *.txt* z tym edytorem. Aby zapobiec pośredniemu uruchamianiu aplikacji w programie .NET `false`Framework, należy jawnie ustawić wartość <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> . W programie .NET Core <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> wartością domyślną jest `false`. Oznacza to, że domyślnie skojarzone aplikacje `Process.Start`nie są uruchamiane podczas wywoływania .

Ta zmiana została wprowadzona w .NET Core ze względu na wydajność. Zazwyczaj <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> jest używany do uruchamiania aplikacji bezpośrednio. Bezpośrednie uruchamianie aplikacji nie musi obejmować powłoki systemu Windows i ponosić skojarzony koszt wydajności. Aby przyspieszyć ten domyślny przypadek, program .NET Core zmienia domyślną wartość <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> na `false`. Jeśli jej potrzebujesz, możesz zdecydować się na wolniejszą ścieżkę.

#### <a name="version-introduced"></a>Wprowadzono wersję

2.1

> [!NOTE]
> We wcześniejszych wersjach programu `UseShellExecute` .NET Core nie został zaimplementowany dla systemu Windows.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli aplikacja opiera się na <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> stare <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> zachowanie, <xref:System.Diagnostics.ProcessStartInfo> wywołać z ustawioną `true` na obiekt.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
