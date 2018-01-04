---
title: Wykonywanie polecenia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 43fb2d8e42aeae5340874ab082f33257b197eac3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="executing-a-command"></a><span data-ttu-id="d2178-102">Wykonywanie polecenia</span><span class="sxs-lookup"><span data-stu-id="d2178-102">Executing a Command</span></span>
<span data-ttu-id="d2178-103">Każdy dostawca danych programu .NET Framework uwzględnionych w programie .NET Framework ma własną obiektu polecenia, która dziedziczy <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="d2178-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="d2178-104">.NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbCommand> obiekt dostawcy danych programu .NET Framework dla programu SQL Server zawiera <xref:System.Data.SqlClient.SqlCommand> obiekt dostawcy danych programu .NET Framework dla ODBC obejmuje <xref:System.Data.Odbc.OdbcCommand> obiektu i .NET Framework Dostawca danych dla Oracle zawiera <xref:System.Data.OracleClient.OracleCommand> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d2178-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="d2178-105">Każdy z tych obiektów udostępnia metody wykonywania poleceń na podstawie typu polecenia i żądaną wartość zwracaną, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d2178-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="d2178-106">Polecenie</span><span class="sxs-lookup"><span data-stu-id="d2178-106">Command</span></span>|<span data-ttu-id="d2178-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d2178-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="d2178-108">Zwraca `DataReader` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d2178-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="d2178-109">Zwraca pojedynczą wartość skalarną.</span><span class="sxs-lookup"><span data-stu-id="d2178-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="d2178-110">Wykonuje polecenia, która nie zwraca żadnych wierszy.</span><span class="sxs-lookup"><span data-stu-id="d2178-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="d2178-111">Zwraca <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d2178-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d2178-112">Dostępne dla `SqlCommand` tylko obiekt.</span><span class="sxs-lookup"><span data-stu-id="d2178-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="d2178-113">Każdy obiekt polecenia jednoznacznie obsługuje również <xref:System.Data.CommandType> wyliczenie określający, jak ciąg polecenia jest interpretowany, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d2178-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="d2178-114">Obiekt CommandType</span><span class="sxs-lookup"><span data-stu-id="d2178-114">CommandType</span></span>|<span data-ttu-id="d2178-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d2178-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="d2178-116">Polecenie SQL definiujący instrukcje mają być wykonane w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="d2178-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="d2178-117">Nazwa procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="d2178-117">The name of the stored procedure.</span></span> <span data-ttu-id="d2178-118">Można użyć `Parameters` właściwości polecenia dostępu do parametrów wejściowych i wyjściowych i wartości zwracane, niezależnie od tego, który `Execute` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d2178-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="d2178-119">Korzystając z `ExecuteReader`, ani zwracać wartości i parametry wyjściowe nie są dostępne do `DataReader` jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="d2178-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="d2178-120">Nazwa tabeli.</span><span class="sxs-lookup"><span data-stu-id="d2178-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d2178-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2178-121">Example</span></span>  
 <span data-ttu-id="d2178-122">Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Data.SqlClient.SqlCommand> obiekt, aby wykonać procedurę składowaną przez ustawienie jej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2178-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="d2178-123">A <xref:System.Data.SqlClient.SqlParameter> obiekt jest używany do określenia parametru wejściowego procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="d2178-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="d2178-124">Polecenie zostanie wykonane przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> — metoda i dane wyjściowe z <xref:System.Data.SqlClient.SqlDataReader> jest wyświetlany w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="d2178-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="d2178-125">Rozwiązywanie problemów z poleceń</span><span class="sxs-lookup"><span data-stu-id="d2178-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="d2178-126">.NET Framework Data Provider for SQL Server dodaje liczniki wydajności, które umożliwiają wykrywanie sporadyczne problemy związane z wykonania polecenia nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d2178-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="d2178-127">Aby uzyskać więcej informacji, zobacz [liczniki wydajności](../../../../docs/framework/data/adonet/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="d2178-127">For more information see [Performance Counters](../../../../docs/framework/data/adonet/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2178-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2178-128">See Also</span></span>  
 [<span data-ttu-id="d2178-129">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="d2178-129">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="d2178-130">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="d2178-130">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="d2178-131">Praca z DataReaders</span><span class="sxs-lookup"><span data-stu-id="d2178-131">Working with DataReaders</span></span>](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="d2178-132">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="d2178-132">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
