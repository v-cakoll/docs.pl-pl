---
title: Zestawów znaków i organizowania — .NET
description: Dowiedz się, jak różne wartości CharSet można zmienić, jak .NET, kieruje dane do kodu natywnego.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: c50c58ad639b1efb29c13e5124fe3c32e8af96fc
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063336"
---
# <a name="charsets-and-marshaling"></a>Zestawów znaków i organizowanie

Sposób `char` wartości `string` obiekty, i `System.Text.StringBuilder` obiekty są organizowane zależy od wartości `CharSet` pola na P/Invoke lub struktury. Możesz ustawić `CharSet` elementu P/Invoke przez ustawienie <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola podczas deklarowania metody P/Invoke. Aby ustawić `CharSet` struktury, można ustawić <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pola w swojej deklaracji struktury. Jeśli te pola atrybutów nie są ustawione, to kompilator języka, aby określić, które `CharSet` do użycia. C#użytkowania VB <xref:System.Runtime.InteropServices.CharSet.Ansi> charset domyślnie.

W poniższej tabeli przedstawiono mapowania między każdym charset i jak znak lub ciąg jest reprezentowana podczas przekazywania za pomocą tego zestaw znaków:

| `CharSet` Wartość | Windows            | .NET core 2.2 i wcześniej na Unix | .NET core 3.0 i nowszych, jak i narzędzia Mono w systemach Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (ANSI)      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Auto            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Upewnij się, że wiesz, jakie reprezentacji z natywną reprezentację oczekuje, że podczas pobierania usługi zestaw znaków.
