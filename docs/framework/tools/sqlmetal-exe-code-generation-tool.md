---
title: SqlMetal.exe (Narzędzie generowania kodu)
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: f435c93f68feb564aaca0f52842e567aa688ac64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938007"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="bc01b-102">SqlMetal.exe (Narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="bc01b-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="bc01b-103">Narzędzie wiersza polecenia SQLMetal generuje kod i mapowanie dla [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] składnika .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc01b-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="bc01b-104">Stosując opisane w dalszej części tego tematu opcje, można za pomocą programu SqlMetal wykonać kilka różnych akcji, takich jak:</span><span class="sxs-lookup"><span data-stu-id="bc01b-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="bc01b-105">Na podstawie bazy danych — generowanie kodu źródłowego i atrybutów mapowania lub pliku mapowania.</span><span class="sxs-lookup"><span data-stu-id="bc01b-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="bc01b-106">Na podstawie bazy danych — generowanie pliku języka Intermediate Database Markup Language (dbml) na potrzeby dostosowywania.</span><span class="sxs-lookup"><span data-stu-id="bc01b-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="bc01b-107">Na podstawie pliku dbml — generowanie kodu i atrybutów mapowania lub pliku mapowania.</span><span class="sxs-lookup"><span data-stu-id="bc01b-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="bc01b-108">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc01b-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="bc01b-109">Domyślnie plik znajduje się w `drive`folderze: \Program Files\Microsoft SDKs\Windows\v \Bin.`n.nn`</span><span class="sxs-lookup"><span data-stu-id="bc01b-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="bc01b-110">Jeśli program Visual Studio nie zostanie zainstalowany, można również pobrać plik SQLMetal, pobierając [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="bc01b-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc01b-111">Deweloperzy, którzy korzystają z programu Visual Studio, mogą również generować klasy jednostek przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="bc01b-111">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="bc01b-112">Podejście z użyciem wiersza polecenia dobrze sprawdza się w przypadku dużych baz danych.</span><span class="sxs-lookup"><span data-stu-id="bc01b-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="bc01b-113">Program SqlMetal to narzędzie wiersza polecenia, więc można użyć go w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bc01b-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="bc01b-114">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="bc01b-114">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="bc01b-115">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md). W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="bc01b-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc01b-116">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc01b-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="bc01b-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="bc01b-117">Options</span></span>  
 <span data-ttu-id="bc01b-118">Aby wyświetlić najbardziej aktualną listę opcji, wpisz `sqlmetal /?` w wierszu polecenia z zainstalowanej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="bc01b-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="bc01b-119">**Opcje połączenia**</span><span class="sxs-lookup"><span data-stu-id="bc01b-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="bc01b-120">Opcja</span><span class="sxs-lookup"><span data-stu-id="bc01b-120">Option</span></span>|<span data-ttu-id="bc01b-121">Opis</span><span class="sxs-lookup"><span data-stu-id="bc01b-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bc01b-122">**/Server:**  *>\<nazwy*</span><span class="sxs-lookup"><span data-stu-id="bc01b-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="bc01b-123">Określa nazwę serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bc01b-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="bc01b-124">**/Database:**  *>\<nazwy*</span><span class="sxs-lookup"><span data-stu-id="bc01b-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="bc01b-125">Określa wykaz baz danych na serwerze.</span><span class="sxs-lookup"><span data-stu-id="bc01b-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="bc01b-126">**/User:**  *>\<nazwy*</span><span class="sxs-lookup"><span data-stu-id="bc01b-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="bc01b-127">Określa identyfikator logowania użytkownika. Wartość domyślna: Użyj uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bc01b-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="bc01b-128">**/Password:**  *>\<hasła*</span><span class="sxs-lookup"><span data-stu-id="bc01b-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="bc01b-129">Określa hasło logowania.</span><span class="sxs-lookup"><span data-stu-id="bc01b-129">Specifies logon password.</span></span> <span data-ttu-id="bc01b-130">Wartość domyślna: Użyj uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bc01b-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="bc01b-131">**/Conn:**  *>parametrów\<połączenia*</span><span class="sxs-lookup"><span data-stu-id="bc01b-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="bc01b-132">Określa parametry połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="bc01b-132">Specifies database connection string.</span></span> <span data-ttu-id="bc01b-133">Nie można używać z opcjami **/Server**, **/Database**, **/User**i **/Password** .</span><span class="sxs-lookup"><span data-stu-id="bc01b-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="bc01b-134">W parametrach połączenia nie można umieszczać nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="bc01b-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="bc01b-135">Zamiast tego należy określić nazwę pliku w wierszu polecenia jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="bc01b-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="bc01b-136">Na przykład poniższy wiersz określa "c:\northwnd.mdf" jako plik wejściowy: **SQLMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\northwnd.mdf"** .</span><span class="sxs-lookup"><span data-stu-id="bc01b-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="bc01b-137">**/timeout:**  *>\<sekund*</span><span class="sxs-lookup"><span data-stu-id="bc01b-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="bc01b-138">Określa wartość limitu czasu używaną, gdy program SqlMetal uzyskuje dostęp do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bc01b-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="bc01b-139">Wartość domyślna: 0 (to nie jest limit czasu).</span><span class="sxs-lookup"><span data-stu-id="bc01b-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="bc01b-140">**Opcje wyodrębniania**</span><span class="sxs-lookup"><span data-stu-id="bc01b-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="bc01b-141">Opcja</span><span class="sxs-lookup"><span data-stu-id="bc01b-141">Option</span></span>|<span data-ttu-id="bc01b-142">Opis</span><span class="sxs-lookup"><span data-stu-id="bc01b-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bc01b-143">**/views**</span><span class="sxs-lookup"><span data-stu-id="bc01b-143">**/views**</span></span>|<span data-ttu-id="bc01b-144">Wyodrębnia widoki bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bc01b-144">Extracts database views.</span></span>|  
