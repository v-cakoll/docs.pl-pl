---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449410"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>UnauthorizedAccessException zgłoszone przez FileSystemInfo. Attributes

W programie .NET Core jest generowany <xref:System.UnauthorizedAccessException>, gdy wywołujący próbuje ustawić wartość atrybutu pliku, ale nie ma uprawnienia do zapisu.

#### <a name="change-description"></a>Zmień opis

W .NET Framework jest generowany <xref:System.ArgumentException>, gdy wywołujący próbuje ustawić wartość atrybutu pliku w <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>, ale nie ma uprawnienia do zapisu. W przypadku platformy .NET Core w zamian zostanie zgłoszony <xref:System.UnauthorizedAccessException>. (W środowisku .NET Core jest nadal zgłaszane <xref:System.ArgumentException>, jeśli obiekt wywołujący podejmie próbę ustawienia nieprawidłowego atrybutu pliku).

#### <a name="version-introduced"></a>Wprowadzona wersja

1.0

#### <a name="recommended-action"></a>Zalecana akcja

Zmodyfikuj wszystkie instrukcje `catch`, aby przechwycić <xref:System.UnauthorizedAccessException> zamiast lub oprócz <xref:System.ArgumentException>, w razie potrzeby.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
