---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449410"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>UnauthorizedAccessException zgłoszony przez FileSystemInfo.Attributes

W .NET Core <xref:System.UnauthorizedAccessException> jest generowany, gdy obiekt wywołujący próbuje ustawić wartość atrybutu pliku, ale nie ma uprawnień do zapisu.

#### <a name="change-description"></a>Zmień opis

W platformie .NET Framework jest <xref:System.ArgumentException> generowany, gdy obiekt <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> wywołujący próbuje ustawić wartość atrybutu pliku, ale nie ma uprawnień do zapisu. W .NET Core <xref:System.UnauthorizedAccessException> zamiast tego jest generowany. (W .NET Core <xref:System.ArgumentException> jest nadal generowany, jeśli obiekt wywołujący próbuje ustawić nieprawidłowy atrybut pliku).

#### <a name="version-introduced"></a>Wprowadzona wersja

1.0

#### <a name="recommended-action"></a>Zalecana akcja

Zmodyfikuj `catch` <xref:System.UnauthorizedAccessException> wszystkie instrukcje, aby przechwycić <xref:System.ArgumentException>zamiast lub oprócz , w razie potrzeby.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
