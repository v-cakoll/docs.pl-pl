---
title: DbProviderFactories
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e8c6310b8ce164a60541dae030ce603bccd372e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="dbproviderfactories"></a><span data-ttu-id="26fcb-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="26fcb-102">DbProviderFactories</span></span>
<span data-ttu-id="26fcb-103"><xref:System.Data.Common> Przestrzeń nazw zawiera klasy do tworzenia <xref:System.Data.Common.DbProviderFactory> wystąpień do pracy z konkretnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="26fcb-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="26fcb-104">Po utworzeniu <xref:System.Data.Common.DbProviderFactory> wystąpienia i przekaż go informacji na temat dostawcy danych `DbProviderFactory` można określić obiektu połączenia poprawny, silnie typizowaną do zwrócenia na podstawie informacji ma zostać podana.</span><span class="sxs-lookup"><span data-stu-id="26fcb-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="26fcb-105">W programie .NET Framework w wersji 4, dostawców danych, takich jak <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, i <xref:System.Data.OracleClient> nie są wymienione w pliku machine.config, ale niestandardowych dostawców będą nadal wyświetlane istnieje.</span><span class="sxs-lookup"><span data-stu-id="26fcb-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26fcb-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="26fcb-106">In This Section</span></span>  
 [<span data-ttu-id="26fcb-107">Omówienie modelu fabryki</span><span class="sxs-lookup"><span data-stu-id="26fcb-107">Factory Model Overview</span></span>](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 <span data-ttu-id="26fcb-108">Zawiera omówienie fabryki wzorca projektowego i interfejs programowania.</span><span class="sxs-lookup"><span data-stu-id="26fcb-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="26fcb-109">Uzyskiwanie DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="26fcb-109">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="26fcb-110">Pokazuje, jak listy dostawców zainstalowane dane i tworzyć <xref:System.Data.Common.DbConnection> z `DbProviderFactory`.</span><span class="sxs-lookup"><span data-stu-id="26fcb-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="26fcb-111">Obiektu DbConnection, polecenie DbCommand i dbexception —</span><span class="sxs-lookup"><span data-stu-id="26fcb-111">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="26fcb-112">Przedstawia sposób tworzenia <xref:System.Data.Common.DbCommand> i <xref:System.Data.Common.DbDataReader>oraz sposób obsługi błędów danych przy użyciu <xref:System.Data.Common.DbException>.</span><span class="sxs-lookup"><span data-stu-id="26fcb-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="26fcb-113">Modyfikowanie danych za pomocą obiekt DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="26fcb-113">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="26fcb-114">Pokazuje, jak używać <xref:System.Data.Common.DbCommandBuilder> z <xref:System.Data.Common.DbDataAdapter> do pobrania i modyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="26fcb-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26fcb-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26fcb-115">See Also</span></span>  
 [<span data-ttu-id="26fcb-116">Trwa pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="26fcb-116">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="26fcb-117">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="26fcb-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
