---
ms.openlocfilehash: fa09831ac47a59535ff73c8c8680c2642c3248c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235521"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>SqlBulkCopy używa, miejsce docelowe kodowania kolumny ciągów

|   |   |
|---|---|
|Szczegóły|Podczas wstawiania danych do kolumny, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> używa kodowania kolumny docelowej zamiast domyślnego kodowania <code>VARCHAR</code> i <code>CHAR</code> typów. Ta zmiana eliminuje możliwość uszkodzenia danych na skutek użycia domyślnego kodowania w sytuacji, gdy w kolumnie docelowej nie jest używane kodowanie domyślne. W rzadkich przypadkach istniejąca aplikacja może zgłaszać wyjątek sqlexception — Jeśli ta zmiana kodowania skutkuje danymi, które jest zbyt duży, aby mieściły się w kolumnie docelowej.|
|Sugestia|Oczekuje, że <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> już spowoduje uszkodzenie danych ze względu na różnice kodowania. Jeśli ciągi osiągnięty limit rozmiaru kolumny docelowej są kopiowane, może być konieczne albo wstępnie zakodowania danych (w celu skopiowania do sprawdzenia, czy dane będą zgodne w kolumnie docelowej) lub przechwycić <xref:System.Data.SqlClient.SqlException?displayProperty=name>s.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)?displayProperty=nameWithType></li></ul>|
