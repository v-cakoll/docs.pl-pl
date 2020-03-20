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
ms.openlocfilehash: d5b4c2b59b585b3d3a3584ef9055e70c9d998e85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71044078"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (Narzędzie generowania kodu)
Narzędzie wiersza polecenia SqlMetal generuje kod [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] i mapowanie dla składnika programu .NET Framework. Stosując opisane w dalszej części tego tematu opcje, można za pomocą programu SqlMetal wykonać kilka różnych akcji, takich jak:  
  
- Na podstawie bazy danych — generowanie kodu źródłowego i atrybutów mapowania lub pliku mapowania.  
  
- Na podstawie bazy danych — generowanie pliku języka Intermediate Database Markup Language (dbml) na potrzeby dostosowywania.  
  
- Na podstawie pliku dbml — generowanie kodu i atrybutów mapowania lub pliku mapowania.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Domyślnie plik znajduje się `drive`pod adresem :\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin. Jeśli program Visual Studio nie zostanie zainstalowany, można również pobrać plik SQLMetal, pobierając pakiet [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
> Deweloperzy korzystający z programu Visual Studio mogą również używać projektanta relacyjnego obiektu do generowania klas jednostek. Podejście z użyciem wiersza polecenia dobrze sprawdza się w przypadku dużych baz danych. Program SqlMetal to narzędzie wiersza polecenia, więc można użyć go w procesie kompilacji.  
  
 Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md). W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Opcje  
 Aby wyświetlić najbardziej aktualną `sqlmetal /?` listę opcji, wpisz w wierszu polecenia z zainstalowanej lokalizacji.  
  
 **Opcje połączenia**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/server:** * \<nazwa>*|Określa nazwę serwera bazy danych.|  
|**/database:** * \<nazwa>*|Określa wykaz baz danych na serwerze.|  
|**/user:** * \<nazwa>*|Określa identyfikator użytkownika logowania. Wartość domyślna: użyj uwierzytelniania systemu Windows.|  
|**/password:** * \<hasło>*|Określa hasło logowania. Wartość domyślna: Użyj uwierzytelniania systemu Windows.|  
|**/conn:** * \<>ciągu połączenia*|Określa parametry połączenia z bazą danych. Nie można używać z **opcjami /server**, **/database**, **/user**lub **/password.**<br /><br /> W parametrach połączenia nie można umieszczać nazwy pliku. Zamiast tego należy określić nazwę pliku w wierszu polecenia jako plik wejściowy. Na przykład następujący wiersz określa "c:\northwnd.mdf" jako plik wejściowy: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.|  
|**/timeout:** * \<sekundy>*|Określa wartość limitu czasu używaną, gdy program SqlMetal uzyskuje dostęp do bazy danych. Wartość domyślna: 0 (czyli brak limitu czasu).|  
  
 **Opcje ekstrakcji**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/widoki**|Wyodrębnia widoki bazy danych.|  
|**/funkcje**|Wyodrębnia funkcje bazy danych.|  
|**/sprocs**|Wyodrębnia procedury składowane.|  
  
 **Opcje wyjścia**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/dbml** *[:plik]*|Wysyła dane wyjściowe w postaci pliku dbml. Nie można używać z opcją **/map.**|  
|**/code** *[:plik]*|Wysyła dane wyjściowe w postaci kodu źródłowego. Nie można używać z opcją **/dbml.**|  
|**/map** *[:plik]*|Generuje plik mapowania XML zamiast atrybutów. Nie można używać z opcją **/dbml.**|  
  
 **Różne**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/język:** * \<język>*|Określa język kodu źródłowego.<br /><br /> Prawidłowy język * \<>*: vb, csharp.<br /><br /> Wartość domyślna: pochodzi z rozszerzeniem nazwy pliku kodu.|  
