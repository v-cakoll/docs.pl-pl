---
title: Zestaw znaków i kierowanie — .NET
description: Dowiedz się, w jaki sposób różne wartości zestawów znaków mogą zmienić sposób, w jaki program .NET będzie kierować dane do kodu natywnego.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 301fa3d8bd379e76a0e751c3a20d0d8be37d9ac0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700924"
---
# <a name="charsets-and-marshaling"></a>Zestawy znaków i marshaling

Sposób, w jaki wartości `char`, obiekty `string` i `System.Text.StringBuilder` są organizowane, zależy od wartości pola `CharSet` na stronie P/Invoke lub strukturze. Można ustawić `CharSet` elementu P/Invoke przez ustawienie pola <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> podczas deklarowania P/Invoke. Aby ustawić `CharSet` dla typu, należy ustawić pole <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> w deklaracji klasy lub struktury. Gdy te pola atrybutów nie są ustawione, jest do kompilatora języka, aby określić, który `CharSet` ma być używany. C#i VB domyślnie Użyj zestawu znaków <xref:System.Runtime.InteropServices.CharSet.Ansi>.

W poniższej tabeli przedstawiono mapowanie między poszczególnymi zestawami i sposób reprezentowania znaku lub ciągu podczas organizowania z tym zestawem znaków:

| wartość `CharSet` | Windows            | .NET Core 2,2 i wcześniejszy w systemie UNIX | .NET Core 3,0 i nowsze i mono w systemie UNIX |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (domyślna [strona kodowa systemu Windows (ANSI)](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Auto            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Upewnij się, że wiesz, co należy reprezentować natywną reprezentację podczas wybierania zestawu znaków.
