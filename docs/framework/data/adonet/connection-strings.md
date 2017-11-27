---
title: "Parametry połączenia w ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bd787373b869c31727cfc0d027b6b98774b0d630
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="b7eed-102">Parametry połączenia w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7eed-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="b7eed-103">.NET Framework 2.0 wprowadzono nowe funkcje do pracy z parametrów połączenia, w tym wprowadzenia nowych słów kluczowych do klasy konstruktora ciąg połączenia, które ułatwiają tworzenie prawidłowe połączenie ciągów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b7eed-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
 <span data-ttu-id="b7eed-104">Parametry połączenia zawierają informacje inicjowania jest przekazywana jako parametr z dostawcy danych do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b7eed-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="b7eed-105">Składnia jest zależna od dostawcy danych, a podczas próby otwarcia połączenia jest przeanalizować parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="b7eed-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="b7eed-106">Błędy składniowe wygenerować wyjątek czasu wykonywania, ale inne błędy występują tylko wtedy, gdy źródło danych otrzymuje informacje o połączeniu.</span><span class="sxs-lookup"><span data-stu-id="b7eed-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="b7eed-107">Po sprawdzeniu poprawności źródła danych dotyczy opcje określone w parametrach połączenia i otwarcie połączenia.</span><span class="sxs-lookup"><span data-stu-id="b7eed-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>  
  
 <span data-ttu-id="b7eed-108">Format ciągu połączenia jest rozdzielaną średnikami listę par klucz/wartość parametru:</span><span class="sxs-lookup"><span data-stu-id="b7eed-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>  
  
 `keyword1=value; keyword2=value;`  
  
 <span data-ttu-id="b7eed-109">Słowa kluczowe nie jest uwzględniana wielkość liter i spacji między pary klucz wartość są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="b7eed-109">Keywords are not case sensitive, and spaces between key/value pairs are ignored.</span></span> <span data-ttu-id="b7eed-110">Jednak wartości może być uwzględniana wielkość liter, w zależności od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b7eed-110">However, values may be case sensitive, depending on the data source.</span></span> <span data-ttu-id="b7eed-111">Wszelkie wartości zawierające średnika, pojedynczy cudzysłów lub podwójny cudzysłów musi być ujęta w znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="b7eed-111">Any values containing a semicolon, single quotation marks, or double quotation marks must be enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="b7eed-112">Składnia ciągu połączenia prawidłowy zależy od dostawcy i powstał całościowo wcześniejszych interfejsy API, takich jak ODBC.</span><span class="sxs-lookup"><span data-stu-id="b7eed-112">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="b7eed-113">.NET Framework Data Provider for SQL Server (SqlClient) zawiera wiele elementów z starsze składnię i jest zazwyczaj bardziej elastyczne z typowych składnia ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b7eed-113">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="b7eed-114">Są często jednakowo prawidłowe synonimy dla elementów składnia ciągu połączenia, ale niektóre składni i błędów pisowni mogą powodować problemy.</span><span class="sxs-lookup"><span data-stu-id="b7eed-114">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="b7eed-115">Na przykład "`Integrated Security=true`" jest nieprawidłowa, podczas gdy "`IntegratedSecurity=true`" powoduje, że wystąpił błąd.</span><span class="sxs-lookup"><span data-stu-id="b7eed-115">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="b7eed-116">Ponadto parametry połączenia zbudowane w czasie wykonywania na podstawie danych wejściowych użytkownika niezweryfikowanych może prowadzić do ataków iniekcji ciągu, zagrażające zabezpieczeń w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="b7eed-116">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>  
  
 <span data-ttu-id="b7eed-117">Aby rozwiązać te problemy, ADO.NET 2.0 wprowadzono nowe konstruktorów ciągu połączenia dla każdego dostawcy danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7eed-117">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="b7eed-118">Słowa kluczowe są widoczne jako właściwości włączenie składnia ciągu połączenia do sprawdzenia poprawności przed przesłaniem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b7eed-118">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7eed-119">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b7eed-119">In This Section</span></span>  
 [<span data-ttu-id="b7eed-120">Konstruktorzy ciągów połączenia</span><span class="sxs-lookup"><span data-stu-id="b7eed-120">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="b7eed-121">Pokazuje, jak używać `ConnectionStringBuilder` klasy, aby utworzyć prawidłowe połączenie ciągi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b7eed-121">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>  
  
 [<span data-ttu-id="b7eed-122">Parametry połączenia i pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b7eed-122">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="b7eed-123">Przedstawiono sposób przechowywania i pobierania parametrów połączenia w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b7eed-123">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>  
  
 [<span data-ttu-id="b7eed-124">Składnia ciągu połączenia</span><span class="sxs-lookup"><span data-stu-id="b7eed-124">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="b7eed-125">Opisuje sposób konfigurowania parametrów połączeń specyficznych dla dostawcy dla `SqlClient`, `OracleClient`, `OleDb`, i `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="b7eed-125">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>  
  
 [<span data-ttu-id="b7eed-126">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="b7eed-126">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="b7eed-127">Prezentuje techniki chroniące informacje używane do połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="b7eed-127">Demonstrates techniques for protecting information used to connect to a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7eed-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7eed-128">See Also</span></span>  
 [<span data-ttu-id="b7eed-129">Połączenie ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="b7eed-129">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="b7eed-130">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b7eed-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
