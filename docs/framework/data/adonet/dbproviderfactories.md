---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: e3ea9e3d083314f8df25f9edadbd1a18f1227293
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784100"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="7bb4a-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="7bb4a-102">DbProviderFactories</span></span>
<span data-ttu-id="7bb4a-103">Przestrzeń nazw zawiera klasy służące <xref:System.Data.Common.DbProviderFactory> do tworzenia wystąpień do pracy z określonymi źródłami danych. <xref:System.Data.Common></span><span class="sxs-lookup"><span data-stu-id="7bb4a-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="7bb4a-104">Po utworzeniu <xref:System.Data.Common.DbProviderFactory> wystąpienia i przejściu do niego informacji o dostawcy `DbProviderFactory` danych można określić poprawny obiekt połączenia o jednoznacznie określonym typie, który ma zostać zwrócony na podstawie dostarczonych informacji.</span><span class="sxs-lookup"><span data-stu-id="7bb4a-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="7bb4a-105">Począwszy od .NET Framework w wersji 4, dostawcy danych, takie <xref:System.Data.Odbc>jak <xref:System.Data.OleDb> <xref:System.Data.SqlClient>,, i <xref:System.Data.OracleClient> nie są już wymienione w pliku Machine. config, ale Dostawcy niestandardowi nadal będą wyświetlani w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="7bb4a-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7bb4a-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7bb4a-106">In This Section</span></span>  
 [<span data-ttu-id="7bb4a-107">Omówienie modelu fabryki</span><span class="sxs-lookup"><span data-stu-id="7bb4a-107">Factory Model Overview</span></span>](factory-model-overview.md)  
 <span data-ttu-id="7bb4a-108">Zawiera omówienie wzorca projektowego i interfejsu programowania.</span><span class="sxs-lookup"><span data-stu-id="7bb4a-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="7bb4a-109">Uzyskiwanie DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="7bb4a-109">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="7bb4a-110">Pokazuje, jak wyświetlić listę zainstalowanych dostawców danych i utworzyć <xref:System.Data.Common.DbConnection> `DbProviderFactory`z programu.</span><span class="sxs-lookup"><span data-stu-id="7bb4a-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="7bb4a-111">DbConnection, DbCommand i DbException</span><span class="sxs-lookup"><span data-stu-id="7bb4a-111">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="7bb4a-112">Pokazuje, jak utworzyć <xref:System.Data.Common.DbCommand> i <xref:System.Data.Common.DbDataReader>i jak obsługiwać błędy danych przy użyciu programu <xref:System.Data.Common.DbException>.</span><span class="sxs-lookup"><span data-stu-id="7bb4a-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="7bb4a-113">Modyfikowanie danych za pomocą obiektu DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="7bb4a-113">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="7bb4a-114">Pokazuje, w jaki sposób <xref:System.Data.Common.DbCommandBuilder> używać elementu <xref:System.Data.Common.DbDataAdapter> with a, aby pobierać i modyfikować dane.</span><span class="sxs-lookup"><span data-stu-id="7bb4a-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb4a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bb4a-115">See also</span></span>

- [<span data-ttu-id="7bb4a-116">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7bb4a-116">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="7bb4a-117">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7bb4a-117">ADO.NET Overview</span></span>](ado-net-overview.md)
