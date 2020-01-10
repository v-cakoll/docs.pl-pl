---
title: Zestaw znaków i kierowanie — .NET
description: Dowiedz się, w jaki sposób różne wartości zestawów znaków mogą zmienić sposób, w jaki program .NET będzie kierować dane do kodu natywnego.
ms.date: 01/18/2019
ms.openlocfilehash: 4be4bd5a968eb5c0d6959a0f378ee1223ed906ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706390"
---
# <a name="charsets-and-marshaling"></a>Zestawy znaków i marshaling

Sposób, w jaki `char` wartości, obiekty `string` i obiekty `System.Text.StringBuilder` są organizowane, zależy od wartości pola `CharSet` na P/Invoke lub strukturze. Można ustawić `CharSet` P/Invoke przez ustawienie pola <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> podczas deklarowania P/Invoke. Aby ustawić `CharSet` dla typu, należy ustawić pole <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> w deklaracji klasy lub struktury. Gdy te pola atrybutów nie są ustawione, jest do kompilatora języka, aby określić, który `CharSet` do użycia. C#i Visual Basic używać zestawu znaków <xref:System.Runtime.InteropServices.CharSet.Ansi> domyślnie.

W poniższej tabeli przedstawiono mapowanie między poszczególnymi zestawami i sposób reprezentowania znaku lub ciągu podczas organizowania z tym zestawem znaków:

| wartość `CharSet` | Windows            | .NET Core 2,2 i wcześniejszy w systemie UNIX | .NET Core 3,0 i nowsze i mono w systemie UNIX |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (domyślna [strona kodowa systemu Windows (ANSI)](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Auto            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Upewnij się, że wiesz, co należy reprezentować natywną reprezentację podczas wybierania zestawu znaków.
