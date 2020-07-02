---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620317"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>Nazwa pliku dziennika utworzona przez metodę ObjectContext. isdatabase zmieniła się, aby pasowała do specyfikacji SQL Server

#### <a name="details"></a>Szczegóły

Gdy <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> Metoda jest wywoływana bezpośrednio lub za pomocą Code First z dostawcą SqlClient i wartością AttachDBFileName w parametrach połączenia, tworzy plik dziennika o nazwie filename_log. ldf zamiast FileName. ldf (gdzie filename to nazwa pliku określonego przez wartość AttachDBFileName). Ta zmiana usprawnia proces debugowania, dostarczając plik dziennika o nazwie zgodnej ze specyfikacjami programu SQL Server.

#### <a name="suggestion"></a>Sugestia

Jeśli nazwa pliku dziennika jest ważna dla aplikacji, należy zaktualizować aplikację, tak aby była oczekiwana standardowa format nazwy pliku _log. ldf.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
