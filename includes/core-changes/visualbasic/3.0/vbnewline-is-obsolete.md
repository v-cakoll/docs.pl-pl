---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116367"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała

Stała <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>a jest oznaczona jako [\[przestarzałe\]](xref:System.ObsoleteAttribute) począwszy od platformy .net Core 3,0 wersja zapoznawcza 8.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 8

#### <a name="change-description"></a>Opis zmiany

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut został zastosowany do stałej <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>. Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora. W .NET Framework i poprzednich wersjach programu .NET Core nie została oznaczona jako przestarzała.

Ta zmiana została wprowadzona w celu obsługi Visual Basic jako języka dla tworzenia wielu platform. Stała <xref:Microsoft.VisualBasic.Constants.vbNewLine> jest równoznaczna z `\r\n`, sekwencją znaków nowego wiersza w systemie Windows. W systemach opartych na systemie UNIX znak nowego wiersza jest `\n`.

#### <a name="recommended-action"></a>Zalecane działanie

Komunikat o [nieaktualnym](xref:System.ObsoleteAttribute) atrybucie dla <xref:Microsoft.VisualBasic.Constants.vbNewLine> zawiera następujące zalecenia:

W przypadku powrotu karetki i wysuwu wiersza Użyj <xref:Microsoft.VisualBasic.Constants.vbCrLf>. W przypadku wiersza dla bieżącej platformy Użyj <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Kategoria

Język Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
