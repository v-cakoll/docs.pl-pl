---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021822"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>NieautoryzowaneaccessException generowane przez FileSystemInfo.Attributes

W .NET Core <xref:System.UnauthorizedAccessException> jest generowany, gdy wywołujący próbuje ustawić wartość atrybutu pliku, ale nie ma uprawnień do zapisu.

#### <a name="change-description"></a>Zmień opis

W .NET Framework <xref:System.ArgumentException> jest generowany, gdy wywołujący próbuje ustawić <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> wartość atrybutu pliku, ale nie ma uprawnień do zapisu. W .NET Core <xref:System.UnauthorizedAccessException> zamiast tego jest wyrzucany. (W .NET Core <xref:System.ArgumentException> program .NET Core jest nadal generowany, jeśli wywołujący próbuje ustawić nieprawidłowy atrybut pliku).

#### <a name="version-introduced"></a>Wprowadzono wersję

1.0

#### <a name="recommended-action"></a>Zalecana akcja

Zmodyfikuj wszystkie `catch` instrukcje, aby złapać <xref:System.UnauthorizedAccessException> zamiast lub oprócz , <xref:System.ArgumentException>w razie potrzeby.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
