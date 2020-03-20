---
title: Konstruktorzy parametrów połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 8cadeac0bcbf301f7d973e93435885de82052603
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151666"
---
# <a name="connection-string-builders"></a><span data-ttu-id="e0963-102">Konstruktorzy parametrów połączeń</span><span class="sxs-lookup"><span data-stu-id="e0963-102">Connection String Builders</span></span>
<span data-ttu-id="e0963-103">We wcześniejszych wersjach ADO.NET nie wystąpiło sprawdzanie w czasie kompilacji ciągów połączeń z wartościami ciągu łączonego, <xref:System.ArgumentException>dzięki czemu w czasie wykonywania niepoprawne słowo kluczowe wygenerowało plik .</span><span class="sxs-lookup"><span data-stu-id="e0963-103">In earlier versions of ADO.NET, compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="e0963-104">Każdy z dostawców danych programu .NET Framework obsługiwane różne składni dla słów kluczowych ciągu połączenia, co utrudniło konstruowanie prawidłowych ciągów połączeń, jeśli odbywa się ręcznie.</span><span class="sxs-lookup"><span data-stu-id="e0963-104">Each of the .NET Framework data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="e0963-105">Aby rozwiązać ten problem, ADO.NET 2.0 wprowadziła nowe konstruktory ciągów połączeń dla każdego dostawcy danych programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0963-105">To address this problem, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="e0963-106">Każdy dostawca danych zawiera silnie typizowana klasę konstruktora ciągów połączeń, która dziedziczy po <xref:System.Data.Common.DbConnectionStringBuilder>programie .</span><span class="sxs-lookup"><span data-stu-id="e0963-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="e0963-107">W poniższej tabeli wymieniono dostawców danych platformy .NET Framework i skojarzone z nimi klasy konstruktora ciągów połączeń.</span><span class="sxs-lookup"><span data-stu-id="e0963-107">The following table lists the .NET Framework data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="e0963-108">Dostawca</span><span class="sxs-lookup"><span data-stu-id="e0963-108">Provider</span></span>|<span data-ttu-id="e0963-109">ConnectionStringBuilder, klasa</span><span class="sxs-lookup"><span data-stu-id="e0963-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="e0963-110">Ataki iniekcji ciągu połączenia</span><span class="sxs-lookup"><span data-stu-id="e0963-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="e0963-111">Atak iniekcji ciągu połączenia może wystąpić, gdy dynamiczne łączenie ciągów jest używane do tworzenia ciągów połączeń, które są oparte na danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e0963-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="e0963-112">Jeśli ciąg nie zostanie zweryfikowany, a złośliwy tekst lub znaki nie zostaną zmienione, osoba atakująca może potencjalnie uzyskać dostęp do poufnych danych lub innych zasobów na serwerze.</span><span class="sxs-lookup"><span data-stu-id="e0963-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="e0963-113">Na przykład osoba atakująca może zamontować atak, podając średnik i dołączając dodatkową wartość.</span><span class="sxs-lookup"><span data-stu-id="e0963-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="e0963-114">Parametry połączenia są analizowane przy użyciu algorytmu "ostatni wygrywa", a wrogie dane wejściowe są zastępowane wartością uzasadnioną.</span><span class="sxs-lookup"><span data-stu-id="e0963-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="e0963-115">Klasy konstruktora ciągów połączeń mają na celu wyeliminowanie zgadywania i ochronę przed błędami składni i lukami w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="e0963-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="e0963-116">Zapewniają one metody i właściwości odpowiadające znanym parom klucz/wartość dozwolonym przez każdego dostawcę danych.</span><span class="sxs-lookup"><span data-stu-id="e0963-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="e0963-117">Każda klasa utrzymuje stałą kolekcję synonimów i może tłumaczyć z synonimu na odpowiednią dobrze znaną nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="e0963-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="e0963-118">Sprawdza są wykonywane dla prawidłowych par klucz/wartość i nieprawidłowa para zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e0963-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="e0963-119">Ponadto wartości wstrzyknięte są obsługiwane w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="e0963-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="e0963-120">W poniższym przykładzie <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pokazano, jak obsługuje wstawioną dodatkową wartość dla `Initial Catalog` ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e0963-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 <span data-ttu-id="e0963-121">Dane wyjściowe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pokazuje, że obsługiwane to poprawnie, uciekając od dodatkowej wartości w cudzysłowie podwójne zamiast dołączania go do ciągu połączenia jako nowa para klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="e0963-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="e0963-122">Tworzenie ciągów połączeń z plików konfiguracyjnych</span><span class="sxs-lookup"><span data-stu-id="e0963-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="e0963-123">Jeśli niektóre elementy ciągu połączenia są znane wcześniej, mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania, aby utworzyć pełny ciąg połączenia.</span><span class="sxs-lookup"><span data-stu-id="e0963-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="e0963-124">Na przykład nazwa bazy danych może być znana z wyprzedzeniem, ale nie nazwa serwera.</span><span class="sxs-lookup"><span data-stu-id="e0963-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="e0963-125">Możesz też chcieć, aby użytkownik podał nazwę i hasło w czasie wykonywania bez możliwości wstrzyknąć inne wartości do ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e0963-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="e0963-126">Jeden z przeciążonych konstruktorów dla konstruktora ciągów połączeń przyjmuje <xref:System.String> jako argument, który umożliwia dostarczenie częściowego ciągu połączenia, który następnie można ukończyć z danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e0963-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="e0963-127">Ciąg połączenia częściowego mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e0963-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0963-128">Obszar <xref:System.Configuration> nazw umożliwia programowy dostęp do <xref:System.Web.Configuration.WebConfigurationManager> plików konfiguracyjnych, które używają aplikacji sieci Web i aplikacji <xref:System.Configuration.ConfigurationManager> dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e0963-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="e0963-129">Aby uzyskać więcej informacji na temat pracy z ciągami połączeń i plikami konfiguracyjnymi, zobacz [Parametry połączenia i pliki konfiguracyjne](connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="e0963-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="e0963-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0963-130">Example</span></span>  
 <span data-ttu-id="e0963-131">W tym przykładzie pokazano pobieranie częściowego ciągu połączenia z pliku <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>konfiguracyjnego i wypełnianie go przez ustawienie programu , i <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> właściwości <xref:System.Data.SqlClient.SqlConnectionStringBuilder>pliku .</span><span class="sxs-lookup"><span data-stu-id="e0963-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="e0963-132">Plik konfiguracyjny jest zdefiniowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e0963-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> <span data-ttu-id="e0963-133">Należy ustawić odwołanie do `System.Configuration.dll` w projekcie, aby kod do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="e0963-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e0963-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0963-134">See also</span></span>

- [<span data-ttu-id="e0963-135">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="e0963-135">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="e0963-136">Bezpieczeństwo danych i poufności informacji</span><span class="sxs-lookup"><span data-stu-id="e0963-136">Privacy and Data Security</span></span>](privacy-and-data-security.md)
- [<span data-ttu-id="e0963-137">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e0963-137">ADO.NET Overview</span></span>](ado-net-overview.md)
