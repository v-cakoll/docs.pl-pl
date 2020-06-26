---
title: Zestaw znaków i kierowanie — .NET
description: Dowiedz się, w jaki sposób różne wartości zestawów znaków mogą zmienić sposób, w jaki program .NET będzie kierować dane do kodu natywnego.
ms.date: 01/18/2019
ms.openlocfilehash: 39566593aa38bacfa41b44a8af8cc2dfb294d766
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416112"
---
# <a name="charsets-and-marshaling"></a>Zestawy znaków i marshaling

Sposób `char` organizowania wartości, `string` obiektów i `System.Text.StringBuilder` obiektów zależy od wartości `CharSet` pola na P/Invoke lub strukturze. Można ustawić wartość `CharSet` p/Invoke przez ustawienie <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola podczas deklarowania p/Invoke. Aby ustawić `CharSet` dla typu, należy ustawić <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole w deklaracji klasy lub struktury. Gdy te pola atrybutów nie są ustawione, do kompilatora języka można określić, który z nich ma być `CharSet` używany. C# i Visual Basic domyślnie używają zestawu <xref:System.Runtime.InteropServices.CharSet.Ansi> znaków.

W poniższej tabeli przedstawiono mapowanie między poszczególnymi zestawami i sposób reprezentowania znaku lub ciągu podczas organizowania z tym zestawem znaków:

| `CharSet`wartościami | Windows            | .NET Core 2,2 i wcześniejszy w systemie UNIX | .NET Core 3,0 i nowsze i mono w systemie UNIX |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| `Ansi`          | `char`(domyślna [strona kodowa systemu Windows (ANSI)](/windows/win32/intl/code-pages))      | `char`(UTF-8)                    | `char`(UTF-8)                           |
| `Unicode`       | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char16_t`(UTF-16)                      |
| `Auto`          | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char`(UTF-8)                           |

Upewnij się, że wiesz, co należy reprezentować natywną reprezentację podczas wybierania zestawu znaków.
