---
title: Parametry połączenia
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 3f56a487121757706ef6b4dfd11fcd761657431a
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202279"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="595f0-102">Parametry połączenia w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="595f0-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="595f0-103">Parametry połączenia zawierają informacje inicjujące, które są przesyłane jako parametr z dostawcy danych do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="595f0-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="595f0-104">Dostawca danych odbiera parametry połączenia jako wartość <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="595f0-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="595f0-105">Dostawca analizuje parametry połączenia i sprawdza, czy składnia jest poprawna i czy słowa kluczowe są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="595f0-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="595f0-106">Następnie <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> Metoda przekazuje przeanalizowane parametry połączenia do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="595f0-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="595f0-107">Źródło danych wykonuje dalsze walidacje i nawiązuje połączenie.</span><span class="sxs-lookup"><span data-stu-id="595f0-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="595f0-108">Składnia parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="595f0-108">Connection string syntax</span></span>

<span data-ttu-id="595f0-109">Parametry połączenia to rozdzielana średnikami lista par parametrów klucz/wartość:</span><span class="sxs-lookup"><span data-stu-id="595f0-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```csharp
keyword1=value; keyword2=value;
```

<span data-ttu-id="595f0-110">W słowach kluczowych nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="595f0-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="595f0-111">Jednak w zależności od źródła danych w wartościach może być rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="595f0-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="595f0-112">Oba słowa kluczowe i wartości mogą zawierać [znaki odstępu](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="595f0-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="595f0-113">Odstępy wiodące i końcowe są ignorowane w słowach kluczowych i w wartościach bez cudzysłowów.</span><span class="sxs-lookup"><span data-stu-id="595f0-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="595f0-114">Jeśli wartość zawiera średnika, [znaki kontrolne Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)lub wiodące lub końcowe biały znak, musi być ujęta w znaki pojedynczego lub podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="595f0-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="595f0-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="595f0-115">For example:</span></span>

```csharp
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="595f0-116">Otaczający znak może nie występować w wartości, którą on należy.</span><span class="sxs-lookup"><span data-stu-id="595f0-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="595f0-117">W związku z tym, wartość zawierająca znaki pojedynczego cudzysłowu może być ujęta tylko w znaki podwójnego cudzysłowu i odwrotnie:</span><span class="sxs-lookup"><span data-stu-id="595f0-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```csharp
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="595f0-118">Możesz również wprowadzić znak ucieczki, używając dwóch z nich jednocześnie:</span><span class="sxs-lookup"><span data-stu-id="595f0-118">You can also escape the enclosing character by using two of them together:</span></span>

```csharp
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="595f0-119">Cudzysłowy, a także znak równości, nie wymagają ucieczki, dlatego następujące parametry połączenia są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="595f0-119">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```csharp
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="595f0-120">Ponieważ każda wartość jest odczytana do następnego średnika lub końca ciągu, wartość w tym ostatnim przykładzie to `a=b=c` , a ostatni średnik jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="595f0-120">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="595f0-121">Wszystkie parametry połączenia mają tę samą składnię podstawową opisaną powyżej.</span><span class="sxs-lookup"><span data-stu-id="595f0-121">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="595f0-122">Zestaw rozpoznanych słów kluczowych zależy od dostawcy, ale został rozmieszczony w latach od wcześniejszych interfejsów API, takich jak *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="595f0-122">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="595f0-123">Dostawca danych *.NET Framework* dla *SQL Server* ( `SqlClient` ) obsługuje wiele słów kluczowych ze starszych interfejsów API, ale zazwyczaj bardziej elastycznie i akceptuje synonimy dla wielu wspólnych słów kluczowych parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="595f0-123">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="595f0-124">Wpisywanie błędów może spowodować błędy.</span><span class="sxs-lookup"><span data-stu-id="595f0-124">Typing mistakes can cause errors.</span></span> <span data-ttu-id="595f0-125">Na przykład, `Integrated Security=true` jest prawidłowy, ale `IntegratedSecurity=true` powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="595f0-125">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="595f0-126">Parametry połączenia tworzone ręcznie w czasie wykonywania z niezweryfikowanych danych wejściowych użytkownika są narażone na ataki przez iniekcję ciągów i zagrażają bezpieczeństwu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="595f0-126">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="595f0-127">Aby rozwiązać te problemy, w *ADO.NET* 2,0 wprowadzono [konstruktory parametrów połączenia](connection-string-builders.md) dla każdego dostawcy danych *.NET Framework* .</span><span class="sxs-lookup"><span data-stu-id="595f0-127">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="595f0-128">Te konstruktory parametrów połączenia uwidaczniają parametry jako właściwości silnie wpisane i umożliwiają sprawdzanie poprawności parametrów połączenia przed ich wysłaniem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="595f0-128">These connection string builders expose parameters as strongly typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="595f0-129">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="595f0-129">In This Section</span></span>

<span data-ttu-id="595f0-130">[Konstruktory parametrów połączenia](connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="595f0-130">[Connection String Builders](connection-string-builders.md)</span></span>\
<span data-ttu-id="595f0-131">Pokazuje, w jaki sposób używać `ConnectionStringBuilder` klas do konstruowania prawidłowych parametrów połączenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="595f0-131">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="595f0-132">[Parametry połączenia i pliki konfiguracji](connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="595f0-132">[Connection Strings and Configuration Files](connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="595f0-133">Pokazuje, jak przechowywać i pobierać parametry połączenia w plikach konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="595f0-133">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="595f0-134">[Składnia parametrów połączenia](connection-string-syntax.md)</span><span class="sxs-lookup"><span data-stu-id="595f0-134">[Connection String Syntax](connection-string-syntax.md)</span></span>\
<span data-ttu-id="595f0-135">Opisuje sposób konfigurowania parametrów połączenia specyficznych dla dostawcy dla `SqlClient` , `OracleClient` , `OleDb` i `Odbc` .</span><span class="sxs-lookup"><span data-stu-id="595f0-135">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="595f0-136">[Ochrona informacji o połączeniu](protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="595f0-136">[Protecting Connection Information](protecting-connection-information.md)</span></span>\
<span data-ttu-id="595f0-137">Demonstruje techniki ochrony informacji używanych do nawiązywania połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="595f0-137">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="595f0-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="595f0-138">See also</span></span>

- [<span data-ttu-id="595f0-139">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="595f0-139">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="595f0-140">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="595f0-140">ADO.NET Overview</span></span>](ado-net-overview.md)
