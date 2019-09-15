---
ms.openlocfilehash: 2a0ebcf61fd96df6d2235962c1f1e9cac3fb22e6
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988501"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała

Stała jest oznaczona jako [przestarzała](xref:System.ObsoleteAttribute) w .NET Framework, ale atrybut nie był wcześniej w bibliotece .NET Core 3,0. <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="details"></a>Szczegóły

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> został zastosowany do `vbNewLine` stałej, która jest zgodna z .NET Framework. `vbNewLine` Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora. 

W poprzednich wersjach programu .NET Core program `vbNewLine` nie wygenerował ostrzeżenia kompilatora.

#### <a name="recommended-action"></a>Zalecana akcja

Komunikat o [przestarzałym](xref:System.ObsoleteAttribute) atrybucie `vbNewLine` dla programu zawiera następujące zalecenia:

> W przypadku powrotu karetki i wysuwu wiersza Użyj [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf). W przypadku wiersza dla bieżącej platformy Użyj <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

