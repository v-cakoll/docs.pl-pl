---
title: Zestaw znaków i kierowanie — .NET
description: Dowiedz się, w jaki sposób różne wartości zestawów znaków mogą zmienić sposób, w jaki program .NET będzie kierować dane do kodu natywnego.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: cac71c5d09514dfe1244d16224944e05826edfa9
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817840"
---
# <a name="charsets-and-marshaling"></a>Zestawy znaków i marshaling

Sposób `char` organizowania wartości, `string` obiektów i `System.Text.StringBuilder` obiektów zależy od wartości `CharSet` pola na P/Invoke lub strukturze. Można ustawić `CharSet` wartość p/Invoke przez <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> ustawienie pola podczas deklarowania p/Invoke. Aby ustawić `CharSet` dla struktury, należy <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> ustawić pole w deklaracji struktury. Gdy te pola atrybutów nie są ustawione, do kompilatora języka można określić, który `CharSet` z nich ma być używany. C#i VB domyślnie używają <xref:System.Runtime.InteropServices.CharSet.Ansi> zestawu znaków.

W poniższej tabeli przedstawiono mapowanie między poszczególnymi zestawami i sposób reprezentowania znaku lub ciągu podczas organizowania z tym zestawem znaków:

| `CharSet`wartościami | Windows            | .NET Core 2,2 i wcześniejszy w systemie UNIX | .NET Core 3,0 i nowsze i mono w systemie UNIX |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char`(domyślna [strona kodowa systemu Windows (ANSI)](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char16_t`(UTF-16)                      |
| Auto            | `wchar_t`(UTF-16) | `char16_t`(UTF-16)               | `char` (UTF-8)                           |

Upewnij się, że wiesz, co należy reprezentować natywną reprezentację podczas wybierania zestawu znaków.
