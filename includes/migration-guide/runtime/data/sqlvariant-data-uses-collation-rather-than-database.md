---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235533"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>Dane typu Sql_variant używa sortowania sql_variant, a nie sortowania bazy danych

|   |   |
|---|---|
|Szczegóły|<code>sql_variant</code> danych używa <code>sql_variant</code> sortowania zamiast sortowania bazy danych.|
|Sugestia|Ta zmiana dotyczy możliwego uszkodzenia danych, jeśli sortowanie bazy danych różni się od <code>sql_variant</code> sortowania. W aplikacjach korzystających z uszkodzonych danych może wystąpić błąd.|
|Zakres|Przezroczyste|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
