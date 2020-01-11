---
title: Ograniczenia ADO.NET
ms.date: 12/13/2019
description: W tym artykule opisano niektóre z ADO.NETych ograniczeń, które można napotkać.
ms.openlocfilehash: 8664b73071fc859ed30080f549b05e7d6ed020f4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901250"
---
# <a name="adonet-limitations"></a>Ograniczenia ADO.NET

Microsoft. Data. sqlite udostępnia implementacje wielu streszczeń ADO.NET, ale istnieją pewne ograniczenia.

## <a name="database-schema-information"></a>Informacje o schemacie bazy danych

Metadane dotyczące wyników zapytania są dostępne za pomocą metody <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A>.

`DbConnection.GetSchema()` nie jest zaimplementowana. Ten interfejs API nie jest dobrze zdefiniowany, dlatego zalecamy pobranie metadanych bazy danych bezpośrednio przy użyciu standardowych interfejsów API programu SQLite, takich jak tabela [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) i [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) pragma.

Aby uzyskać więcej informacji, zobacz [metadane](metadata.md).

## <a name="systemtransactions"></a>System. Transactions

Firma Microsoft. Data. sqlite nie obsługuje jeszcze system. Transactions. Zamiast tego użyj transakcji ADO.NET. Aby uzyskać więcej informacji, zobacz [transakcje](transactions.md).

Prześlij opinię na temat braku obsługi dla elementu System. Transactions w przypadku problemu [#13825](https://github.com/dotnet/efcore/issues/13825).

## <a name="data-adapters"></a>Karty danych

`DbDataAdapter` nie została jeszcze zaimplementowana przez firmę Microsoft. Data. sqlite. Oznacza to, że można używać ADO.NET `DataSet` i `DataTable` do ładowania danych i ich aktualizowania.

Użyj [#13838](https://github.com/dotnet/efcore/issues/13838) problemu, aby przekazać opinię na temat implementowania `DbDataAdapter`.

## <a name="output-parameters"></a>Parametry wyjściowe

Produkt SQLite nie obsługuje parametrów wyjściowych.

## <a name="positional-parameters"></a>Parametry pozycyjne

Microsoft. Data. sqlite obsługuje tylko nazwane [Parametry](parameters.md). Parametry pozycyjne nie są obsługiwane.

## <a name="stored-procedures"></a>Procedury składowane

SQLite nie obsługuje procedur składowanych.

## <a name="isolation-levels"></a>Poziomy izolacji

Poziomy izolacji `Chaos` i `Snapshot` nie są obsługiwane w transakcjach oprogramowania SQLite.

## <a name="see-also"></a>Zobacz także

* [Ograniczenia asynchroniczne](async.md)
* [Typy danych](types.md)
* [Transakcje](transactions.md)
