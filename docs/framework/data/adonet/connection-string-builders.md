---
title: Konstruktorzy parametrów połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 17ef057fccbea48da698e0ecfa5c789e125adbb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034544"
---
# <a name="connection-string-builders"></a><span data-ttu-id="d1183-102">Konstruktorzy parametrów połączeń</span><span class="sxs-lookup"><span data-stu-id="d1183-102">Connection String Builders</span></span>
<span data-ttu-id="d1183-103">We wcześniejszych wersjach programu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], w czasie kompilacji sprawdzania tak, aby w czasie wykonywania, generowany jest niepoprawna — słowo kluczowe parametrów połączenia parametrami połączonych wartości nie były wykonywane, <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="d1183-103">In earlier versions of [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="d1183-104">Każdy z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] danych obsługiwani różnej składni dla słowa kluczowe parametrów połączenia, które wprowadzone konstruowanie ciągi prawidłowe połączenie jest trudne, jeśli jest wykonywane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="d1183-104">Each of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="d1183-105">Aby rozwiązać ten problem, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 wprowadzono nowe Konstruktorzy parametrów połączeń dla każdego [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych.</span><span class="sxs-lookup"><span data-stu-id="d1183-105">To address this problem, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 introduced new connection string builders for each [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="d1183-106">Każdy dostawca danych obejmuje połączenia silnie typizowane parametry konstruktora klasy dziedziczącej z klasy <xref:System.Data.Common.DbConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="d1183-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="d1183-107">W poniższej tabeli wymieniono [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych i ich skojarzone z nimi połączenie ciąg konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="d1183-107">The following table lists the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="d1183-108">Dostawca</span><span class="sxs-lookup"><span data-stu-id="d1183-108">Provider</span></span>|<span data-ttu-id="d1183-109">Klasa ConnectionStringBuilder</span><span class="sxs-lookup"><span data-stu-id="d1183-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="d1183-110">Ataki polegające na iniekcji ciąg połączenia</span><span class="sxs-lookup"><span data-stu-id="d1183-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="d1183-111">Ataku polegającego na iniekcji ciąg połączenia może wystąpić, gdy dynamiczne ciągów jest używany do tworzenia parametrów połączenia, które są oparte na danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d1183-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="d1183-112">Jeśli ciąg nie jest tekst zweryfikowane i złośliwych lub znaków, nie zawiera wyjścia, osoba atakująca może potencjalnie uzyskać dostęp do poufnych danych lub innych zasobów na serwerze.</span><span class="sxs-lookup"><span data-stu-id="d1183-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="d1183-113">Na przykład osoba atakująca może zainstalować ataku przez dostarczenie średnika i dołączanie dodatkowych wartości.</span><span class="sxs-lookup"><span data-stu-id="d1183-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="d1183-114">Ciąg połączenia jest analizowany przy użyciu algorytmu "wins ostatnim miejscu", a szkodliwy danych wejściowych zostanie zastąpiony wartością uzasadnione.</span><span class="sxs-lookup"><span data-stu-id="d1183-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="d1183-115">Konstruktor klasy ciąg połączenia są przeznaczone do wyeliminowania wątpliwości i ochrony przed błędy składniowe i luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="d1183-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="d1183-116">Zapewniają one, metody i właściwości odpowiadający pary znanych klucz/wartość, w dozwolonym przez każdego dostawcy danych.</span><span class="sxs-lookup"><span data-stu-id="d1183-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="d1183-117">Każda klasa przechowuje stałej kolekcji synonimów i może dokonywać translacji z synonimem do odpowiedniego dobrze znaną nazwą klucza.</span><span class="sxs-lookup"><span data-stu-id="d1183-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="d1183-118">Testy są wykonywane dla pary klucz/wartość prawidłowy, i zgłasza wyjątek, parę nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d1183-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="d1183-119">Ponadto wprowadzonego wartości są obsługiwane w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="d1183-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="d1183-120">W poniższym przykładzie pokazano sposób, w jaki <xref:System.Data.SqlClient.SqlConnectionStringBuilder> obsługuje wstawiono wartość dodatkowego `Initial Catalog` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="d1183-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
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
  
 <span data-ttu-id="d1183-121">Dane wyjściowe pokazują, że <xref:System.Data.SqlClient.SqlConnectionStringBuilder> poprawnej obsługi to przez zmianę znaczenia wartości dodatkowej w podwójnym cudzysłowie zamiast dołączenie jej do połączenia jako nową parę klucz wartość.</span><span class="sxs-lookup"><span data-stu-id="d1183-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="d1183-122">Tworzenie parametrów połączenia z plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d1183-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="d1183-123">Jeśli wcześniej wiadomo, niektóre elementy ciągu połączenia, mogą być przechowywane w pliku konfiguracji i pobierane w czasie wykonywania do konstruowania pełne parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="d1183-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="d1183-124">Na przykład nazwą bazy danych może być znane z wyprzedzeniem, ale nie nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="d1183-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="d1183-125">Można też użytkownika o podanie nazwy i hasła w czasie wykonywania bez możliwości wprowadzić inne wartości do parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="d1183-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="d1183-126">Jedno z przeciążenia konstruktorów dla konstruktora parametrów połączenia wykorzystuje <xref:System.String> jako argument, co umożliwia podać ciąg połączenia częściowe, który można wykonać z danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d1183-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="d1183-127">Parametry połączenia częściowe można przechowywane w pliku konfiguracji i pobierane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d1183-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1183-128"><xref:System.Configuration> Przestrzeń nazw umożliwia programowy dostęp do plików konfiguracyjnych, które używają <xref:System.Web.Configuration.WebConfigurationManager> dla aplikacji sieci Web i <xref:System.Configuration.ConfigurationManager> dla aplikacji Windows.</span><span class="sxs-lookup"><span data-stu-id="d1183-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="d1183-129">Aby uzyskać więcej informacji na temat pracy z parametrów połączenia i pliki konfiguracji, zobacz [parametry połączenia i pliki konfiguracyjne](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="d1183-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="d1183-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1183-130">Example</span></span>  
 <span data-ttu-id="d1183-131">W tym przykładzie przedstawiono pobieranie parametrów połączenia częściowe z pliku konfiguracji i jego ukończenia, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, i <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> właściwości <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="d1183-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="d1183-132">Plik konfiguracji jest zdefiniowana w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d1183-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="d1183-133">Należy ustawić odwołanie `System.Configuration.dll` w projekcie kodu do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="d1183-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d1183-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1183-134">See also</span></span>

- [<span data-ttu-id="d1183-135">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="d1183-135">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="d1183-136">Bezpieczeństwo danych i poufności informacji</span><span class="sxs-lookup"><span data-stu-id="d1183-136">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)
- [<span data-ttu-id="d1183-137">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d1183-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
