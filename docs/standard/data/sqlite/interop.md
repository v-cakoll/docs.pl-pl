---
title: Współdziałanie
ms.date: 12/13/2019
description: Dowiedz się, jak współpracować z innymi bibliotekami oprogramowania SQLite.
ms.openlocfilehash: 486e2a8e00999b8ebe9c85a5fcc1539c514676d3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447238"
---
# <a name="interoperability"></a>Współdziałanie

Microsoft. Data. sqlite używa SQLitePCLRaw do korzystania z natywnej biblioteki programu SQLite. SQLitePCLRaw udostępnia cienki interfejs API platformy .NET za pośrednictwem natywnego interfejsu API programu SQLite. SqliteConnection i SqliteDataReader zapewniają dostęp do podstawowych obiektów SQLitePCLRaw, które umożliwiają bezpośrednie wywoływanie tych interfejsów API.

Poniższy przykład pokazuje, jak wywołać `sqlite3_trace` , aby napisać wykonane instrukcje SQL do konsoli programu:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

Poniższy przykład pokazuje, jak wiele `sqlite3_stmt_status` maszyn wirtualnych z systemem SQLite ma wykonać instrukcję SQL skompilowaną do:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

Obiekty SQLitePCLRaw nawet uwidaczniają wskaźnik do obiektów natywnych, dzięki czemu można P/wywołać dodatkowe natywne interfejsy API oprogramowania SQLite.
