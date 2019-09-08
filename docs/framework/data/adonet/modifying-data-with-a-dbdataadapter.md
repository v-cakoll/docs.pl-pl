---
title: Modyfikowanie danych za pomocą obiektu DbDataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: cd1f5faa0efe141dc064f0150b94807b90e7e2b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794822"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Modyfikowanie danych za pomocą obiektu DbDataAdapter
<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> Metoda obiektu<xref:System.Data.Common.DbProviderFactory> daje obiekt,któryjestsilniewpisanado<xref:System.Data.Common.DbDataAdapter> źródłowego dostawcy danych określonego podczas tworzenia fabryki. Następnie można użyć programu, <xref:System.Data.Common.DbCommandBuilder> aby utworzyć polecenia do wstawiania, aktualizowania i usuwania danych <xref:System.Data.DataSet> ze źródła danych.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Pobieranie danych przy użyciu DbDataAdapter  
 W tym przykładzie pokazano, jak utworzyć silnie `DbDataAdapter` wpisaną na podstawie nazwy dostawcy i parametrów połączenia. Kod używa <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metody <xref:System.Data.Common.DbProviderFactory> do utworzenia <xref:System.Data.Common.DbConnection>. Następnie kod używa <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> metody do <xref:System.Data.Common.DbCommand> tworzenia `CommandText` i wybierania danych przez ustawienie właściwości i `Connection` . Na koniec kod tworzy <xref:System.Data.Common.DbDataAdapter> obiekt <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> przy użyciu metody i ustawia jego `SelectCommand` właściwość. `Fill` Metoda`DbDataAdapter`ładowaniadanych do .<xref:System.Data.DataTable>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Modyfikowanie danych za pomocą obiektu DbDataAdapter  
 W `DataTable` tym przykładzie pokazano, jak modyfikować dane przy użyciu a <xref:System.Data.Common.DbDataAdapter> za pomocą programu <xref:System.Data.Common.DbCommandBuilder> , aby generować polecenia wymagane do aktualizowania danych w źródle danych. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> JestustawionynapobieraniewartościCustomerIDi`DbDataAdapter` NazwaFirmy z tabeli Customers. <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> Metoda jest używana do ustawiania właściwości, metoda jest używana do ustawiania właściwości, a metoda jest używana do ustawiania <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> właściwości. <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> Kod dodaje nowy wiersz do tabeli Customers i aktualizuje źródło danych. Kod następnie lokalizuje dodany wiersz, wyszukując identyfikator IDKlienta, który jest kluczem podstawowym zdefiniowanym dla tabeli Customers. Zmienia on NazwaFirmy i aktualizuje źródło danych. Na koniec kod usuwa wiersz.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Obsługa parametrów  
 Dostawcy danych .NET Framework obsługują nazewnictwo i Określanie parametrów i symboli zastępczych parametrów w różny sposób. Ta składnia jest dostosowana do określonego źródła danych, zgodnie z opisem w poniższej tabeli.  
  
|Dostawca danych|Składnia nazewnictwa parametrów|  
|-------------------|-----------------------------|  
|`SqlClient`|Używa nazwanych parametrów w formacie `@` *ParameterName*.|  
|`OracleClient`|Używa nazwanych parametrów w formacie `:` *parmname* (lub *parmname*).|  
|`OleDb`|Używa znaczników parametrów pozycyjnych wskazanych przez znak zapytania (`?`).|  
|`Odbc`|Używa znaczników parametrów pozycyjnych wskazanych przez znak zapytania (`?`).|  
  
 Model fabryki nie ułatwia tworzenia sparametryzowanych `DbCommand` i `DbDataAdapter` obiektów. Musisz rozgałęzić w kodzie, aby utworzyć parametry, które są dostosowane do dostawcy danych.  
  
> [!IMPORTANT]
> Unikanie parametrów specyficznych dla dostawcy całkowicie przy użyciu łączenia ciągów do konstruowania bezpośrednich instrukcji SQL nie jest zalecane ze względów bezpieczeństwa. Używanie łączenia ciągów zamiast parametrów pozostawia aplikację narażoną na ataki z iniekcją SQL.  
  
## <a name="see-also"></a>Zobacz także

- [DbProviderFactories](dbproviderfactories.md)
- [Uzyskiwanie DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand i DbException](dbconnection-dbcommand-and-dbexception.md)
- [Omówienie ADO.NET](ado-net-overview.md)
