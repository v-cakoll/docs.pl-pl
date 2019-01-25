---
title: Parametry połączenia w ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: c765eee661858499240344cb5059fe1fa9a58ab5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627567"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="98107-102">Parametry połączenia w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="98107-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="98107-103">Parametry połączenia zawierają informacje inicjowania, który jest przekazywany jako parametr od dostawcy danych do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="98107-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="98107-104">Dostawca danych otrzymuje parametry połączenia jako wartość <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="98107-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="98107-105">Dostawca analizuje ciąg połączenia i zapewnia, że składnia jest poprawna i że słowa kluczowe są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="98107-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="98107-106">A następnie <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> metoda przekazuje parametry przeanalizowany połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="98107-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="98107-107">Źródło danych dalsze przeprowadza weryfikację i nawiąże połączenie.</span><span class="sxs-lookup"><span data-stu-id="98107-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="98107-108">Składnia ciągu połączenia</span><span class="sxs-lookup"><span data-stu-id="98107-108">Connection string syntax</span></span>

<span data-ttu-id="98107-109">Ciąg połączenia jest rozdzielaną średnikami listę par klucz/wartość do parametru:</span><span class="sxs-lookup"><span data-stu-id="98107-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>
  
    keyword1=value; keyword2=value;
  
<span data-ttu-id="98107-110">Słowa kluczowe nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="98107-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="98107-111">Jednakże, wartości, może być uwzględniana jest wielkość liter, w zależności od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="98107-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="98107-112">Słowa kluczowe i wartości mogą zawierać [białych znaków](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="98107-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="98107-113">Początkowe i końcowe biały jest ignorowany słów kluczowych i nienotowane wartości.</span><span class="sxs-lookup"><span data-stu-id="98107-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="98107-114">Jeśli wartość zawiera średnika, [znaków kontrolnych Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters), lub wiodące lub końcowe biały znak, muszą być ujęte w pojedyncze lub podwójne znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="98107-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="98107-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="98107-115">For example:</span></span>

    Keyword=" whitespace  ";
    Keyword='special;character';

<span data-ttu-id="98107-116">Znak otaczającej nie wystąpi w wartość, która je otacza.</span><span class="sxs-lookup"><span data-stu-id="98107-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="98107-117">Wartość zawierającą znaki pojedynczego cudzysłowu mogą być ujęte w związku z tym, tylko w znaki cudzysłowu i na odwrót:</span><span class="sxs-lookup"><span data-stu-id="98107-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

<span data-ttu-id="98107-118">Znaki cudzysłowu, same, jak również równości, nie wymagają anulowania zapewnianego element, aby poniższe parametry połączenia są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="98107-118">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

<span data-ttu-id="98107-119">Ponieważ każda wartość jest do odczytu do następnego średnika lub końca ciągu, wartości w drugim przykładzie jest `a=b=c`, i końcowy średnik jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="98107-119">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="98107-120">Wszystkie ciągi połączenia współużytkować tę samą składnię podstawowe opisanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="98107-120">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="98107-121">Zbiór rozpoznane słowa kluczowe, jest zależna od dostawcy i został przekształcony w ciągu lat, za pomocą starszych interfejsów API, takich jak *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="98107-121">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="98107-122">*.NET Framework* dostawca danych dla *programu SQL Server* (`SqlClient`) obsługuje wiele słów kluczowych z interfejsów API starszych, ale jest zazwyczaj bardziej elastyczne i akceptuje synonimy dla wielu typowych parametrów połączenia słowa kluczowe.</span><span class="sxs-lookup"><span data-stu-id="98107-122">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="98107-123">Błędów może spowodować błędy.</span><span class="sxs-lookup"><span data-stu-id="98107-123">Typing mistakes can cause errors.</span></span> <span data-ttu-id="98107-124">Na przykład `Integrated Security=true` jest prawidłowy, ale `IntegratedSecurity=true` powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="98107-124">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="98107-125">Parametry połączenia, tworzony ręcznie, w czasie wykonywania z danych wejściowych użytkownika niezweryfikowanych są narażone na ataki polegające na iniekcji ciągu i zagrozić zabezpieczeń w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="98107-125">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="98107-126">Aby rozwiązać te problemy *ADO.NET* 2.0 wprowadzono [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md) dla każdego *.NET Framework* dostawcy danych.</span><span class="sxs-lookup"><span data-stu-id="98107-126">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](../../../../docs/framework/data/adonet/connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="98107-127">Te Konstruktorzy parametrów połączeń ujawnić parametry jako silnie typizowane właściwości, dzięki czemu będzie można sprawdzić poprawność parametrów połączenia przed wysłaniem ich do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="98107-127">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="98107-128">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="98107-128">In This Section</span></span>  
 [<span data-ttu-id="98107-129">Konstruktorzy parametrów połączeń</span><span class="sxs-lookup"><span data-stu-id="98107-129">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="98107-130">Pokazuje sposób użycia `ConnectionStringBuilder` klas do utworzenia prawidłowego połączenia ciągów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="98107-130">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>
  
 [<span data-ttu-id="98107-131">Parametry połączenia i pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="98107-131">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="98107-132">Pokazuje, jak przechowywać i pobierać parametry połączenia w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="98107-132">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>
  
 [<span data-ttu-id="98107-133">Składnia parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="98107-133">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="98107-134">W tym artykule opisano jak skonfigurować parametry połączenia specyficzne dla dostawcy na potrzeby `SqlClient`, `OracleClient`, `OleDb`, i `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="98107-134">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>
  
 [<span data-ttu-id="98107-135">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="98107-135">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="98107-136">Pokazuje technik ochrony informacje używane do połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="98107-136">Demonstrates techniques for protecting information used to connect to a data source.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98107-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98107-137">See also</span></span>
- [<span data-ttu-id="98107-138">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="98107-138">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="98107-139">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="98107-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
