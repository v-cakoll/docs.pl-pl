---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 2376cf39228cb5e8208112333ba06bb80070de84
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208818"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="80824-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="80824-102">DbProviderFactories</span></span>
<span data-ttu-id="80824-103"><xref:System.Data.Common> Nazw zawiera klasy do tworzenia <xref:System.Data.Common.DbProviderFactory> wystąpień do pracy z konkretnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="80824-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="80824-104">Po utworzeniu <xref:System.Data.Common.DbProviderFactory> wystąpienia i przekazać go informacje o dostawcy danych `DbProviderFactory` można określić obiekt połączenia poprawny, silnie typizowaną do zwrócenia na podstawie informacji został dostarczony.</span><span class="sxs-lookup"><span data-stu-id="80824-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="80824-105">Począwszy od programu .NET Framework w wersji 4, dostawców danych takich jak <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, i <xref:System.Data.OracleClient> już nie są wymienione w pliku machine.config, ale niestandardowego dostawcy będą nadal będą wyświetlane istnieje.</span><span class="sxs-lookup"><span data-stu-id="80824-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80824-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="80824-106">In This Section</span></span>  
 [<span data-ttu-id="80824-107">Omówienie modelu fabryki</span><span class="sxs-lookup"><span data-stu-id="80824-107">Factory Model Overview</span></span>](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 <span data-ttu-id="80824-108">Zawiera omówienie wzorca projektowego fabryki i interfejs programowania.</span><span class="sxs-lookup"><span data-stu-id="80824-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="80824-109">Uzyskiwanie DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="80824-109">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="80824-110">Pokazuje, jak listy dostawcy danych zainstalowanego i tworzenia <xref:System.Data.Common.DbConnection> z `DbProviderFactory`.</span><span class="sxs-lookup"><span data-stu-id="80824-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="80824-111">DbConnection, DbCommand i DbException</span><span class="sxs-lookup"><span data-stu-id="80824-111">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="80824-112">Przedstawia sposób tworzenia <xref:System.Data.Common.DbCommand> i <xref:System.Data.Common.DbDataReader>i sposób obsługi błędów danych przy użyciu <xref:System.Data.Common.DbException>.</span><span class="sxs-lookup"><span data-stu-id="80824-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="80824-113">Modyfikowanie danych za pomocą obiektu DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="80824-113">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="80824-114">Pokazuje sposób użycia <xref:System.Data.Common.DbCommandBuilder> z <xref:System.Data.Common.DbDataAdapter> do pobrania i modyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="80824-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80824-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80824-115">See also</span></span>

- [<span data-ttu-id="80824-116">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="80824-116">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="80824-117">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="80824-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
