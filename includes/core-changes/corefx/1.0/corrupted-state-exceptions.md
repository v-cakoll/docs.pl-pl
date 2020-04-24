---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135632"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a>Obsługa wyjątków uszkodzonych stanów nie jest obsługiwana

Obsługa wyjątków uszkodzonego stanu procesu w programie .NET Core nie jest obsługiwana.

#### <a name="change-description"></a>Zmień opis

Wcześniej wyjątki z uszkodzonym stanem procesu mogą być przechwytywane i obsługiwane przez program obsługi wyjątków kodu zarządzanego, na przykład przy użyciu instrukcji [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) w języku C#.

Począwszy od platformy .NET Core 1,0, wyjątki stanu uszkodzonego procesu nie mogą być obsługiwane przez kod zarządzany. Środowisko uruchomieniowe języka wspólnego nie dostarcza wyjątków o uszkodzonym stanie do kodu zarządzanego.

#### <a name="version-introduced"></a>Wprowadzona wersja

1.0

#### <a name="recommended-action"></a>Zalecana akcja

Należy unikać konieczności obsługi wyjątków uszkodzonego stanu przez odnoszące się do nich sytuacje. Jeśli jest absolutnie niezbędne do obsługi wyjątków uszkodzonego stanu procesu, należy napisać procedurę obsługi wyjątków w kodzie C lub C++.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [legacyCorruptedStateExceptionsPolicy, element](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
