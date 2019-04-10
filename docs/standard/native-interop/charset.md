---
title: Zestawów znaków i przeprowadzić marshaling — .NET
description: Dowiedz się, jak różne wartości CharSet można zmienić, jak .NET, kieruje dane do kodu natywnego.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 0b9ea8498b56e6d14770cf57e7e82b9992b1ee50
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299880"
---
# <a name="charsets-and-marshalling"></a>Zestawów znaków i kierowania

Sposób `char` wartości `string` obiekty, i `System.Text.StringBuilder` obiekty są skierowany zależy od wartości `CharSet` pola na P/Invoke lub struktury. Możesz ustawić `CharSet` elementu P/Invoke przez ustawienie <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola podczas deklarowania metody P/Invoke. Aby ustawić `CharSet` struktury, można ustawić <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pola w swojej deklaracji struktury. Jeśli te pola atrybutów nie są ustawione, to kompilator języka, aby określić, które `CharSet` do użycia. C#użytkowania VB <xref:System.Runtime.InteropServices.CharSet.Ansi> charset domyślnie.

W poniższej tabeli przedstawiono mapowania między każdym charset i jak znak lub ciąg są reprezentowane przy/wycofany z tym zestaw znaków:

| CharSet | Windows            | Unix                                   | Narzędzie mono w systemach Unix        |
|---------|--------------------|----------------------------------------|---------------------|
| Ansi    | `char` (ANSI)      | `char` (ANSI w systemie macOS, UTF-8 w systemie Linux) | `char` (UTF-8)      |
| Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16)                    | `char16_t` (UTF-16) |
| Auto    | `wchar_t` (UTF-16) | `char16_t` (UTF-16)                    | `char` (UTF-8)      |

Upewnij się, że wiesz, jakie reprezentacji z natywną reprezentację oczekuje, że podczas pobierania usługi zestaw znaków.
