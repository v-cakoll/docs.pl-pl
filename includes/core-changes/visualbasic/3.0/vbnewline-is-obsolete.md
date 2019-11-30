---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567459"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała

Stała <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>a jest oznaczona jako [przestarzała](xref:System.ObsoleteAttribute) , rozpoczynając od platformy .net Core 3,0 wersja zapoznawcza 8.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 8

#### <a name="change-description"></a>Zmień opis

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut został zastosowany do stałej <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>. Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora. W poprzednich wersjach programu .NET Core i .NET Framework nie została oznaczona jako przestarzała.

Ta zmiana została wprowadzona w celu obsługi Visual Basic jako języka dla tworzenia wielu platform. Stała `vbNewLine` jest równoznaczna z `\r\n`, sekwencją znaków nowego wiersza w systemie Windows. W systemach opartych na systemie UNIX znak nowego wiersza jest `\n`.

#### <a name="recommended-action"></a>Zalecane działanie

Komunikat o [nieaktualnym](xref:System.ObsoleteAttribute) atrybucie dla `vbNewLine` zawiera następujące zalecenia:

> W przypadku powrotu karetki i wysuwu wiersza Użyj [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf). W przypadku wiersza dla bieżącej platformy Użyj <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Kategoria

Język Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
