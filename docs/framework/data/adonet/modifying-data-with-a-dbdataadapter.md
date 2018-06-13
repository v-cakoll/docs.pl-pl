---
title: Modyfikowanie danych za pomocą obiekt DbDataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: 851c724d354b0e819ca320c32e98249f2ec66506
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765844"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Modyfikowanie danych za pomocą obiekt DbDataAdapter
<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> Metody <xref:System.Data.Common.DbProviderFactory> obiektu umożliwia <xref:System.Data.Common.DbDataAdapter> obiekt, który jest silnie typizowaną do podstawowego dostawcy danych określony w momencie utworzyć fabryki. Następnie można użyć <xref:System.Data.Common.DbCommandBuilder> do tworzenia poleceń do wstawiania, aktualizowania i usuwania danych z <xref:System.Data.DataSet> ze źródłem danych.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Pobieranie danych z obiekt DbDataAdapter  
 W tym przykładzie pokazano, jak utworzyć silnie typizowaną `DbDataAdapter` na podstawie ciągu połączenia i nazwę dostawcy. W kodzie użyto <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metody <xref:System.Data.Common.DbProviderFactory> do utworzenia <xref:System.Data.Common.DbConnection>. Następnie w kodzie użyto <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> metodę w celu utworzenia <xref:System.Data.Common.DbCommand> aby wybrać dane przez ustawienie jej `CommandText` i `Connection` właściwości. Na koniec kod tworzy <xref:System.Data.Common.DbDataAdapter> przy użyciu <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> — metoda i ustawia jej `SelectCommand` właściwości. `Fill` Metody `DbDataAdapter` wczytuje dane do <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Modyfikowanie danych za pomocą obiekt DbDataAdapter  
 W tym przykładzie pokazano, jak modyfikować danych w `DataTable` przy użyciu <xref:System.Data.Common.DbDataAdapter> przy użyciu <xref:System.Data.Common.DbCommandBuilder> do generowania poleceń wymaganych do aktualizacji danych w źródle danych. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> z `DbDataAdapter` ustawiono pobieranie CustomerID i NazwaFirmy z tabeli Klienci. <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> Metoda jest używana do ustawiania <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> właściwości, <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> metoda jest używana do ustawiania <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> właściwości oraz <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> metoda jest używana do ustawiania <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> właściwości. Ten kod dodaje nowy wiersz do tabeli Klienci i aktualizuje źródła danych. Następnie kod klient zlokalizuje wiersz, wyszukując CustomerID, która jest kluczem podstawowym zdefiniowane dla tabeli klientów. Zmienia CompanyName, a aktualizacje źródła danych. Na koniec kod usuwa wiersz.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Parametry obsługi  
 Dostawcy danych .NET Framework obsługi nazywania i określanie parametrów i symbole zastępcze parametru inaczej. Ta składnia jest dostosowane do określonego źródła danych, zgodnie z opisem w poniższej tabeli.  
  
|Dostawca danych|Składnia nazwy parametru|  
|-------------------|-----------------------------|  
|`SqlClient`|Używa nazwanych parametrów w formacie `@` *parametername*.|  
|`OracleClient`|Używa nazwanych parametrów w formacie `:` *parmname* (lub *parmname*).|  
|`OleDb`|Używa wskaźników parametrów pozycyjnych wskazywanym przez znak zapytania (`?`).|  
|`Odbc`|Używa wskaźników parametrów pozycyjnych wskazywanym przez znak zapytania (`?`).|  
  
 Fabryka nie jest pomocne przy tworzeniu sparametryzowane `DbCommand` i `DbDataAdapter` obiektów. Konieczne będzie gałęzi w kodzie, aby utworzyć parametry, które są dostosowane do dostawcy danych.  
  
> [!IMPORTANT]
>  Unikanie parametrów specyficznych dla dostawcy całkowicie przy użyciu ciągów do konstruowania bezpośredniego instrukcji SQL nie jest zalecane ze względów bezpieczeństwa. Za pomocą ciągów zamiast parametrów pozostawia aplikacji narażony na ataki.  
  
## <a name="see-also"></a>Zobacz też  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Uzyskiwanie DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand i DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