|<span data-ttu-id="bc01b-145">**/functions**</span><span class="sxs-lookup"><span data-stu-id="bc01b-145">**/functions**</span></span>|<span data-ttu-id="bc01b-146">Wyodrębnia funkcje bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bc01b-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="bc01b-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="bc01b-147">**/sprocs**</span></span>|<span data-ttu-id="bc01b-148">Wyodrębnia procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="bc01b-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="bc01b-149">**Opcje wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="bc01b-149">**Output options**</span></span>  
  
|<span data-ttu-id="bc01b-150">Opcja</span><span class="sxs-lookup"><span data-stu-id="bc01b-150">Option</span></span>|<span data-ttu-id="bc01b-151">Opis</span><span class="sxs-lookup"><span data-stu-id="bc01b-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bc01b-152">**/DBML** *[: plik]*</span><span class="sxs-lookup"><span data-stu-id="bc01b-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="bc01b-153">Wysyła dane wyjściowe w postaci pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="bc01b-153">Sends output as .dbml.</span></span> <span data-ttu-id="bc01b-154">Nie można używać z opcją **/map** .</span><span class="sxs-lookup"><span data-stu-id="bc01b-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="bc01b-155">**/Code** *[: plik]*</span><span class="sxs-lookup"><span data-stu-id="bc01b-155">**/code** *[:file]*</span></span>|<span data-ttu-id="bc01b-156">Wysyła dane wyjściowe w postaci kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="bc01b-156">Sends output as source code.</span></span> <span data-ttu-id="bc01b-157">Nie można używać z opcją **/DBML** .</span><span class="sxs-lookup"><span data-stu-id="bc01b-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="bc01b-158">**/map** *[: plik]*</span><span class="sxs-lookup"><span data-stu-id="bc01b-158">**/map** *[:file]*</span></span>|<span data-ttu-id="bc01b-159">Generuje plik mapowania XML zamiast atrybutów.</span><span class="sxs-lookup"><span data-stu-id="bc01b-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="bc01b-160">Nie można używać z opcją **/DBML** .</span><span class="sxs-lookup"><span data-stu-id="bc01b-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="bc01b-161">**Różne**</span><span class="sxs-lookup"><span data-stu-id="bc01b-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="bc01b-162">Opcja</span><span class="sxs-lookup"><span data-stu-id="bc01b-162">Option</span></span>|<span data-ttu-id="bc01b-163">Opis</span><span class="sxs-lookup"><span data-stu-id="bc01b-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bc01b-164">**/Language:**  *>\<języka*</span><span class="sxs-lookup"><span data-stu-id="bc01b-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="bc01b-165">Określa język kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="bc01b-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="bc01b-166">*Prawidłowy\<język >* : VB, CSharp.</span><span class="sxs-lookup"><span data-stu-id="bc01b-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="bc01b-167">Wartość domyślna: Pochodny od rozszerzenia nazwy pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="bc01b-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="bc01b-168">**/Namespace:**  *>\<nazwy*</span><span class="sxs-lookup"><span data-stu-id="bc01b-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="bc01b-169">Określa przestrzeń nazw wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="bc01b-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="bc01b-170">Wartość domyślna: brak przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bc01b-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="bc01b-171">**/Context:**  *Typ\<>*</span><span class="sxs-lookup"><span data-stu-id="bc01b-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="bc01b-172">Określa nazwę klasy kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="bc01b-172">Specifies name of data context class.</span></span> <span data-ttu-id="bc01b-173">Wartość domyślna: Pochodny od nazwy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bc01b-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="bc01b-174">**/entitybase:**  *Typ\<>*</span><span class="sxs-lookup"><span data-stu-id="bc01b-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="bc01b-175">Określa klasę bazową klas obiektów w generowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bc01b-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="bc01b-176">Wartość domyślna: Jednostki nie mają klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="bc01b-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="bc01b-177">**/Pluralize**</span><span class="sxs-lookup"><span data-stu-id="bc01b-177">**/pluralize**</span></span>|<span data-ttu-id="bc01b-178">Automatycznie zmienia nazwy klas i składowych na liczbę mnogą lub pojedynczą.</span><span class="sxs-lookup"><span data-stu-id="bc01b-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="bc01b-179">Ta opcja jest dostępna tylko w Stanach Zjednoczonych Wersja w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="bc01b-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="bc01b-180">**/Serialization:**  *opcja\<>*</span><span class="sxs-lookup"><span data-stu-id="bc01b-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="bc01b-181">Generuje klasy, które można serializować.</span><span class="sxs-lookup"><span data-stu-id="bc01b-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="bc01b-182">*Prawidłowe\<> opcji*: Brak, jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="bc01b-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="bc01b-183">Wartość domyślna: Brak.</span><span class="sxs-lookup"><span data-stu-id="bc01b-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="bc01b-184">Aby uzyskać więcej informacji, zobacz [serializacji](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="bc01b-184">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="bc01b-185">**Plik wejściowy**</span><span class="sxs-lookup"><span data-stu-id="bc01b-185">**Input File**</span></span>  
  
