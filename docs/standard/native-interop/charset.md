---
title: Zestawów znaków i przeprowadzić marshaling — .NET
description: Dowiedz się, jak różne wartości CharSet można zmienić, jak .NET, kieruje dane do kodu natywnego.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: f436bbbf435df07d242f9bf295b0264c4cfd5b3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480849"
---
# <a name="charsets-and-marshalling"></a>Zestawów znaków i kierowania

Sposób `char` wartości `string` obiekty, i `System.Text.StringBuilder` obiekty są skierowany zależy od wartości `CharSet` pola na P/Invoke lub struktury. Możesz ustawić `CharSet` elementu P/Invoke przez ustawienie <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola podczas deklarowania metody P/Invoke. Aby ustawić `CharSet` struktury, można ustawić <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pola w swojej deklaracji struktury. Jeśli te pola atrybutów nie są ustawione, to kompilator języka, aby określić, które `CharSet` do użycia. C#użytkowania VB <xref:System.Runtime.InteropServices.CharSet.Ansi> charset domyślnie.

W poniższej tabeli przedstawiono mapowania między każdym charset i jak znak lub ciąg są reprezentowane przy/wycofany z tym zestaw znaków:

| CharSet | Windows            | UNIX w programie .NET Core 2.2 i starszych wersji | Narzędzie mono i Unix w programie .NET Core 3.0 i nowszych |
|---------|--------------------|-----------------------------|------------------------------------------|
| Ansi    | `char` (ANSI)      | `char` (UTF-8)              | `char` (UTF-8)                           |
| Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16)         | `char16_t` (UTF-16)                      |
| Auto    | `wchar_t` (UTF-16) | `char16_t` (UTF-16)         | `char` (UTF-8)                           |

Upewnij się, że wiesz, jakie reprezentacji z natywną reprezentację oczekuje, że podczas pobierania usługi zestaw znaków.
