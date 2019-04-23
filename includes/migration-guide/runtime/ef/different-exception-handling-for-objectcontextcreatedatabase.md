---
ms.openlocfilehash: 33ad1c044001e0a8d09708cc7a1f06e05cb307de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804735"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Obsługa dla metod ObjectContext.CreateDatabase i DbProviderServices.CreateDatabase różnych wyjątków

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, w przypadku niepowodzenia tworzenia bazy danych <code>CreateDatabase</code> metod będzie próbował usunąć pustej bazy danych. Jeśli ta operacja zakończy się powodzeniem, oryginalnym <xref:System.Data.SqlClient.SqlException?displayProperty=name> będą propagowane (zamiast <xref:System.InvalidOperationException?displayProperty=name> , zawsze został zgłoszony w .NET Framework 4.0)|
|Sugestia|Gdy przechwytywanie <xref:System.InvalidOperationException?displayProperty=name> podczas wykonywania <xref:System.Data.Objects.ObjectContext.CreateDatabase> lub <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions powinien teraz również zostać przechwycony.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