|<span data-ttu-id="bc01b-186">Opcja</span><span class="sxs-lookup"><span data-stu-id="bc01b-186">Option</span></span>|<span data-ttu-id="bc01b-187">Opis</span><span class="sxs-lookup"><span data-stu-id="bc01b-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bc01b-188">**\<plik wejściowy >**</span><span class="sxs-lookup"><span data-stu-id="bc01b-188">**\<input file>**</span></span>|<span data-ttu-id="bc01b-189">Określa plik. mdf SQL Server Express, plik SQL Server Compact 3,5. sdf lub plik pośredni. dbml.</span><span class="sxs-lookup"><span data-stu-id="bc01b-189">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc01b-190">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc01b-190">Remarks</span></span>  
 <span data-ttu-id="bc01b-191">Działanie programu SqlMetal w rzeczywistości obejmuje wykonanie dwóch kroków:</span><span class="sxs-lookup"><span data-stu-id="bc01b-191">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="bc01b-192">Wyodrębnienie metadanych bazy danych do pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="bc01b-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="bc01b-193">Wygenerowanie pliku wyjściowego z kodem.</span><span class="sxs-lookup"><span data-stu-id="bc01b-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="bc01b-194">Korzystając z odpowiednich opcji wiersza polecenia, można utworzyć Visual Basic lub C# kod źródłowy lub utworzyć plik mapowania XML.</span><span class="sxs-lookup"><span data-stu-id="bc01b-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="bc01b-195">Aby wyodrębnić metadane z pliku mdf, należy określić nazwę pliku mdf po wszystkich innych opcjach.</span><span class="sxs-lookup"><span data-stu-id="bc01b-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="bc01b-196">Jeśli **/Server** nie jest określony, zakłada się **localhost/SQLExpress** .</span><span class="sxs-lookup"><span data-stu-id="bc01b-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="bc01b-197">Microsoft SQL Server 2005 zgłasza wyjątek, jeśli spełnione są co najmniej jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="bc01b-197">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="bc01b-198">Program SqlMetal próbuje wyodrębnić procedurę składowaną, którą sam wywołuje.</span><span class="sxs-lookup"><span data-stu-id="bc01b-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="bc01b-199">Poziom zagnieżdżenia procedury składowanej, funkcji lub widoku przekracza 32.</span><span class="sxs-lookup"><span data-stu-id="bc01b-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="bc01b-200">Program SqlMetal przechwytuje ten wyjątek i zgłasza go jako ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="bc01b-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="bc01b-201">Aby określić nazwę pliku wejściowego, należy dodać ją do wiersza polecenia jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="bc01b-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="bc01b-202">Dołączenie nazwy pliku w parametrach połączenia (przy użyciu opcji **/Conn** ) nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bc01b-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bc01b-203">Przykłady</span><span class="sxs-lookup"><span data-stu-id="bc01b-203">Examples</span></span>  
 <span data-ttu-id="bc01b-204">Generuje plik dbml zawierający wyodrębnione metadane SQL:</span><span class="sxs-lookup"><span data-stu-id="bc01b-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="bc01b-205">**SQLMetal/Server:/Database o identyfikatorze northwind/dbml: meta. dbml**</span><span class="sxs-lookup"><span data-stu-id="bc01b-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="bc01b-206">Generuje plik dbml zawierający metadane SQL wyodrębnione z pliku mdf przy użyciu programu SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="bc01b-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="bc01b-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="bc01b-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="bc01b-208">Generuje plik dbml zawierający metadane SQL wyodrębnione z programu SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="bc01b-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="bc01b-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="bc01b-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="bc01b-210">Generuje kod źródłowy na podstawie pliku metadanych dbml:</span><span class="sxs-lookup"><span data-stu-id="bc01b-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="bc01b-211">**SQLMetal/Namespace: NWIND/Code: NWIND. cs/Language: CSharp. dbml**</span><span class="sxs-lookup"><span data-stu-id="bc01b-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="bc01b-212">Generuje kod źródłowy bezpośrednio na podstawie metadanych SQL:</span><span class="sxs-lookup"><span data-stu-id="bc01b-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="bc01b-213">**SQLMetal/Server: KSW/Database: Northwind/Namespace: NWIND/Code: NWIND. cs/Language: CSharp**</span><span class="sxs-lookup"><span data-stu-id="bc01b-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc01b-214">W przypadku korzystania z opcji **/pluralize** z przykładową bazą danych Northwind należy zwrócić uwagę na następujące zachowanie.</span><span class="sxs-lookup"><span data-stu-id="bc01b-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="bc01b-215">Gdy program SqlMetal tworzy nazwy tabel typu wiersz, nazwy tabel mają liczbę pojedynczą.</span><span class="sxs-lookup"><span data-stu-id="bc01b-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="bc01b-216">Gdy udostępnia <xref:System.Data.Linq.DataContext> właściwości tabel, nazwy tabel są w liczbie mnogiej.</span><span class="sxs-lookup"><span data-stu-id="bc01b-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="bc01b-217">Przypadkowo nazwy tabel w przykładowej bazie danych Northwind mają już liczbę mnogą.</span><span class="sxs-lookup"><span data-stu-id="bc01b-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="bc01b-218">Dlatego też nie widać działania tej części opcji.</span><span class="sxs-lookup"><span data-stu-id="bc01b-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="bc01b-219">Popularną praktyką jest nadawanie tabelom w bazie danych nazw w liczbie pojedynczej, ale równie popularną praktyką na platformie .NET jest nadawanie kolekcjom nazw w liczbie mnogiej.</span><span class="sxs-lookup"><span data-stu-id="bc01b-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc01b-220">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc01b-220">See also</span></span>

- [<span data-ttu-id="bc01b-221">Instrukcje: Generuj model obiektów w Visual Basic lubC#</span><span class="sxs-lookup"><span data-stu-id="bc01b-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="bc01b-222">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bc01b-222">Code Generation in LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="bc01b-223">Mapowanie zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="bc01b-223">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
