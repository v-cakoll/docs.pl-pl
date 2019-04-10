---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
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
