---
title: Konstruktorzy parametrów połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: e1f8d636e793b2d8b984fe1aa0b823fa58a4981d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040181"
---
# <a name="connection-string-builders"></a><span data-ttu-id="39c42-102">Konstruktorzy parametrów połączeń</span><span class="sxs-lookup"><span data-stu-id="39c42-102">Connection String Builders</span></span>
<span data-ttu-id="39c42-103">We wcześniejszych wersjach programu ADO.NET sprawdzanie czasu kompilacji parametrów połączenia z połączonymi wartościami ciągu nie zakończyło się, więc w czasie wykonywania nieprawidłowe słowo kluczowe wygenerowało <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="39c42-103">In earlier versions of ADO.NET, compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="39c42-104">Każdy dostawca danych .NET Framework obsługuje inną składnię dla słów kluczowych parametrów połączenia, która sprawia, że prawidłowe parametry połączenia są trudne, jeśli zostały wykonane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="39c42-104">Each of the .NET Framework data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="39c42-105">Aby rozwiązać ten problem, ADO.NET 2,0 wprowadził nowe konstruktory parametrów połączenia dla każdego dostawcy danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39c42-105">To address this problem, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="39c42-106">Każdy dostawca danych zawiera klasę konstruktora parametrów połączenia o jednoznacznie określonym typie, która dziedziczy po <xref:System.Data.Common.DbConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="39c42-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="39c42-107">Poniższa tabela zawiera listę dostawców danych .NET Framework i skojarzonych z nimi klas konstruktorów parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="39c42-107">The following table lists the .NET Framework data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="39c42-108">Dostawcy</span><span class="sxs-lookup"><span data-stu-id="39c42-108">Provider</span></span>|<span data-ttu-id="39c42-109">Klasa ConnectionStringBuilder</span><span class="sxs-lookup"><span data-stu-id="39c42-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="39c42-110">Ataki przed iniekcją parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="39c42-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="39c42-111">Atak polegający na iniekcji parametrów połączenia może wystąpić, gdy dynamiczne łączenie ciągów służy do tworzenia parametrów połączenia opartych na danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="39c42-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="39c42-112">Jeśli ciąg nie zostanie sprawdzony i złośliwy tekst lub znaki nie zostały zmienione, osoba atakująca może uzyskać dostęp do poufnych danych lub innych zasobów na serwerze.</span><span class="sxs-lookup"><span data-stu-id="39c42-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="39c42-113">Na przykład osoba atakująca może zainstalować atak, dostarczając średnik i dołączając dodatkową wartość.</span><span class="sxs-lookup"><span data-stu-id="39c42-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="39c42-114">Parametry połączenia są analizowane przy użyciu algorytmu "ostatni jeden WINS", a dane wejściowe nieszkodliwy jest zastępowany dla wiarygodnej wartości.</span><span class="sxs-lookup"><span data-stu-id="39c42-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="39c42-115">Klasy konstruktora parametrów połączenia zostały zaprojektowane w celu wyeliminowania wątpliwości i ochrony przed błędami składni i lukami w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="39c42-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="39c42-116">Udostępniają one metody i właściwości odpowiadające znanym par klucz/wartość dozwolonym przez każdego dostawcę danych.</span><span class="sxs-lookup"><span data-stu-id="39c42-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="39c42-117">Każda klasa przechowuje stałe kolekcje synonimów i może przetłumaczyć ze synonimu na odpowiadającą mu dobrze znaną nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="39c42-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="39c42-118">Testy są wykonywane dla prawidłowych par klucz/wartość i nieprawidłowa para zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="39c42-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="39c42-119">Ponadto wartości wstrzykiwane są obsługiwane w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="39c42-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="39c42-120">Poniższy przykład ilustruje, jak <xref:System.Data.SqlClient.SqlConnectionStringBuilder> obsługuje wstawioną dodatkową wartość dla ustawienia `Initial Catalog`.</span><span class="sxs-lookup"><span data-stu-id="39c42-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
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
  
 <span data-ttu-id="39c42-121">Dane wyjściowe pokazują, że <xref:System.Data.SqlClient.SqlConnectionStringBuilder> prawidłowo obsłużył to przez anulowanie dodatkowej wartości w podwójnym cudzysłowie zamiast dołączania do parametrów połączenia jako nowej pary klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="39c42-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="39c42-122">Kompilowanie parametrów połączenia z plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="39c42-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="39c42-123">Jeśli niektóre elementy parametrów połączenia są znane wcześniej, mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania w celu skonstruowania kompletnych parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="39c42-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="39c42-124">Na przykład nazwa bazy danych może być znana z wyprzedzeniem, ale nie z nazwą serwera.</span><span class="sxs-lookup"><span data-stu-id="39c42-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="39c42-125">Może też być konieczne podanie przez użytkownika nazwy i hasła w czasie wykonywania bez możliwości wprowadzania innych wartości do parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="39c42-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="39c42-126">Jeden z przeciążonych konstruktorów dla konstruktora parametrów połączenia przyjmuje <xref:System.String> jako argument, dzięki czemu można podawać częściowe parametry połączenia, które następnie można wykonać przy użyciu danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="39c42-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="39c42-127">Częściowe parametry połączenia mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="39c42-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39c42-128">Przestrzeń nazw <xref:System.Configuration> umożliwia programistyczny dostęp do plików konfiguracji, które używają <xref:System.Web.Configuration.WebConfigurationManager> dla aplikacji sieci Web i <xref:System.Configuration.ConfigurationManager> aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="39c42-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="39c42-129">Aby uzyskać więcej informacji na temat pracy z parametrami połączenia i plikami konfiguracji, zobacz [parametry połączeń i pliki konfiguracji](connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="39c42-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="39c42-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="39c42-130">Example</span></span>  
 <span data-ttu-id="39c42-131">W tym przykładzie pokazano, jak pobrać częściowe parametry połączenia z pliku konfiguracji i zakończyć je przez ustawienie właściwości <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>i <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="39c42-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="39c42-132">Plik konfiguracji jest definiowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="39c42-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> <span data-ttu-id="39c42-133">Należy ustawić odwołanie do `System.Configuration.dll` w projekcie, aby kod mógł zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="39c42-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="39c42-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39c42-134">See also</span></span>

- [<span data-ttu-id="39c42-135">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="39c42-135">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="39c42-136">Bezpieczeństwo danych i poufności informacji</span><span class="sxs-lookup"><span data-stu-id="39c42-136">Privacy and Data Security</span></span>](privacy-and-data-security.md)
- [<span data-ttu-id="39c42-137">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="39c42-137">ADO.NET Overview</span></span>](ado-net-overview.md)
