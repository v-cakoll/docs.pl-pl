---
title: Parametry połączenia w ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 02fe8d984f1287673477bb142b3f9626e248898e
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363748"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="78bf2-102">Parametry połączenia w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="78bf2-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="78bf2-103">Parametry połączenia zawierają informacje inicjujące, które są przesyłane jako parametr z dostawcy danych do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="78bf2-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="78bf2-104">Dostawca danych odbiera parametry połączenia jako wartość <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="78bf2-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="78bf2-105">Dostawca analizuje parametry połączenia i sprawdza, czy składnia jest poprawna i czy słowa kluczowe są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="78bf2-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="78bf2-106"><xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> Następnie metoda przekazuje przeanalizowane parametry połączenia do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="78bf2-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="78bf2-107">Źródło danych wykonuje dalsze walidacje i nawiązuje połączenie.</span><span class="sxs-lookup"><span data-stu-id="78bf2-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="78bf2-108">Składnia parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="78bf2-108">Connection string syntax</span></span>

<span data-ttu-id="78bf2-109">Parametry połączenia to rozdzielana średnikami lista par parametrów klucz/wartość:</span><span class="sxs-lookup"><span data-stu-id="78bf2-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```
keyword1=value; keyword2=value;
```

<span data-ttu-id="78bf2-110">W słowach kluczowych nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="78bf2-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="78bf2-111">Jednak w zależności od źródła danych w wartościach może być rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="78bf2-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="78bf2-112">Oba słowa kluczowe i wartości mogą zawierać [znaki odstępu](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="78bf2-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="78bf2-113">Odstępy wiodące i końcowe są ignorowane w słowach kluczowych i w wartościach bez cudzysłowów.</span><span class="sxs-lookup"><span data-stu-id="78bf2-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="78bf2-114">Jeśli wartość zawiera średnika, [znaki kontrolne Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)lub wiodące lub końcowe biały znak, musi być ujęta w znaki pojedynczego lub podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="78bf2-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="78bf2-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="78bf2-115">For example:</span></span>

```
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="78bf2-116">Otaczający znak może nie występować w wartości, którą on należy.</span><span class="sxs-lookup"><span data-stu-id="78bf2-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="78bf2-117">W związku z tym, wartość zawierająca znaki pojedynczego cudzysłowu może być ujęta tylko w znaki podwójnego cudzysłowu i odwrotnie:</span><span class="sxs-lookup"><span data-stu-id="78bf2-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="78bf2-118">Możesz również wprowadzić znak ucieczki, używając dwóch z nich jednocześnie:</span><span class="sxs-lookup"><span data-stu-id="78bf2-118">You can also escape the enclosing character by using two of them together:</span></span>

```
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="78bf2-119">Cudzysłowy, a także znak równości, nie wymagają ucieczki, dlatego następujące parametry połączenia są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="78bf2-119">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="78bf2-120">Ponieważ każda wartość jest odczytana do następnego średnika lub końca ciągu, wartość w tym ostatnim przykładzie to `a=b=c`, a ostatni średnik jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="78bf2-120">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="78bf2-121">Wszystkie parametry połączenia mają tę samą składnię podstawową opisaną powyżej.</span><span class="sxs-lookup"><span data-stu-id="78bf2-121">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="78bf2-122">Zestaw rozpoznanych słów kluczowych zależy od dostawcy, ale został rozmieszczony w latach od wcześniejszych interfejsów API, takich jak *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="78bf2-122">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="78bf2-123">Dostawca danych *.NET Framework* dla *SQL Server* (`SqlClient`) obsługuje wiele słów kluczowych ze starszych interfejsów API, ale zazwyczaj bardziej elastycznie i akceptuje synonimy dla wielu wspólnych słów kluczowych parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="78bf2-123">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="78bf2-124">Wpisywanie błędów może spowodować błędy.</span><span class="sxs-lookup"><span data-stu-id="78bf2-124">Typing mistakes can cause errors.</span></span> <span data-ttu-id="78bf2-125">Na przykład, `Integrated Security=true` jest prawidłowy, ale `IntegratedSecurity=true` powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="78bf2-125">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="78bf2-126">Parametry połączenia tworzone ręcznie w czasie wykonywania z niezweryfikowanych danych wejściowych użytkownika są narażone na ataki przez iniekcję ciągów i zagrażają bezpieczeństwu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="78bf2-126">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="78bf2-127">Aby rozwiązać te problemy, w *ADO.NET* 2,0 wprowadzono [konstruktory parametrów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md) dla każdego dostawcy danych *.NET Framework* .</span><span class="sxs-lookup"><span data-stu-id="78bf2-127">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](../../../../docs/framework/data/adonet/connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="78bf2-128">Te konstruktory parametrów połączenia uwidaczniają parametry jako właściwości o jednoznacznie określonym typie i umożliwiają sprawdzanie poprawności parametrów połączenia przed ich wysłaniem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="78bf2-128">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="78bf2-129">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="78bf2-129">In This Section</span></span>

<span data-ttu-id="78bf2-130">[Konstruktory parametrów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="78bf2-130">[Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md)</span></span>\
<span data-ttu-id="78bf2-131">Pokazuje, `ConnectionStringBuilder` w jaki sposób używać klas do konstruowania prawidłowych parametrów połączenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="78bf2-131">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="78bf2-132">[Parametry połączenia i pliki konfiguracji](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="78bf2-132">[Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="78bf2-133">Pokazuje, jak przechowywać i pobierać parametry połączenia w plikach konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="78bf2-133">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="78bf2-134">[Składnia parametrów połączenia](../../../../docs/framework/data/adonet/connection-string-syntax.md)</span><span class="sxs-lookup"><span data-stu-id="78bf2-134">[Connection String Syntax](../../../../docs/framework/data/adonet/connection-string-syntax.md)</span></span>\
<span data-ttu-id="78bf2-135">Opisuje sposób konfigurowania parametrów połączenia specyficznych dla dostawcy dla `SqlClient` `OleDb`, `OracleClient`, i `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="78bf2-135">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="78bf2-136">[Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="78bf2-136">[Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md)</span></span>\
<span data-ttu-id="78bf2-137">Demonstruje techniki ochrony informacji używanych do nawiązywania połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="78bf2-137">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="78bf2-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78bf2-138">See also</span></span>

- [<span data-ttu-id="78bf2-139">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="78bf2-139">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="78bf2-140">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="78bf2-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
