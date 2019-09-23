---
ms.openlocfilehash: 5ef785f476b795a9c53e511d51b2683b99e6da05
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181994"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała

Stała jest oznaczona jako [przestarzała](xref:System.ObsoleteAttribute) , począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 8. <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="details"></a>Szczegóły

Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> został zastosowany do stałej. Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora. W poprzednich wersjach programu .NET Core i .NET Framework nie została oznaczona jako przestarzała.

Ta zmiana została wprowadzona w celu obsługi Visual Basic jako języka dla tworzenia wielu platform. Stała jest równoznaczna z `\r\n`sekwencją znaków nowego wiersza w systemie Windows. `vbNewLine` W systemach opartych na systemie UNIX znak nowego wiersza `\n`to.
 
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

