---
ms.openlocfilehash: f7c13688236f3d66f3225ecf5d93b4c3284e2e71
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002891"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała

Stała <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> jest oznaczona jako [przestarzała](xref:System.ObsoleteAttribute) , rozpoczynając od platformy .net Core 3,0 wersja zapoznawcza 8.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 8

#### <a name="details"></a>Szczegóły

Począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut został zastosowany do stałej <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>. Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora. W poprzednich wersjach programu .NET Core i .NET Framework nie została oznaczona jako przestarzała.

Ta zmiana została wprowadzona w celu obsługi Visual Basic jako języka dla tworzenia wielu platform. Stała `vbNewLine` jest równoważna z `\r\n`, sekwencją znaków nowego wiersza w systemie Windows. W systemach opartych na systemie UNIX znak nowego wiersza jest `\n`.
 
#### <a name="recommended-action"></a>Zalecana akcja

Komunikat o [nieaktualnym](xref:System.ObsoleteAttribute) atrybucie dla `vbNewLine` obejmuje następujące zalecenia:

> W przypadku powrotu karetki i wysuwu wiersza Użyj [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf). W przypadku wiersza bieżącej platformy Użyj <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

