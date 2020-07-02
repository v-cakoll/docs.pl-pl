---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620288"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a>Sql_variant dane używają sortowania sql_variant zamiast sortowania bazy danych

#### <a name="details"></a>Szczegóły

<code>sql_variant</code>dane korzystają z <code>sql_variant</code> sortowania zamiast sortowania bazy danych.

#### <a name="suggestion"></a>Sugestia

Ta zmiana dotyczy możliwego uszkodzenia danych, jeśli sortowanie bazy danych różni się od <code>sql_variant</code> sortowania. W aplikacjach korzystających z uszkodzonych danych może wystąpić błąd.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Przezroczyste|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