|**/namespace:** * \<nazwa>*|Określa przestrzeń nazw wygenerowanego kodu. Wartość domyślna: brak przestrzeni nazw.|  
|**/context:** * \<typ>*|Określa nazwę klasy kontekstu danych. Wartość domyślna: pochodzi z nazwy bazy danych.|  
|**/entitybase:** * \<typ>*|Określa klasę bazową klas obiektów w generowanym kodzie. Wartość domyślna: obiekty nie mają klasy bazowej.|  
|**/pluralizacja**|Automatycznie zmienia nazwy klas i składowych na liczbę mnogą lub pojedynczą.<br /><br /> Ta opcja jest dostępna tylko w wersji angielskiej (USA).|  
|**/serializacja:** * \<opcja>*|Generuje klasy, które można serializować.<br /><br /> Prawidłowa opcja * \<>*: Brak, Jednokierunkowy. Wartość domyślna: None.<br /><br /> Aby uzyskać więcej informacji, zobacz [Serializacja](../data/adonet/sql/linq/serialization.md).|  
  
 **Plik wejściowy**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**\<>pliku wejściowego**|Określa plik mdf programu SQL Server Express, plik SQL Server Compact 3.5 .sdf lub plik pośredni .dbml.|  
  
## <a name="remarks"></a>Uwagi  
 Działanie programu SqlMetal w rzeczywistości obejmuje wykonanie dwóch kroków:  
  
- Wyodrębnienie metadanych bazy danych do pliku dbml.  
  
- Wygenerowanie pliku wyjściowego z kodem.  
  
     Korzystając z odpowiednich opcji wiersza polecenia, można utworzyć kod źródłowy języka Visual Basic lub C# lub utworzyć plik mapowania XML.  
  
 Aby wyodrębnić metadane z pliku mdf, należy określić nazwę pliku mdf po wszystkich innych opcjach.  
  
 Jeśli **nie podano /server,** zakłada **się localhost/sqlexpress.**  
  
 Program Microsoft SQL Server 2005 zgłasza wyjątek, jeśli spełniony jest co najmniej jeden z następujących warunków:  
  
- Program SqlMetal próbuje wyodrębnić procedurę składowaną, którą sam wywołuje.  
  
- Poziom zagnieżdżenia procedury składowanej, funkcji lub widoku przekracza 32.  
  
     Program SqlMetal przechwytuje ten wyjątek i zgłasza go jako ostrzeżenie.  
  
 Aby określić nazwę pliku wejściowego, należy dodać ją do wiersza polecenia jako plik wejściowy. Uwzględnienie nazwy pliku w ciągu połączenia (przy użyciu opcji **/conn)** nie jest obsługiwane.  
  
## <a name="examples"></a>Przykłady  
 Generuje plik dbml zawierający wyodrębnione metadane SQL:  
  
 **sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**  
  
 Generuje plik dbml zawierający metadane SQL wyodrębnione z pliku mdf przy użyciu programu SQL Server Express:  
  
 **sqlmetal /dbml:mymeta.dbml mydbfile.mdf**  
  
 Generuje plik dbml zawierający metadane SQL wyodrębnione z programu SQL Server Express:  
  
 **sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**  
  
 Generuje kod źródłowy na podstawie pliku metadanych dbml:  
  
 **sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**  
  
 Generuje kod źródłowy bezpośrednio na podstawie metadanych SQL:  
  
 **sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**  
  
> [!NOTE]
> Korzystając z opcji **/pluralize** z przykładową bazą danych Northwind, należy zwrócić uwagę na następujące zachowanie. Gdy program SqlMetal tworzy nazwy tabel typu wiersz, nazwy tabel mają liczbę pojedynczą. Gdy tworzy <xref:System.Data.Linq.DataContext> właściwości dla tabel, nazwy tabel są mnogie. Przypadkowo nazwy tabel w przykładowej bazie danych Northwind mają już liczbę mnogą. Dlatego też nie widać działania tej części opcji. Popularną praktyką jest nadawanie tabelom w bazie danych nazw w liczbie pojedynczej, ale równie popularną praktyką na platformie .NET jest nadawanie kolekcjom nazw w liczbie mnogiej.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C#](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [Generowanie kodu w składniku LINQ to SQL](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Mapowanie zewnętrzne](../data/adonet/sql/linq/external-mapping.md)
