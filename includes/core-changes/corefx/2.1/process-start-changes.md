---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449408"
---
### <a name="change-in-default-value-of-useshellexecute"></a>Zmiana wartości domyślnej programu UseShellExecute

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>ma domyślną `false` wartość na .NET Core. W platformie .NET Framework `true`jego wartością domyślną jest .

#### <a name="change-description"></a>Zmień opis

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>umożliwia bezpośrednie uruchomienie aplikacji, na przykład za `Process.Start("mspaint.exe")` pomocą kodu, takiego jak uruchamianie programu Paint. Umożliwia również pośrednie uruchomienie skojarzonej aplikacji, jeśli <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> jest ustawiona na `true`. W programie .NET Framework <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> wartością domyślną `true`jest `Process.Start("mytextfile.txt")` , co oznacza, że kod taki jak uruchomi Notatnik, jeśli pliki *txt* zostały skojarzone z tym edytorem. Aby zapobiec pośredniemu uruchamianiu aplikacji w platformie .NET Framework, należy jawnie ustawić <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> wartość `false`. W uspolu .NET Core <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`wartością domyślną jest wartość . Oznacza to, że domyślnie skojarzone aplikacje `Process.Start`nie są uruchamiane podczas nawiązywania połączenia .

Ta zmiana została wprowadzona w .NET Core ze względu na wydajność. Zazwyczaj <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> służy do bezpośredniego uruchamiania aplikacji. Bezpośrednie uruchomienie aplikacji nie musi obejmować powłoki systemu Windows i ponoszenia skojarzonych kosztów wydajności. Aby przyspieszyć tę domyślną obudowę, program <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> .NET Core zmienia wartość domyślną wartości na `false`. Jeśli jej potrzebujesz, możesz wybrać się na wolniejszą ścieżkę.

#### <a name="version-introduced"></a>Wprowadzona wersja

2.1

> [!NOTE]
> We wcześniejszych wersjach programu `UseShellExecute` .NET Core nie został zaimplementowany dla systemu Windows.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli aplikacja opiera się na <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> stare <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> zachowanie, wywołać `true` z ustawionyna <xref:System.Diagnostics.ProcessStartInfo> na obiekcie.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
