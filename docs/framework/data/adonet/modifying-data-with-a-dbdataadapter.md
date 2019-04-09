---
title: Modyfikowanie danych za pomocą obiektu DbDataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: 3038e35947cd8f97266d374a367a77380df440dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158876"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Modyfikowanie danych za pomocą obiektu DbDataAdapter
<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> Metody <xref:System.Data.Common.DbProviderFactory> zapewnia obiekt <xref:System.Data.Common.DbDataAdapter> obiekt, który jest silnie typizowaną do podstawowego dostawcy danych określony w momencie tworzenia fabryka. Następnie można użyć <xref:System.Data.Common.DbCommandBuilder> do tworzenia poleceń do wstawiania, aktualizowania i usuwania danych z <xref:System.Data.DataSet> ze źródłem danych.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Trwa pobieranie danych z DbDataAdapter  
 Ten przykład przedstawia sposób tworzenia silnie typizowaną `DbDataAdapter` na podstawie parametrów połączenia i nazwę dostawcy. Kod używa <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metody <xref:System.Data.Common.DbProviderFactory> utworzyć <xref:System.Data.Common.DbConnection>. Następnie kod używa <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> metodę w celu utworzenia <xref:System.Data.Common.DbCommand> aby wybrać dane, ustawiając jego `CommandText` i `Connection` właściwości. Na koniec kod tworzy <xref:System.Data.Common.DbDataAdapter> przy użyciu <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> metody i ustawia jego `SelectCommand` właściwości. `Fill` Metody `DbDataAdapter` służy do ładowania danych do <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Modyfikowanie danych za pomocą obiektu DbDataAdapter  
 W tym przykładzie pokazano, jak modyfikowanie danych w `DataTable` przy użyciu <xref:System.Data.Common.DbDataAdapter> przy użyciu <xref:System.Data.Common.DbCommandBuilder> można wygenerować polecenia wymagane do aktualizowania danych w źródle danych. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> z `DbDataAdapter` jest ustawiona na pobieranie CustomerID i CompanyName z tabeli Customers. <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> Metoda jest używana do ustawiania <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> właściwości <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> metoda jest używana do ustawiania <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> właściwości i <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> metoda jest używana do ustawiania <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> właściwości. Ten kod dodaje nowy wiersz do tabeli Klienci i aktualizuje źródło danych. Kod następnie lokalizuje dodano wiersza, wyszukując CustomerID, która jest kluczem podstawowym zdefiniowane dla tabeli Customers. Zmienia CompanyName i aktualizuje źródło danych. Na koniec kod usuwa wiersz.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Parametry obsługi  
 Dostawcy danych .NET Framework obsługują nazewnictwa i określanie parametrów i symbole zastępcze parametr inaczej. Ta składnia dostosowane do określonego źródła danych, zgodnie z opisem w poniższej tabeli.  
  
|Dostawca danych|Składnia nazwy parametru|  
|-------------------|-----------------------------|  
|`SqlClient`|Korzysta z nazwanych parametrów w formacie `@` *parametername*.|  
|`OracleClient`|Korzysta z nazwanych parametrów w formacie `:` *parmname* (lub *parmname*).|  
|`OleDb`|Używa wskaźników parametr pozycyjne wskazywanym przez znak zapytania (`?`).|  
|`Odbc`|Używa wskaźników parametr pozycyjne wskazywanym przez znak zapytania (`?`).|  
  
 Model fabryki nie jest pomocne przy tworzeniu sparametryzowane `DbCommand` i `DbDataAdapter` obiektów. Konieczne będzie gałęzi w kodzie, aby utworzyć parametry, które są dostosowane do dostawcy danych.  
  
> [!IMPORTANT]
>  Unikanie parametrów właściwe dla dostawcy całkowicie za pomocą ciągów do konstruowania bezpośrednie instrukcji SQL nie jest zalecane ze względów bezpieczeństwa. Za pomocą ciągów zamiast parametrów pozostawia aplikacji podatny na ataki przez wstrzyknięcie kodu SQL.  
  
## <a name="see-also"></a>Zobacz także

- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [Uzyskiwanie DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand i DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
