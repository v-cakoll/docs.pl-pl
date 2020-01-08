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
# <a name="interoperability"></a><span data-ttu-id="83ef6-103">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="83ef6-103">Interoperability</span></span>

<span data-ttu-id="83ef6-104">Microsoft. Data. sqlite używa SQLitePCLRaw do korzystania z natywnej biblioteki programu SQLite.</span><span class="sxs-lookup"><span data-stu-id="83ef6-104">Microsoft.Data.Sqlite uses SQLitePCLRaw to interact with the native SQLite library.</span></span> <span data-ttu-id="83ef6-105">SQLitePCLRaw udostępnia cienki interfejs API platformy .NET za pośrednictwem natywnego interfejsu API programu SQLite.</span><span class="sxs-lookup"><span data-stu-id="83ef6-105">SQLitePCLRaw provides a thin .NET API over the native SQLite API.</span></span> <span data-ttu-id="83ef6-106">SqliteConnection i SqliteDataReader zapewniają dostęp do podstawowych obiektów SQLitePCLRaw, które umożliwiają bezpośrednie wywoływanie tych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="83ef6-106">SqliteConnection and SqliteDataReader provide access to the underlying SQLitePCLRaw objects letting you call these APIs directly.</span></span>

<span data-ttu-id="83ef6-107">Poniższy przykład pokazuje, jak wywoływać `sqlite3_trace`, aby napisać wykonane instrukcje SQL do konsoli:</span><span class="sxs-lookup"><span data-stu-id="83ef6-107">The following example shows how to call `sqlite3_trace` to write executed SQL statements to the console:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

<span data-ttu-id="83ef6-108">W poniższym przykładzie pokazano wywoływanie `sqlite3_stmt_status`, aby sprawdzić, jak wiele maszyn wirtualnych z systemem SQLite ma wykonać instrukcję SQL skompilowaną w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="83ef6-108">And the following example shows calling `sqlite3_stmt_status` to see how many SQLite virtual machine steps a SQL statement compiled into:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

<span data-ttu-id="83ef6-109">Obiekty SQLitePCLRaw nawet uwidaczniają wskaźnik do obiektów natywnych, dzięki czemu można P/wywołać dodatkowe natywne interfejsy API oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="83ef6-109">The SQLitePCLRaw objects even expose a pointer to the native objects letting you P/Invoke additional native SQLite APIs.</span></span>
