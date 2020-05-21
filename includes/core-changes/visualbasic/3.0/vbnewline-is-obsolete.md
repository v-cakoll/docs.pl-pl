---
ms.openlocfilehash: 535a73c6b748166a1e4a4661a6bab0671c653278
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721287"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała

<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>Stała jest oznaczona jako [ \[ przestarzała \] ](xref:System.ObsoleteAttribute) , począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 8.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 8

#### <a name="change-description"></a>Zmień opis

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut został zastosowany do <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> stałej. Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora. W .NET Framework i poprzednich wersjach programu .NET Core nie została oznaczona jako przestarzała.

Ta zmiana została wprowadzona w celu obsługi Visual Basic jako języka dla tworzenia wielu platform. <xref:Microsoft.VisualBasic.Constants.vbNewLine>Stała jest równoznaczna z `\r\n` sekwencją znaków nowego wiersza w systemie Windows. W systemach opartych na systemie UNIX znak nowego wiersza to `\n` .

#### <a name="recommended-action"></a>Zalecana akcja

Komunikat o [przestarzałym](xref:System.ObsoleteAttribute) atrybucie dla programu <xref:Microsoft.VisualBasic.Constants.vbNewLine> zawiera następujące zalecenia:

W przypadku powrotu karetki i wysuwu wiersza Użyj <xref:Microsoft.VisualBasic.Constants.vbCrLf> . W przypadku wiersza dla bieżącej platformy Użyj <xref:System.Environment.NewLine?displayProperty=nameWithType> .

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
