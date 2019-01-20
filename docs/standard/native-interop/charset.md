---
title: Zestawów znaków i przeprowadzić marshaling — .NET
description: Dowiedz się, jak różne wartości CharSet można zmienić, jak .NET, kieruje dane do kodu natywnego.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2ff6c485906db481cb5236f83e885ba9fd46450b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416227"
---
# <a name="charsets-and-marshalling"></a>Zestawów znaków i kierowania

Sposób `char` wartości `string` obiekty, i `System.Text.StringBuilder` obiekty są skierowany zależy od wartości `CharSet` pola na P/Invoke lub struktury. Możesz ustawić `CharSet` elementu P/Invoke przez ustawienie <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola podczas deklarowania metody P/Invoke. Aby ustawić `CharSet` struktury, można ustawić <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pola w swojej deklaracji struktury. Jeśli te pola atrybutów nie są ustawione, to kompilator języka, aby określić, które `CharSet` do użycia. C#używa <xref:System.Runtime.InteropServices.CharSet.Ansi> charset domyślnie.

W poniższej tabeli przedstawiono mapowania między każdym charset i jak znak lub ciąg są reprezentowane przy/wycofany z tym zestaw znaków:

| CharSet | Windows | Unix | Narzędzie mono w systemach Unix |
|---------|---------|-------|-------|
| Ansi    | `char` (ANSI)  | `char` (ANSI w systemie macOS, UTF-8 w systemie Linux) | `char` (UTF-8) |
| Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char16_t` (UTF-16) |
| Auto | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char` (UTF-8) |

Upewnij się, że wiesz, jakie reprezentacji z natywną reprezentację oczekuje, że podczas pobierania usługi zestaw znaków.
